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

# 🌎 Links úteis postgres

Lista de links úteis e interessantes para postgres

### Backup e restore

* [How incremental backups work in PostgreSQL, and how to implement them in 10 minutes](https://kcaps.medium.com/how-incremental-backups-work-in-postgresql-and-how-to-implement-them-in-10-minutes-d3689e8414d9)
* [Dump não é Backup](https://www.savepoint.blog.br/2010/05/06/dump-nao-e-backup/)
* [https://www.postgresqltutorial.com](https://www.postgresqltutorial.com/)
*



### Para casos onde a replica (slave) ficar indisponível por algum tempo

Arquivamento de WAL está como Continuous Archiving: [https://www.postgresql.org/docs/current/continuous-archiving.html](https://www.postgresql.org/docs/current/continuous-archiving.html)\
\
Replication Slots: \
[https://www.postgresql.org/docs/current/warm-standby.html#STREAMING-REPLICATION-SLOTS](https://www.postgresql.org/docs/current/warm-standby.html#STREAMING-REPLICATION-SLOTS)
