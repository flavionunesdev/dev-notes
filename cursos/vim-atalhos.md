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

# 🔮 Vim (atalhos)

Atalhos para vim

### Normal mode

* h - movimenta o cursor para esquerda
* l - movimenta o cursos para direita
* j - movimenta para baixo
* k - movimenta para cima
* w (word) - navega entre palavras para frente
* b - navega entre palavras para tras
* gg - Navega para a primeira linha
* '' - Navega para onde estava o cursor antes de ir para o inicio do arquivo
* \[Shift] + g - navega para última linha do arquivo
* dd (delete) - Deleta a linha onde estiver o cursor
* &#x20;u (undo) - Desfazer alterações (Equivalente ao CTRL + z)
* \[Ctrl] + r - refaz as alterações
* zz (zoom) Zom na linha atual centralizando na tela
* zt - Zoom Top
* zb - Zoom Bottom
* x - Remove o caractere onde está o cursor
* { - Navega entre blocos de codigo para cima
* } - Navega entre blocos de codigo para baixo
* o - adiciona uma linha abaixo e ja inicia o modo de inserção
* \[Shift] + o - adiciona uma linha acima e ja inicia o modo de inserção
* i - inicia modo de inserção (posicao anterior ao cursor)
* \[Shift] + i - Vai para o inicio da linha e inicia modo de inserção
* a (append) - inicia o modo de inserção (posicao posterior ao cursor)
* \[Shift] + a - Vai para o final da linha e inicia modo de inserção
* s - apaga o caratere atual e ja entra em modo de inserção
* \[Shift] + s - apaga a linha inteira e ja inicia o modo de inserção
* \* - faz busca com a palavra onde estiver o cursor
* yy - Copia a linha atual
* p (paste) cola o valor copiado
* cc (change) Altera a linha remove a linha e inicia em modo de inserção

#### Combinações de teclas

* dd - Deleta a linha atual
* 3dd - Deleta as tres proximas linhas
* dw - Deleta a palavra
* yw - Copia a palavra
* cw (change) - Altera a palavra
* dt)  (detele to character) - Deleta da posição atual do cursor até encontrar o caractere informando nesse exemplo o )
* di) (delete inside ")") - Deleta tudo que estiver entre parentes com base na posicao atual do cursor
* da) (delete around ")") - Deleta tud que estiver entre parentes incluindo os parenteses&#x20;

### Command mode

* :w - Salvar as alterações
* :q - Sair do editor
* :wq - Salvar e sair
* :q! - Sair forçado
* :w! - Salvar forçado
* :10 - vai para linha 10
