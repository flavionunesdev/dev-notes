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

# 😄 Configurando nova maquina ubuntu

### Instalar

* [x] Dbeaver [https://dbeaver.io/download](https://dbeaver.io/download/)
* [x] Chrome
* [x] Firefox
* [x] Docker and docker-compose
* [x] VsCode [https://code.visualstudio.com/docs/?dv=linux64\_deb](https://code.visualstudio.com/docs/?dv=linux64\_deb)
* [x] git
* [x] asdf [https://asdf-vm.com/guide/getting-started.html](https://asdf-vm.com/guide/getting-started.html)
* [x] nodejs with asdf [https://github.com/asdf-vm/asdf-nodejs](https://github.com/asdf-vm/asdf-nodejs)
* [x] golang with asdf [https://github.com/asdf-community/asdf-golang](https://github.com/asdf-community/asdf-golang)
* [x] bun with asdf [https://github.com/cometkim/asdf-bun](https://github.com/cometkim/asdf-bun)
* [x] Terminator
* [x] KeypassXC
* [x] Discord [https://discord.com/download](https://discord.com/download)
* [x] Insomnia [https://insomnia.rest/download](https://insomnia.rest/download)
* [x] VirtualBox [https://www.virtualbox.org](https://www.virtualbox.org/)
* [x] Zsh
* [x] ohmyz [https://ohmyz.sh/#install](https://ohmyz.sh/#install)
* [x] rclone [https://rclone.org/install/](https://rclone.org/install/)
* [x] ansible
* [x] indicator-sysmonitor

<pre class="language-sh" data-overflow="wrap"><code class="lang-sh"><strong>sudo su
</strong><strong># install docker and docker-compose   
</strong>wget -qO- https://get.docker.com/ | sh
service docker start
systemctl enable docker
curl -L https://github.com/docker/compose/releases/download/v2.24.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
<strong>chmod +x /usr/local/bin/docker-compose
</strong>
# install git
apt install git

# install terminator
apt install terminator

# install keypassxc+
snap install keepassxc

# install zsh
apt install zsh

# install ansible
apt install ansible

# install indicator sys-monitor
add-apt-repository ppa:fossfreedom/indicator-sysmonitor
apt update
apt install indicator-sysmonitor
</code></pre>

### Install asdf&#x20;

{% code overflow="wrap" %}
```sh
# Siga a documentação para checar a ultima versão disponível e fazer a configuração correta - https://asdf-vm.com/guide/getting-started.html
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.14.0
```
{% endcode %}

### asdf install nodejs e golang

{% code overflow="wrap" %}
```sh
asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
asdf plugin add golang https://github.com/asdf-community/asdf-golang.git
asdf plugin add bun

asdf install nodejs 20.11.0
asdf install golang 1.21.6
asdf install bun 1.0.25

asdf global nodejs 20.11.0
asdf global golang 1.21.6
asdf global bun 1.0.25
```
{% endcode %}
