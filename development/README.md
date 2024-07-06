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

# 🤜 Dicas Nestjs

Algumas dicas úteis para nestjs

## Copiando assets para dist <a href="#copiando-assets-para-dist" id="copiando-assets-para-dist"></a>

Adicione em **compilerOptions** o nó **assets** no arquivo **nest-cli.json**

{% code title="nest-cli.json" overflow="wrap" %}
```json
{
    "collection": "@nestjs/schematics",
    "sourceRoot": "src",
    "compilerOptions": {
        "assets": [
            "i18n/**/*",
            "templates/**/*",
            "assets/**/*"
        ]
    }
}
```
{% endcode %}

