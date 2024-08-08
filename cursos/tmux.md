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

# ☕ Tmux

Um multiplexador com muitas opções interessantes que podem aumentar a sua produtividade

Ele tem um conceito de tecla mestre, que é na verdade uma combinação de teclas inciais que precede todos os outros comandos a serem executados. Por padrão a tecla mestre do tmux é **CTRL + B.** Pode ser alterada, mas não vejo um bom motivo para isso e prefiro utilizar o padrão mesmo.

{% hint style="info" %}
Uma coisa que acabou me confundindo na tecla mestre e que achei que deveria precionar tudo junto quando na verdade é Tecla Mestre Solta e preciona a proxima tecla
{% endhint %}

Principais teclas de atalho

<table><thead><tr><th width="201">Comando</th><th>Descrição</th></tr></thead><tbody><tr><td>[CTRL + B] e "</td><td>Divide a tela na horizontal</td></tr><tr><td>[CTRL + B] e %</td><td>Divide a tela na vertical</td></tr><tr><td>[CTRL + B] e d</td><td>Desatachar. Sai do terminal mas a sessão continua ativa</td></tr><tr><td>[CTRL + B] e $</td><td>Alterar o nome da sessão ativa</td></tr><tr><td>[CTRL + B] e c</td><td>Criar uma nova janela dentro de uma sessão</td></tr><tr><td>[CTRL + B] e p</td><td>Preview navega para janela anterior dentro de uma sessão</td></tr><tr><td>[CTRL + B] e n</td><td>Next - Navega para proxima janela dentro de uma sessão</td></tr><tr><td>[CTRL + B] e {n}</td><td>Navega para janela ao informa ao número da janela</td></tr><tr><td>[CTRL + B] e z</td><td>Da foco e remove o foco da janela atual</td></tr><tr><td>[CTRL + B] e w</td><td>Navega de modo interativo entre sessões e janelas</td></tr><tr><td>[CTRL + B] e s</td><td>Lista apenas sessões de modo interativo</td></tr><tr><td>[CTRL + B] e t</td><td>Abre um relogio no terminal</td></tr><tr><td>[CTRL + B] e ,</td><td>Renomeia a tab</td></tr></tbody></table>

***

### Comandos

Alguns comandos comuns do tmux

#### Criando sessões

```sh
# criando sessão simples e entra
tmux

# criando sessão nomeada e entra
tmux new -s {nome-da-sessao}

# criando sessão nomeada e não entra na sessão
tmux new -s {nome-da-sessao} -d
```

#### Listar sessões existentes

```sh
tmux ls
```

#### Atachar - Retornar a uma sessão ativa

```sh
tmux a -t 0
```

* **a** = Atached
* **-t** = terminal e recebe como parametro o **número** ou **nome** da sessão a ser atachada

#### Matar sessão

```sh
# matando um sessão específica
tmux kill-session -t {number-or-name-session}

# matando todas as sessões
tmux kill-server
```

### Fontes desse tutorial



{% embed url="https://www.youtube.com/watch?v=iCipX7Y3EcY" %}
