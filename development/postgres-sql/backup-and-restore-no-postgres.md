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

# 💾 Backup and restore no postgres

## Como fazer o backup PostgreSQL Comment <a href="#como-fazer-o-backup-postgresql" id="como-fazer-o-backup-postgresql"></a>

{% code overflow="wrap" %}
```sh
pg_dump --host localhost --port 5432 --username provapp --format tar --file fileName.backup --verbose NomeDoBanco
```
{% endcode %}

* **–host localhost**: define o local onde o banco se encontra, pode ser localmente ou externamente em outra rede;
* **–port 5432**: define a porta utilizada, nesse caso a padrão postgres 5432;
* **–username** postgres: define qual é o usuário utilizado na comunicação;
* **–format tar**: o tipo de compressão do arquivo gerado;
* **–file fileName.backup**: define com qual nome e caminho completo do arquivo que será gerado;
* **NomeDoBanco**: por último vai o nome do banco que se estará exportando, atenção neste ponto, pois é case sensitive, ou seja ele considera letras maiúsculas e minúsculas.
* **–verbose** Modo informações detalhadas

## Como fazer o restore PostgreSQL <a href="#como-fazer-o-restore-postgresql" id="como-fazer-o-restore-postgresql"></a>

{% code overflow="wrap" %}
```sh
pg_restore --host localhost --port 5432 --username postgres --dbname nomeDoBanco --verboser fileName.backup
```
{% endcode %}

* **–host localhost**: define o local onde o banco se encontra, pode ser localmente ou externamente em outra rede.
* **–port 5432**: é definida a porta utilizada, nesse caso a padrão postgres 5432.
* **–username postgres**: define qual é o usuário utilizado na comunicação.
* **–dbname nomeDoBanco**: o nome do banco que se estará exportando, atenção neste ponto, pois é case sensitive, ou seja ele considera letras maiúsculas e minúsculas.
* **fileName.backup**: por último, vai o caminho completo do arquivo que deseja restaurar.
* **–verbose** Modo informações detalhadas

## Fazendo backup full de todos os bancos

```sh

# entrando no diretorio do postgres e usando usuario postgres
cd /var/lib/pgsql/9.6 && su postgres

# realizando backup full
pg_dumpall -v -f filename-backup.sql

# verificando tamanho do arquivo
du -h filename-backup.sql

# gerando md5 do arquivo
md5sum filename-backup.sql

```

## Restore Usando pg\_dumpall

```sh

# copiando para maquina de destino
scp {user}@{new_host}:/var/lib/pgsql/9.6/filename-backup.sql .

# checando tamanho 
du -h filename-backup.sql

# checando hash md5 
md5sum filename-backup.sql

# restore full
psql -U postgres -f filename-database.sql
```



{% embed url="https://blog.tecnospeed.com.br/backup-e-restore-postgresql/" %}
