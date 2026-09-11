---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Regex'
id: 2CV-MCK-FEE-ZSX
slug: regex
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 11:17:32'
---
# **<span align="center">Regex</span>**

<br />

O handler de grid **Regex** permite extrair e mapear valores de uma coluna de string usando expressões regulares, criando novas colunas no processo.

Isso é altamente útil para analisar dados de string complexos ou não estruturados, como formatos de log personalizados, mensagens Syslog ou cargas úteis de texto não formatadas, em campos de banco de dados pesquisáveis individualmente.

---

## **Parâmetros de Configuração**

O handler (conhecido internamente como `grid-regex`) possui os seguintes parâmetros de configuração:

-   **Regex Column**: O nome da coluna à qual as expressões regulares serão aplicadas.
-   **Output Fields**: Lista separada por ponto e vírgula de novas colunas a serem criadas a partir das correspondências da regex.
-   **Regex Group**: Define um identificador de expressão regular e como mapear seus grupos de captura para as colunas de saída. Você pode definir múltiplos blocos _regex-group_ para tentar várias regexes em ordem.
-   **Regular Expression**: O padrão regex a ser aplicado.
-   **Regex Field**: Mapeia um grupo de captura (por índice, começando em 1) para uma coluna de saída.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/regex-step1.png" align="center"></figure>

<br />

Ao clicar no ícone de lápis () ao lado de um Regex Group, você pode editar o mapeamento específico dos grupos de captura para os respectivos nomes de coluna de saída:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/regex-step2.png" align="center"></figure>

<br />

---

## **Comportamento Esperado**

Dada a configuração do exemplo anterior (grupo de regex `MySQL` na coluna `syslog_record`) e a seguinte grid:

<br />

<table><tbody><tr><th><p>syslog_record</p></th></tr><tr><td><p><code>&lt;30&gt;Dec 29 16:58:56 LOPOIDCBD01 mysqld_exporter[1201]: ts=2025-12-29T21...</code></p></td></tr></tbody></table>

<br />

A grid resultante será:

<table><tbody><tr><th><p>syslog_record</p></th><th><p>priority</p></th><th><p>datetime</p></th><th><p>hostname</p></th><th><p>process</p></th><th><p>pid</p></th><th><p>message</p></th></tr><tr><td><p><code>&lt;30&gt;Dec 29 16:58:56 LOPOIDCBD01 mysqld_exporter[1201]: ts=2025-12-29T21...</code></p></td><td><p><code>&lt;30&gt;</code></p></td><td><p><code>Dec 29 16:58:56</code></p></td><td><p><code>LOPOIDCBD01</code></p></td><td><p><code>mysqld_exporter</code></p></td><td><p><code>1201</code></p></td><td><p><code>ts=2025-12-29T21...</code></p></td></tr></tbody></table>

<br />

### **Explicação:**

-   O handler aplica a regex `^(\&lt;\d+\&gt;)\s(\w{3}\s+\d+\s+[\d:]+)\s+([^\s]+)\s+([^[\s:]+)(?:[(\d+)])?:\s+(.)$` a cada valor na coluna `syslog_record`.
-   Para cada correspondência, ele extrai os grupos de captura pelo seu índice (começando a partir de 1) e os atribui às colunas definidas na seção `Regex Fields` (`priority`, `datetime`, `hostname`, `process`, `pid`, `message`).
-   Se a regex não corresponder (por exemplo, `invalid_data`), as novas colunas ficarão vazias para essa linha.
-   **A coluna original é preservada;** as novas colunas são anexadas à grid sem modificar ou remover os dados de origem.

<br />