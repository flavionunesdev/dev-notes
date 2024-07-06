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

# 👩‍🚀 CACHES e REDIS



{% embed url="https://www.youtube.com/watch?v=wOi2kyMlowk" %}

## Características do REDIS

### Pontos fortes

* Muito rápido para leitura e escrita
* Muito material disponível para consulta
* Suporte para muitas linguagens de programação
* Suportado por todos os grandes clouds do mercado
* Fácil de trabalhar com cluster e escalar horizontalmente

### Pontos negativos

* Limitado a quantidade de memoria RAM disponível onde estiver instalado
* Não suporta linguagem SQL
* Não tem controle de permissões (após login com usuário e senha) é possível alterar qualquer dado no banco
* Roda em um único CPU

{% hint style="info" %}
Se você tiver uma maquina exclusiva para o redis com 10 núcleos por exemplo, o ideal é fazer um cluster de redis dentro mesma maquina, para aproveitar todos os núcleos da mesma.
{% endhint %}



## Flyweight - O Design Pattern do GOF que salva a pele na infra

{% embed url="https://www.youtube.com/watch?v=2Z17zbLZa_M&t=0s" %}



