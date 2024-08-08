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

# 👨‍🔧 Logs e Grafana Loki - Alura



**Logs oferecem:**

* Data e hora do evento
* Registro imutável
* Rastreabilidade
* Nível de severidade

**Logs devem possuir:**

* Código de evento
* Mensagem personalizada
* Condição tratada
* Período de retenção

### Análise de causa raiz (RCA)

É análise de causa raiz um processo de identificação da raiz do problema que afeta um ou mais sistemas que compoem um produto.

Documentação pos incidente chamada de POS Mortem

### Tempo médio de reparo (MTTR)

Tempo médio de reparo é um identificador que aponta o tempo médio dedicado ao reparo de um sistema em estado de falha.

### Pilares da observabilidade

* **Logs** - Eventos de logs registrados
* **Métricas** - Analise dos aspectos imporantes do aplicação em uma serie temporal, que é transformado em indicador dentro de uma janela de tempo
* **Rastreamento** - O acompanhamento do seu fluxo transacional end to end

{% hint style="info" %}
Sobre métricas pesquisar sobre golden signals ou Sinais de
{% endhint %}

### Níveis de Log

* Trace - Depuração profunda
* Debug - Menos verboso que o trace
* Info - Informações normais da execução da aplicação
* Warn - É um aviso, quando comportamentos inesperados aconteceu, mas não necessariamente um erro
* Error - Aconteceu um erro de fato na aplicação
* Fatal - A aplicação parou de funcionar (Pode ser reservado, depende da linguagem ou framework)



**Qual deve ser a severidade logada para um conflito mapeado em uma regra de negócio através de uma requisição com dados incorretos?**

Segundo o curso um **warn**\


Durante o curso recomenda-se gerar logs de conflitos como, validações de dados, ou regras de negocio tratadas como log level warn.

Exemplos de log level warn:

* CPF incorreto
* Nome muito grande
* Este email já está sendo utilizado

{% hint style="danger" %}
Não é uma boa prática retornar para o cliente erro 500. (Buscar mais informações sobre o assunto) Ele trocou para um erro **502 - Bad Gateway**
{% endhint %}

### Grafana loki

Composto por uma serie de components que compoem uma stack de logs completa

Loki indexa apenas metadados sobre os logs, como labels. os dados de log em si são compactados e armazenados como objetos, formando ńdices pequenos e blocos altamente compactados



