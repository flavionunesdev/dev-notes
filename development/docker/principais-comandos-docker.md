# 🥷 Principais comandos docker

### Remover todos os containers parados <a href="#remover-todos-os-containers-parados" id="remover-todos-os-containers-parados"></a>

{% code overflow="wrap" %}
```sh
docker rm $(docker container ps -a -q)
```
{% endcode %}

### Remove \<none> images <a href="#remove-lt-none-gt-images" id="remove-lt-none-gt-images"></a>

{% code overflow="wrap" %}
```sh
docker rmi $(docker images -f "dangling=true" -q)
```
{% endcode %}

### Obter acesso shell <a href="#obter-acesso-shell" id="obter-acesso-shell"></a>

{% code overflow="wrap" %}
```sh
# via sh
docker exec -i -t {container_name} sh

# via bash
docker exec -i -t {container_name} bash
docker exec -i -t {container_name} /bin/bash
```
{% endcode %}

### Apontando image:latest para outra versão <a href="#apontando-imagelatest-para-outra-versao" id="apontando-imagelatest-para-outra-versao"></a>

{% code overflow="wrap" %}
```sh
docker tag {image:version} image:latest
# Exemplo do comando
docker tag app-image:1 app-image:latest
```
{% endcode %}
