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

# ☕ SSH Managers .ssh/config

Este documento visa mostrar como voce pode fazer de forma simples para organizar o acesso ssh a multiplos servidores de maneira simples, organizada e utilizando recursos nativos do sistema operacional.

### Criando um par de chaves

{% code overflow="wrap" %}
```sh
ssh-keygen -t rsa -b 4096 -f ~/.secrets/ssh-keys/zaut-sandbox
```
{% endcode %}

### Copiando a chave para o servidor de destino

{% code overflow="wrap" %}
```sh
ssh-copy-id -i ./zaut-sandbox.pub root@192.168.200.108
```
{% endcode %}

{% hint style="danger" %}
Ao usar o comando ssh-copy-id é necessario ter a chave privada com mesmo nome da chave publica sem a extensão .pub. Isso acontece porque o ssh-copy-id tentar se conectar no servidor usando a chave privada para validar o processo de cópia.
{% endhint %}

#### Exemplo de par de chaves e sua nomeção para que o ssh-copy-id funcione conforme esperado:

* **mykey** - Chave Privada
* **mykey.pub** - Chave Pública



[https://phoenixnap.com/kb/ssh-config](https://phoenixnap.com/kb/ssh-config)\
\
