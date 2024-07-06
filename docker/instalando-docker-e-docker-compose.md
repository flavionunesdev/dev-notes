---
cover: ../.gitbook/assets/docker.webp
coverY: 118
layout:
  cover:
    visible: true
    size: full
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

# 🐳 Instalando docker e docker-compose

Como fazer a instalação do **docker** e **docker-compose** no linux nas distros Ubuntu 23.04 e Centos 7.

### Instalar no ubuntu 20.04

{% code overflow="wrap" %}
```sh
sudo apt install docker.io
sudo systemctl enable --now docker
sudo usermod -aG docker $(whoami)
docker --version

sudo curl -L https://github.com/docker/compose/releases/download/v2.18.1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
{% endcode %}

### Instalar no Centos 7

{% code overflow="wrap" %}
```sh
wget -qO- https://get.docker.com/ | sh
systemctl start docker
systemctl enable docker
curl -L https://github.com/docker/compose/releases/download/1.27.4/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```
{% endcode %}

###
