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

# 🐼 Postgres 14 - Replicação Master - Slave

\#database/postgresql #replicacao #master #slave

> As configurações a seguir foram testadas apenas no postgres 14.

> Para este tipo de replicação tenha exatamente a mesma versão tanto no servidor master quanto nos slaves

**Referências:**

> https://it-inzhener.com/en/articles/detail/postgresql-simple-replication-setup

> No artigo de hoje, falaremos sobre como configurar a replicação no PostgreSQL 14. Simplificando, replicação é copiar o estado de um servidor para outro por meio de logs do wal. Bem, para ser mais preciso, absolutamente todas as alterações que ocorrerem no servidor principal serão copiadas para o servidor de réplica.

### SETPS

#### Instalar o postgres 14 nos servidores master e slave

#### Configurando servidor _MASTER_

Alterer as seguintes configurações em postgresql.conf

```tsconfig
wal_level = replica
max_wal_senders = 100
```

Reinicie o banco de dados

```shell
systemctl restart postgresql
```

Crie um usuário específico para replicação

```shell
psql -U postgres
```

{% code overflow="wrap" %}
```sql
CREATE ROLE user_replicator WITH LOGIN NOSUPERUSER NOCREATEDB NOCREATEROLE NOINHERIT REPLICATION CONNECTION LIMIT -1 PASSWORD '123456';
```
{% endcode %}

Para Listar usuários criados

```sql
\du
```

Configurar o acesso para que haja acesso do servidor de réplica para o servidor de origem e vice-versa do servidor de origem para o servidor de réplica. Alterar o arquivo **pg\_hba.conf**

```shell
host replication user_replicator {ip_master}/32 scram-sha-256  
host replication user_replicator {ip_slave}/32 scram-sha-256
```

Reinicie o banco de dados

```shell
systemctl restart postgresql
```

#### Configurando o servidor _SLAVE_

Alterer as seguintes configurações em postgresql.conf

```
max_wal_senders = 100
```

> As configurações referentes a réplicas precisam ser exatamente as mesmas do servidor master

Agora é hora de migrar todo o conteúdo do servidor de origem para o servidor de réplica. Para isso, utilize o **pg\_basebackup**. Execute a transferência de dados no servidor de réplica (**slave**):

> Não remova a flag --write-recovery-conf, ela é responsável por configurar que este servidor é uma replica e configurar automaticamente a conexão em postgresql.auto.conf

{% code overflow="wrap" %}
```shell

# Pare o servidor slave
systemctl stop postgresql

# Remova todos os dados de /var/lib/postgresql/14/main/
rm -rf /var/lib/postgresql/14/main/*

# Execute o backup
pg_basebackup -h {ip_servidor_master} -U user_replicator -D /var/lib/postgresql/14/main/ --write-recovery-conf --progress --verbose

# Definas as permissões
chmod -R 0700 /var/lib/postgresql/14/main

# Defina usuario e grupo
chown -Rf postgres:postgres /var/lib/postgresql/14/main
```
{% endcode %}

Reinicie o banco de dados

```shell
systemctl restart postgresql
```

Verifique os logs:

```shell
tail -f /var/log/postgresql/postgresql-14-main.log
```

Verificar no master se o slave se conectou a ele:

{% code overflow="wrap" %}
```sql
SELECT application_name, state, sent_lsn, write_lsn, sync_state FROM pg_stat_replication;
```
{% endcode %}

Se for preciso alterar alguma configuração dos parametros de autenticação do slave, é possivel alterar as propriedades de conexão com o master com o seguinte comando:

{% code overflow="wrap" %}
```sql
ALTER SYSTEM SET primary_conninfo = 'user=replicator password=Qwerty123 host=192.168.200.170 port=5432 application_name=db_slave1';
```
{% endcode %}

As configurações acima são alteradas no arquivo **postgresql.auto.conf**

> Após aplicar as novas configurações reinicie o servidor postgres slave

> IMPORTANTE: Não remover o arquivo **standby.signal**, ele sinaliza para o postgres que aquela instancia é uma replica;
