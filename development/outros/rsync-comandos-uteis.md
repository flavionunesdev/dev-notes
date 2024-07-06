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

# 🌴 Rsync - Comandos úteis

#### Link de referência das informações Comment <a href="#link-de-referencia-das-informacoes" id="link-de-referencia-das-informacoes"></a>

[http://www.bosontreinamentos.com.br/linux/10-exemplos-do-comando-rsync-para-backup-e-sincronismo-de-arquivos-no-linux/](http://www.bosontreinamentos.com.br/linux/10-exemplos-do-comando-rsync-para-backup-e-sincronismo-de-arquivos-no-linux/)

### Instalação <a href="#instalacao" id="instalacao"></a>

**Install in CentOS**

{% code overflow="wrap" %}
```sh
yum install rsync
```
{% endcode %}

**Install in debian, ubuntu**

{% code overflow="wrap" %}
```sh
apt install rsync
```
{% endcode %}

### Exemplos de Uso <a href="#exemplos-de-uso" id="exemplos-de-uso"></a>

**Uso local**

{% code overflow="wrap" %}
```sh
rsync [opções] origem destino
```
{% endcode %}

**Modo PUSH, via shell remoto**

{% code overflow="wrap" %}
```sh
rsync [opções] origem usuário@host:destino
```
{% endcode %}

**Modo PULL, via shell remoto**

{% code overflow="wrap" %}
```sh
rsync [opções] usuário@host:origem destino
```
{% endcode %}

### Detalhes das Opções <a href="#detalhes-das-opcoes" id="detalhes-das-opcoes"></a>

#### -a <a href="#a" id="a"></a>

> Modo archive (arquivamento). Copia os arquivos e diretórios recursivamente (como -r) e preserva links simbólicos, permissões de arquivos, propriedades de usuário e grupo (ownership) e timestamps.

#### -h <a href="#h" id="h"></a>

> Números são representados em formato legível por humanos

#### -r <a href="#r" id="r"></a>

> Copia dados recursivamente, sem preservar timestamps e permissões ao transferir os dados

#### -z <a href="#z" id="z"></a>

> Comprimir os dados dos arquivos antes de enviá-los

#### –progress <a href="#progress" id="progress"></a>

> Mostrar o progresso da cópia de arquivos ao transferir os dados

#### -e <a href="#e" id="e"></a>

> Especificar o shell remoto a ser usado (rsh, ssh)

#### -c, –checksum <a href="#c-checksum" id="c-checksum"></a>

> Calcula os checksums dos arquivos para verificar se eles são iguais ao transferi-los. Utilizada para verificar a integridade dos dados copiados.

#### –exclude <a href="#exclude" id="exclude"></a>

> Permite especificar arquivos ou diretórios que não devem ser copiados para o destino

#### –include <a href="#include" id="include"></a>

> Permite especificar arquivos ou diretórios que devem ser copiados para o destino

#### –delete <a href="#delete" id="delete"></a>

> Exclui um arquivo ou diretório no destino caso ele não exista na origem

#### –max-size=TAMk|M|G <a href="#max-sizetamkmg" id="max-sizetamkmg"></a>

> Permite especificar o tamanho TAM máximo dos arquivos transferidos. Por exemplo, –max-size=50k significa que somente serão copiados arquivos com no máximo 50kB.

#### –bwlimit=LIMITE <a href="#bwlimitlimite" id="bwlimitlimite"></a>

> Permite especificar um LIMITE de largura de banda em kbps ao transferir dados de uma máquina para outra, de modo a não impactar a performance da rede.

#### -b, –backup <a href="#b-backup" id="b-backup"></a>

> Não sobrescreve arquivos que já existam no destino da transferência, mas os renomeia adicionando um sufixo \~ aos seus nomes, antes de executar a transferência de novos arquivos.

#### -u, –update <a href="#u-update" id="u-update"></a>

> Não sobrescreve nenhum arquivo no destino da transferência que possua uma data posterior (mais recente) à data do arquivo correspondente, na origem.

#### –remove-source-files <a href="#remove-source-files" id="remove-source-files"></a>

> Exclui (apaga) os arquivos no diretório de origem após o término da transferência de dados.

#### -n <a href="#n" id="n"></a>

> Modo “dry run” – executa uma tentativa de copiar dados sem realmente copiar qualquer arquivo.

#### -v <a href="#v" id="v"></a>

> Modo verboso, que mostra detalhes sobre a transferência de arquivos.

### Exemplos de uso do comando <a href="#exemplos-de-uso-do-comando" id="exemplos-de-uso-do-comando"></a>

### LOCAL to LOCAL <a href="#local-to-local" id="local-to-local"></a>

**Copiar ou sincronizar arquivos em uma máquina localmente. Vamos copiar o arquivo de nome /etc/passwd para o diretório /Backup, comprimindo dados:**

{% code overflow="wrap" %}
```sh
rsync -zvh /etc/passwd /Backup/
```
{% endcode %}

> Se o diretório de destino não existir, será criado pelo próprio rsync. A compressão de dados, na verdade, não é necessária quando copiamos arquivos dentro de um mesmo sistema de arquivos, por conta da performance da transferência dos dados.

**Copiar ou sincronizar um diretório na máquina local. Vamos copiar o diretório /home/fabio completo para o diretório /Backup/, preservando os atributos e permissões dos arquivos:**

{% code overflow="wrap" %}
```sh
rsync -avh /home/fabio /Backup/
```
{% endcode %}

> Se for acrescentada uma barra ao diretório de origem (/home/fabio/), seu conteúdo será copiado para o destino sem no entanto criar o diretório de nome fabio.

### LOCAL to REMOTE <a href="#local-to-remote" id="local-to-remote"></a>

**Copiar ou sincronizar arquivos e diretórios para ou de um servidor na rede. Vamos copiar/sincronizar um diretório da máquina local, como o meu home (/home/fabio) para um servidor na rede, que possui um diretório /home/fabio/Backup e cujo IP é 192.168.1.104. O usuário no host remoto é fabio:**

{% code overflow="wrap" %}
```sh
rsync -avz /home/fabio fabio@192.168.1.104:/home/fabio/Backup/
```
{% endcode %}

> Note que será pedida a senha do usuário no servidor remoto, no caso o fabio.

> Se você precisar efetuar o login remoto como usuário root, deve habilitar essa opção no arquivo de configuração do ssh no servidor, que é o /etc/ssh/sshd\_config. Abra esse arquivo com seu editor de textos favorito, com privilégios de administrador, e altere a seguinte linha:\
> De:\
> PermitRootLogin without-password\
> Para:\
> PermitRootLogin yes\
> Salve e saia do arquivo, e então reinicie o serviço do ssh:

{% code overflow="wrap" %}
```sh
service ssh restart
```
{% endcode %}

> Agora você poderá efetuar a cópia via rsync sobre ssh usando a conta de root.

### REMOTE to LOCAL <a href="#remote-to-local" id="remote-to-local"></a>

**Vamos fazer o contrário agora. Iremos copiar/sincronizar o diretório remoto /home/fabio/Backup no servidor 192.168.1.104 para a máquina local, no diretório /home/fabio/Documentos:**

{% code overflow="wrap" %}
```sh
rsync -avzh fabio@192.168.1.104:/home/fabio/Backup /home/fabio/Documentos/
```
{% endcode %}

**Vamos efetuar a cópia de todos os arquivos e diretórios cujos nomes comecem com a letra ‘h’ do diretório local /etc para o diretório remoto /home/fabio/Backup no servidor 192.168.1.108, excluindo (não copiando) todo os demais arquivos e diretórios de /etc/:**

{% code overflow="wrap" %}
```sh
rsync -avz --include 'h*' --exclude '*' /etc/ fabio@192.168.1.104:~/Backup
```
{% endcode %}

> –exclude ‘\*’ indica que vamos excluir da cópia todos os arquivos e diretórios, exceto os indicados pelo parâmetro –include.

**Vamos fazer o backup do diretório /home/fabio/ para o diretório /home/fabio/Backup no servidor de rede, cujo IP é 192.168.1.104. Como esse backup já foi realizado anteriormente, se algum arquivo no diretório local tiver sido excluído, ao realizar a transferência dos arquivos tal arquivo também será excluído na pasta do servidor, automaticamente (sincronismo).**

{% code overflow="wrap" %}
```sh
rsync -av --delete /home/fabio/ fabio@192.168.1.104:/home/fabio/Backup
```
{% endcode %}

**Idem anterior, porém copiando apenas os arquivos que tenham 10kB ou menos de tamanho. Não serão copiados diretórios, e vamos assumir que o diretório corrente é o diretório de origem dos arquivos.**

{% code overflow="wrap" %}
```sh
rsync -hv --max-size='10K' ./* /home/fabio/meubackup
```
{% endcode %}

**Efetuar backup do diretório /etc local no diretório /home/fabio/Backup do srvidor remoto, mostrando o progresso da cópia dos arquivos:**

{% code overflow="wrap" %}
```sh
rsync -avh --progress /etc/ fabio@192.168.1.104:/home/fabio/Backup
```
{% endcode %}

**Vamos copiar o conteúdo do diretório da rede /home/fabio/Backup para o diretório local /home/fabio/Documentos, apagando os arquivos na origem (remota) após a transferência dos dados:**

{% code overflow="wrap" %}
```sh
rsync -avh --remove-source-files fabio@192.168.1.104:/home/fabio/Backup/ /home/fabio/Documentos/
```
{% endcode %}

**Vamos copiar de volta para o servidor o conteúdo do diretório local /home/fabio/Documentos, porém sem no entanto executar a transferência dos arquivos e diretórios pra valer. Usaremos a opção de dry run (-n) para que o rsync teste essa transferência e retorne o resultado que ocorreria se ela fosse realmente executada:**

{% code overflow="wrap" %}
```sh
rsync -avhn /home/fabio/Documentos fabio@192.168.1.104:/home/fabio/Backup/
```
{% endcode %}

#### Omitindo a opção -n, a cópia dos arquivos será efetivada: <a href="#omitindo-a-opcao-n-a-copia-dos-arquivos-sera-efetivada" id="omitindo-a-opcao-n-a-copia-dos-arquivos-sera-efetivada"></a>

{% code overflow="wrap" %}
```sh
rsync -avh /home/fabio/Documentos fabio@192.168.1.104:/home/fabio/Backup/
```
{% endcode %}

**Verificando as diferenças entre origem e destino**

> Vamos executar novamente o sincronismo de arquivos e diretórios do diretório local para o remoto, como no exemplo #9, porém visualizando as diferenças existentes entre os arquivos na origem e no destino dos dados (opção -i):

```
rsync -avhi /home/fabio/Documentos fabio@192.168.1.104:/home/fabio/Backup/
```

> Na saída serão mostrados diversos caracteres em uma coluna à esquerda dos nomes de arquivos e diretórios.\
> O significado desses caracteres é o seguinte:

**<** indica que um arquivo está sendo transferido para o host remoto (enviado).

**>** indica que um arquivo está sendo transferido para o host local (recebido).

**f** indica que se trata de um arquivo.

**d** indica que se trata de um diretório

**c** indica que está ocorrendo a criação ou alteração de um item, como a criação de um diretório

**s** ocorreu alteração no tamanho.

**h** indica que se trata de um hard link para outro item

**.** indica que o item não será atualizado

**L** indica um symlink

**D** indica um dispositivo

**S** indica arquivo especial, como um socket nomeado ou um fifo.

**t** existe alteração no timestamp.

**o** proprietário alterado

**g** grupo alterado.

> Existem muitas outras opções do comando rsync. Para conferi-las, acesse as páginas de manual ou ajuda do utilitário com **man rsync** ou **rsync –help**
