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

# 🔑 Secrets

Os secrets do Docker Swarm são uma funcionalidade que permite armazenar e gerenciar dados sensíveis, como senhas, chaves de API e certificados, de forma segura dentro de um cluster Swarm. Eles são criptografados e distribuídos de forma segura para os nós do cluster, garantindo que apenas os serviços autorizados possam acessá-los.&#x20;

Os secrets são úteis para fornecer informações confidenciais aos serviços sem expô-las diretamente no código-fonte ou em variáveis de ambiente, ajudando a manter a segurança e a integridade dos dados em ambientes distribuídos. Além disso, os secrets podem ser rotacionados automaticamente, o que é essencial para manter a segurança a longo prazo.



### Listando secrets

```sh
docker secret ls
```

### Criando um novo secret

```sh
 echo -n "pass_teste" | docker secret create db_password -
```

{% hint style="info" %}
O parametro -n depois do echo é para evitar quebra de linha dentro da secret
{% endhint %}

### Criando um novo secret com base em arquivo

```sh
 docker secret create my_secret file.txt
```

### Removendo um secret

```sh
docker secret remove db_password
```

### Usando um secret em um service

{% code overflow="wrap" %}
```sh
 docker service create --name nginx -p 8080:80 --secret db_password nginx:1.5-alpine
```
{% endcode %}

{% embed url="https://www.youtube.com/watch?v=PDiNdjSa1KE" %}
