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

# ☕ Enviar mensagem para o discord com curl

### Simples envio de mensagem de texto para um canal do discord

{% code overflow="wrap" %}
```sh
curl -i \
-H "Accept: application/json" \
-H "Content-Type:application/json" \
-X POST \
--data '{"content": "New Message"}' https://discord.com/api/webhooks/890771548078755871/7ZCJNsfQiQLHMAv0JGFYKYdvkkAtwORBuWTa8VNQO7VtDSoxGl2K_8PdL_IwSBIKT6IF
```
{% endcode %}
