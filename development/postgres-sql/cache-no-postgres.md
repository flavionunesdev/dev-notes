---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 🤠 Cache no Postgres

O PostgreSQL vem com todas as configurações setadas para funcionar em qualquer servidor. O que significa no fim das contas que serve pra tudo, mas não serve para nada… Mentira, serve para começar, porém quando seu banco começar a crescer, você vai notar que vai precisar de mais peformance em alguns lugares específicos e vai precisar mexer em algumas configurações.

Antes de partir para as configurações é importante saber que a memória pode ser classificada em duas categorias: Local Memory e Shared Memory (no final eu deixo um vídeo sobre arquitetura de memória do PostgreSQL, é muito bom para entender a parte mais física desse rolê).

## Local Memory <a href="#id-6822" id="id-6822"></a>

A local memory é carregada por cada processo do backend para o uso no processamento de consultas.

### Work mem <a href="#id-2ff6" id="id-2ff6"></a>

Esse valor é basicamente setado para algoritmos de ordenação complexos, o valor define a quantidade máxima de memória para ser usada em resultados intermediários, hash tables e sorting.

Quando o valor setado é alto, as queries de sort ficam bem peformáticas, porém se ele for setado muito alto, ele pode engargalar a memória disponível, porque ele irá utilizar esse valor alto para todas as operações de sort que forem requisitadas concorrentemente.

Por isso, caso seja necessário em alguma consulta específica, é possível setar ele para aquela query.

O valor default é: 4MB, então dependendo da quantidade de memória disponível é interessante aumentar esse valor, mas sempre observando a quantidade de sort (order by e distinct) que será requisitada do banco.

Para setar para uma única query:

```
SET LOCAL work_mem = '1GB'
SELECT * FROM db ORDER BY id;
```

### Maintenance work mem <a href="#e731" id="e731"></a>

Utilizado para especificar a quantidade de memória que será utilizada para rotinas de manutenção: VACUUM(se não houver autovacuum\_work\_mem configurado), CREATE INDEX e ALTER TABLE ADD FOREIGN KEY.

Essas operações não são concorrentes por sessão, o que significa que um valor mais alto pode ser setado para elas. Valores altos podem melhorar o desempenho de vacuum e para restauração de dumps.

Se for setado um valor alto para autovacuum\_max\_workers, o banco poderá ter um problema de memória disponível, pois o valor de maintenance\_work\_mem poderá ser multiplado por autovacuum\_max\_workers. Por isso é interessante definir o autovacuum\_work\_mem.

O valor default é: 64 MB. Mas seguramente esse valor será muito baixo quando você tiver tabelas muito grandes, ou quando voce criar um index para uma tabela grande também.

Para setar em uma única operação:

```plsql
SET maintenance_work_mem TO '32 MB';
CREATE INDEX idx_id ON db (id);
```

### Temp Buffers <a href="#id-7b18" id="id-7b18"></a>

Esse buffer é utilizado apenas para tabelas temporárias. O valor padrão é 8MB.

Para setar em uma única operação:

```plsql
SET temp_buffers = '1GB';
CREATE TEMP TABLE tmp_tbl AS SELECT * FROM tbl LIMIT 0;
```

## Shared Memory <a href="#id-8b3c" id="id-8b3c"></a>

É alocado pelo servidor do PostgreSQL quando ele inicializa e é usado por todos os processos.

### Shared buffer pool <a href="#id-076a" id="id-076a"></a>

Onde o Postgres carrega páginas com tabelas e indexes do disco, para trabalhar com ele diretamente da memória.

O valor default é baixo, então é uma das principais mudanças que causarão impacto na peformance do seu banco, não existe uma bom valor global, mas não é difícil calcular um bom valor para o seu sistema.

Geralmente um valor interessante é por volta de 25% da RAM total do sistema, no caso de um servidor dedicado. O valor total da RAM nunca deve ser totalmente reservado para shared buffer, pois o próprio Linux reserva uma parte da memória para buffer, onde ele armazena as páginas que também poderão ser usadas em uma consulta (caso a query não encontre no shared buffer, porém tudo que está no shared buffer está nesse cache, só o contrário que não é verdadeiro).

Um percentual mais alto do que 25% pode ser útil, pois quanto mais dados armazenados na memória, menos é necessário ir em disco. Enquanto um valor alto de shared buffer pode ajudar na leitura, ele pode prejudicar na escrita, pois todo o conteúdo que está em memória é processado durante uma gravação.

Valor default: 32MB

### WAL Buffer <a href="#id-1eb6" id="id-1eb6"></a>

Write-Ahead Logging (WAL) garante a integridade dos dados, o PostgreSQL grava registros no WAL e só depois ele transfere esses registros para o disco.

É interessante mudar esse valor se a quantidade de conexões concorrentes for alta, isso poderá aumentar o desempenho.

Valor default: não é definido um valor default pelo PostgreSQL, o que significa que ele utilizará espaço do shared buffer, até que seja definido um valor.

### Effective Cache Size <a href="#id-19cd" id="id-19cd"></a>

Basicamente ele fornece uma estimativa de quanto é a memória disponível para armazenamento em cache. Esse valor é utilizado pelo query planner para descobrir se os planos caberiam ou não na RAM.

Um valor muito utilizado é metade do tamanho da RAM ou 75% em casos de servidores dedicados.

Um valor muito baixo pode fazer com que o planejador resolva não utilizar alguns indíces, ainda que seja mais rápido.

Valor default: 4GB.

Bom, essas são algumas configurações que devem ser pensadas quando começamos a tunar nosso PostgreSQL. Porém não há configuração que salve uma query ruim. Lembrando que serviços de banco de dados costumam ter boas configurações.\


{% embed url="https://medium.com/@jujulisan/otimize-seu-postgresql-come%C3%A7ando-pelo-come%C3%A7o-c4815b627594" %}

{% embed url="https://www.infoq.com/br/articles/postgres-handles-more-than-you-think/" %}

{% embed url="https://www.youtube.com/watch?v=_PQwWUSq1R8" %}
