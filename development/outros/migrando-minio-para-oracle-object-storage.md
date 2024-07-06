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

# 🍥 Migrando minio para Oracle Object Storage

Utilizando ferrramenta rclone e uma maquina debian Debian GNU/Linux 11 (bullseye)

{% code overflow="wrap" %}
```sh
export PATH=$PATH:/usr/sbin/
dpkg -i rclone-v1.65.2-linux-amd64.deb

cd /home/evocorp
mkdir .oci
cd .oci
touch config
# adicione as configurações nesse arquivo
touch oci_key.pem
touch oci_key_public.pem

chmod 600 oci_key.pem

```
{% endcode %}

### Configuração do arquivo config

{% code overflow="wrap" %}
```systemd
[DEFAULT]
user=ocid1.user.oc1..aaaaaaaa7dmpzh6j6y5ukqagfyyxwsx3vl4h6swxygc47aevisl2bej45sgq
fingerprint=d9:c9:a5:3a:81:91:ca:13:51:54:37:ef:44:75:f4:70
key_file=/home/evocorp/.oci/oci_key.pem
tenancy=ocid1.tenancy.oc1..aaaaaaaap4zl2xkmqaln3hk3k32eyluvylvtgit3f2cdre4yxtxhfedhdpia
region=sa-saopaulo-1
```
{% endcode %}

### Configurando rclone

```sh
rclone config
```

* Escolha **n**
* Informe o _name_ **oci-zaut-storage**
* Selecione a opção  **37** / Oracle Cloud Infrastructure Object Storage
* Selecione a _provider_ **2** / use an OCI user and an API key for authentication.
* Informe o _namespace_ do seu object storage na oracle **gritb5i5zh4g**
* Informe o compartiment **ocid1.tenancy.oc1..aaaaaaaap4zl2xkmqaln3hk3k32eyluvylvtgit3f2cdre4yxtxhfedhdpia**
* Informe a _region_ **sa-saopaulo-1**
* Informe o _endpoint_ (opcional)
* Informe o _config\_file_ **/home/evocorp/.oci/config**
* Informe o _config\_profile_ **Deixar Default**&#x20;
* Edit advanced config **n**
* Save configuration **y**

### Migrando dados de um diretorio para o object storage

{% code overflow="wrap" %}
```sh
rclone copy /mnt/disk1/zaut oci-zaut-storage:zaut -v
```
{% endcode %}

### Migrandado dados entre object storages

{% code overflow="wrap" %}
```sh
rclone copy minio_zaut:zaut oci-zaut-storage:zaut -v
```
{% endcode %}

