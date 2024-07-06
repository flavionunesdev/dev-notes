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

# 🐯 Github Auth com ssh

Este tutorial mostra como fazer autenticação da sua conta com github usando um par de chaves ssh

### Passo 1 - Crie um par de chaves

```sh
ssh-keygen -t rsa -b 4096 -f ~/.secrets/ssh-keys/github
```

* **-t** o tipo da chave
* **-b** o tamanho da chave
* **-f** o path do arquivo (pode criar o arquivo com nome que quizer, mas escolha algo que faça sentido)

### Passo 2 - Copiar a chave publica para o github

O comando acima deve criar dois arquivos contendo as chaves publicas e privadas respectivamente. (github - Chave privada e github.pub contendo a chave pública)

Nesta etapa é necessario adicionar a chave pública ao github, para isso acesse as seguintes opções:

* Clique no icone do seu usuário no github
* Clique em settings
* Clique em SSH and GPG Keys
* Clique em new SSH key
* Informe o titulo da chave e a sua key publica

O titulo da chave serve para lembrar o próposito ou mesmo a origem daquela chave.

Para obter o conteudo da chave publica você pode usar o seguinte comando

```sh
cat github.pub
```

### Passo 3 - Configurar a chave privada&#x20;

Este passo pode ser desnecessario caso



### Passo 4 - Testar

Clone um projeto privado para testar

Obs...

