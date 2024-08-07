---
description: Resolvendo problemas com videos no opera browser (Linux)
cover: ../.gitbook/assets/opera-new-logo.jpg
coverY: 11
---

# 🎬 Opera browser (Linux), problemas com vídeos

Aparentemente existe um problema na libffmpeg.so, que acompanha o opera nas instalações linux, fazendo com que videos mp4 não possam ser abertos pelo browser.

Existem algumas formas de contornar esse problema, entre elas podemos trocar o arquivo **libffmpeg.so** que vem junto com a instalação padrão do opera pelo libffmpeg.so do chromium.

### Resolvendo o problema

{% hint style="info" %}
É possível que os caminhos descritos abaixo sejam diferentes dependendo da sua disto linux. As operações abaixo foram feitas no **Ubuntu 20.04.2 LTS.**
{% endhint %}

Antes de iniciar feche o **browser opera**

Navegue para:

<pre class="language-sh"><code class="lang-sh"><strong>cd /usr/lib/x86_64-linux-gnu/opera
</strong></code></pre>

Faça uma copia de segurança do arquivo **libffmpeg.so** original, caso seja necessário recupera-la.

```sh
cp libffmpeg.so libffmpeg.so.backup
```

Caso não tenha o chromium instalado, podemos instalar apenas os codecs do mesmo com o comando:

```sh
sudo apt install -y chromium-codecs-ffmpeg
```

Se a instalação for concluída com sucesso substitua os arquivo libffmpeg.so do opera assim:

{% code overflow="wrap" %}
```sh
sudo cp /snap/chromium-ffmpeg/current/chromium-ffmpeg-103551/chromium-ffmpeg/libffmpeg.so /usr/lib/x86_64-linux-gnu/opera/
```
{% endcode %}

Abra o opera e verifique se consegue abrir videos MP4.
