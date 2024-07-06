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

# 🤜 SSL local mkcert

Instalando e configurando SSL local mkcert

### Instalando mkcert <a href="#instalando-mkcert" id="instalando-mkcert"></a>

{% code overflow="wrap" %}
```sh
sudo apt install libnss3-tools curl -y
sudo curl -L https://github.com/FiloSottile/mkcert/releases/download/v1.4.3/mkcert-v1.4.3-linux-amd64 -o /usr/local/bin/mkcert
sudo chmod +x /usr/local/bin/mkcert
sudo chown evocorp:evocorp /usr/local/bin/mkcert
mkcert -install
```
{% endcode %}

### Gerando os certificados <a href="#gerando-os-certificados" id="gerando-os-certificados"></a>

{% code overflow="wrap" %}
```sh
mkcert corechat.test
```
{% endcode %}

### Gerando os certificados wildcard <a href="#gerando-os-certificados-wildcard" id="gerando-os-certificados-wildcard"></a>

{% code overflow="wrap" %}
```sh
mkcert "*.corechat.test"
```
{% endcode %}

### Para copiar a certificadora para outras maquinas <a href="#para-copiar-a-certificadora-para-outras-maquinas" id="para-copiar-a-certificadora-para-outras-maquinas"></a>

{% code overflow="wrap" %}
```sh
# para mostrar o caminho dos arquivos 
mkcert -CAROOT 

# copiando arquivos para maquina de destino
scp rootCA-key.pem rootCA.pem evocorp@192.168.200.192:/home/evocorp/.local/share/mkcert

# Rodar comando na maquina de destino
mkcert -install
```
{% endcode %}

{% hint style="info" %}
APÓS REALIZAR OPERAÇÃO REINICIE A MAQUINA
{% endhint %}
