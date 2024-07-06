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

# 🍪 Git

### Mostrando logs

{% code overflow="wrap" %}
```sh
git log
```
{% endcode %}

### Corrigir mensagem do ultimo commit

[https://youtu.be/6OokP-NE49k?si=Ucqk0UpILl72Bg5u\&t=187](https://youtu.be/6OokP-NE49k?si=Ucqk0UpILl72Bg5u\&t=187)

{% code overflow="wrap" %}
```sh
git commit -m "Mensagemd de commit correta" --amend
```
{% endcode %}

### Mesclando commits antes de fazer o pull

[https://youtu.be/6OokP-NE49k?si=qGTV7csc6QrkDZfh\&t=230](https://youtu.be/6OokP-NE49k?si=qGTV7csc6QrkDZfh\&t=230)

Existe mais de uma forma de fazer isso

#### Usando rest soft

HEAD Para remover os commits a partir da cabeca e \~2 para remover os dois ultimos commits.

Este comando deve desfazer apenas os commits, mas não irá remover as alterações no arquivos, permitindo que voce possa dar um git commit

{% code overflow="wrap" %}
```sh
git reset --soft HEAD~2
```
{% endcode %}

#### Usando o modo interativo e rebase

[https://youtu.be/6OokP-NE49k?si=rq28edXqmHmNRe8I\&t=373](https://youtu.be/6OokP-NE49k?si=rq28edXqmHmNRe8I\&t=373)

{% code overflow="wrap" %}
```sh
git rebase -i HEAD~3
```
{% endcode %}

### Removendo um arquivo do staged

```sh
git reset -- fileName.txt
```

### Removendo todos os arquivos do staged

{% code overflow="wrap" %}
```sh
git reset --
```
{% endcode %}

### Removendo um arquivo do staged usando a opção interativa

```sh
git add -i
```

* Vai abrir um terminal interativo com algumas opções, escolha a opção **3 - revert**
* Vai listar todos os arquivos que estão no staged e você pode ir digitando apenas o número dos arquivos que não deseja comitar no momento&#x20;
* Ao concluir pressiona **ENTER** para voltar ao menu anterior
* Caso tenha escolhido um arquivo errado e precise adicionar o arquivo no staged escolha a opção **2 - Update** e novamente escolha o número do arquivo que deseja adicionar
* Quando concluir escolhe **quit** para sair

### Apagando modificações com git reset

{% hint style="danger" %}
Cuidado ao utilizar --hard você ira remover tanto os commits quanto as modificações nos arquivos
{% endhint %}

```
git reset --hard HEAD~1
```

### Documentei até

[https://youtu.be/6OokP-NE49k?si=HHoIOciCNKRKr4WF\&t=1012](https://youtu.be/6OokP-NE49k?si=HHoIOciCNKRKr4WF\&t=1012)

### Videos Fabio Akita

{% embed url="https://www.youtube.com/watch?v=6Czd1Yetaac" %}

{% embed url="https://www.youtube.com/watch?v=6OokP-NE49k&t=1s" %}
