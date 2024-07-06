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

# 🗃️ Arquivos YML

{% embed url="https://www.youtube.com/watch?v=JOtIVGy1SgE" %}

## Caracteristicas

* Utilizado para configurações baseado em identação
* Pode ser utilizado com as extensões .yml ou .yaml
* Assim como JSON tambem é baseado em chave e valor
* Diferente do JSON ele utiliza identação

## Exemplos

### Exemplo Chave: Valor

```yaml
# Chave e valor simples
fruta: banana

# Chave e valor com aspas
frutas: "banana abacete"

# Informando numero inteiro
total_frutas: 5

# A chave pode ter espaço
gosta de fruta: true
```

### Exemplo de objeto

```yaml
fruta:
  nome: banana
  cor: amarela
  qtde: 5
```

### Exemplo de array

```yaml
frutas:
  - nome: banana
    cor: amarela
    qtde: 5
  - nome: morango
    cor: vermelho
    qtde: 10
  - nome: limao
    cor: verde
    qtde: 20
```

### Exemplo de arquivo de configuração

```yaml
apiVersion: v1

```
