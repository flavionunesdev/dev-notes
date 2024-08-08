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

# 👨‍💻 Curso GO

## Iniciando novo projeto em go

{% code overflow="wrap" %}
```sh
go mod init {package_name}
```
{% endcode %}

o **package name** geralmente segue uma nomenclatura de  onde está o nome do projeto, algo parecido com o que acontece com o nome de pacotes em java.

Alguns exemplos de nome de pacotes utilizados pela comunidade

```sh
# usando github
go mod init github.com/evocorp/myapp

# usando nome de dominio próprio
go mod init evocorp.dev/myapp
```

Após gerar um novo modulo com **go mod init** ele vai criar os arquivos

* go.mod - Equivalente a um package.json do nodejs
* go.sum - Equivalente ao package.lock do nodejs

## Baixando pacotes em go

Para baixar pacotes usamos o comando **go get**

**Exemplo baixando o pacote uuid**

```
go get github.com/google/uuid
```

## Instalando ou removendo pacotes de forma automática

```sh
go mod tidy
```

O código acima instala todos os pacotes que estiverem faltando e tambem remove todos os que não estão sendo utilizados pela sua aplicação.

## Compilando aplicação go

```sh
go build

# Compilando para windows
GOOS=windows go build

# Compilando para windows na arquietura arm
GOOS=windows GOARCH=arm go build

# Especificando o nome do binário
go build -o nome-app
```

Go build vai funcionar se exister um modulo go criado e o arquivo go.mod, caso contrário para compilar voce deve especificar o arquivo algo como:

{% code overflow="wrap" %}
```sh
go build main.go
```
{% endcode %}

## Listando as versões e arquieturas disponíveis para compilar sua app go

{% code overflow="wrap" %}
```sh
go tool dist list
```
{% endcode %}

## Mostrar variáveis de ambiente do go

```sh
# Mostrando todas as variáves
go env

# Mostrando variáveis especificas
go env GOOS GOARCH
```

## Pacotes

Quando criamos pacotes no go, por convenção sempre nomeamos o nome do pacote como mesmo nome da pasta onde ele se encontra. Exemplos:

```
-- myApp
---- config/
------ config.go
```

No caso do arquivo config.go o package é config pois o mesmo está dentro da pasta config. Temos uma execção para esta convenção para o pacote main.





&#x20;
