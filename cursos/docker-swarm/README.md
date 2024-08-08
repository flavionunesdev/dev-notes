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

# 👩‍🚀 Docker Swarm

### Manager vs Worker

No swarm tem dois tipos de nós manager ou worker.

* worker - Sua função principal é apenas ter containers em execução
* manager - Gerencia todos os detalhes do cluster, nesse tipo de node fica toda a administração do cluster, alem tambem de poder ter containers rodando nele. toda informação sensivel do cluster está no manager

A resiliencia de cluster swarm está na quantidade de nodes manager que o mesmo possue. Para que o cluster continue funcionando ele precisa ter 50% +1 dos nós managers em execução. Dessa maneira só faz sentido manter um número impar de nós manager.

#### Exemplo de calculo

* 1 node manager - Nenhum node pode cair
* 2 node manager - Nenhum node pode cair
* 3 node manager - 1 Node pode cair
* 4 node manager - 1 Node pode cair
* 5 node manager - 2 node pode cair
* 6 node manager - 2 node pode cair

### Comandos do swarm

#### Iniciando um novo cluster

```sh
docker swarm init
# Iniciando e definindo a rede do cluster
docker swarm init --advertise-addr {ip interface}
```

#### Obtendo token para conectar novos nodes ao cluster

```sh
docker swarm join-token worker
# or
docker swarm join-token manager
```

#### Alterando a token para conexao de novos nodes no cluster

```sh
docker swarm join-token --rotate worker
# or
docker swarm join-token --rotate manager
```

{% hint style="info" %}
A geração de novos tokens acima não interfere no cluster em execução, apenas gera novos tokens para ser usado nos próximos nodes a serem adicionados ao cluster
{% endhint %}

#### Listando nodes swarm

```sh
docker node ls
```

#### Promovendo um node worker para manager

```sh
docker node promote {node-name}
```

#### Alterando node manager para worker

```sh
docker node demote {node-name}
```

#### Removendo a maquina do cluster (Dentro do node que será removido)

```sh
docker swarm leave
# Caso o node seja um manager
docker swarm leave -f
```

#### Mostrando os serviços rodando dentro do cluster

```sh
docker service ls
```



### Fontes

{% embed url="https://www.youtube.com/watch?v=ojQUXXea2Bk" %}

{% embed url="https://www.youtube.com/watch?v=aGif8R0BWHg" %}
