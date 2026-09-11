---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Divisão (Split)'
id: P8G-AJA-YBT-F5B
slug: split
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 13:53:43'
---
# **<span align="center">Split</span>**

<br />

O handler de grid **Split** permite subdividir uma única coluna da grid em um ou mais fragmentos usando um caractere delimitador (separador) específico. Em seguida, ele pega um fragmento específico (com base em seu índice numérico) e o salva em uma coluna completamente nova na grid do seu banco de dados.

---

## **Parâmetros de Configuração**

Para configurar o handler de grid **Split**, você deve definir os seguintes parâmetros:

-   **Split Column**: A coluna original que contém a string de texto que você deseja subdividir (por exemplo, `syslog_record`).
-   **Separator**: O caractere exato ou string usada como delimitador para dividir o texto (por exemplo, `%`, `,`, `|` ou `-`).
-   **Field Idx**: O índice numérico do fragmento que você deseja extrair. **Observe que o índice começa em** `1`.
-   **New Column Name**: O nome da nova coluna onde o fragmento extraído será armazenado.

Você pode adicionar o handler de grid `Split` várias vezes se precisar extrair diversos índices diferentes da mesma coluna original para diferentes novas colunas.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/split-step1.png" align="center"></figure>

<br />

---

## **Comportamento Esperado**

Para entender melhor como o handler de grid **Split** se comporta, vamos usar uma mensagem de log fictícia com base na configuração mostrada na imagem acima.

Suponha que nossa coluna `syslog_record` contenha a seguinte estrutura de evento onde os campos são separados por um caractere `%`: `[EVENT_TYPE]%[EVENT_NAME]%[IP_ADDRESS]`.

Dada a seguinte grid:

<table><tbody><tr><th><p>syslog_record</p></th></tr><tr><td><p><code>SystemAlert%DiskFailure%10.0.0.5</code></p></td></tr><tr><td><p><code>Authentication%UserLogin%192.168.1.20</code></p></td></tr><tr><td><p><code>invalid_log_format</code></p></td></tr></tbody></table>

<br />

Se aplicarmos as duas configurações de Split mostradas na imagem:

1.  Extraindo o **Índice 1 (Index 1)** para uma nova coluna chamada `event_type` usando `%` como separador.
2.  Extraindo o **Índice 2 (Index 2)** para uma nova coluna chamada `event` usando `%` como separador.

A grid resultante será:

<table><tbody><tr><th><p>syslog_record</p></th><th><p>event_type</p></th><th><p>event</p></th></tr><tr><td><p><code>SystemAlert%DiskFailure%10.0.0.5</code></p></td><td><p><code>SystemAlert</code></p></td><td><p><code>DiskFailure</code></p></td></tr><tr><td><p><code>Authentication%UserLogin%192.168.1.20</code></p></td><td><p><code>Authentication</code></p></td><td><p><code>UserLogin</code></p></td></tr><tr><td><p><code>invalid_log_format</code></p></td><td><p><code>invalid_log_format</code></p></td><td><p><br></p></td></tr></tbody></table>

<br />

### **Explicação:**

-   Para a primeira linha (`SystemAlert%DiskFailure%10.0.0.5`), a string é dividida por `%` em três partes: `SystemAlert` (Índice 1), `DiskFailure` (Índice 2) e `10.0.0.5` (Índice 3). O handler extrai com precisão o Índice 1 para `event_type` e o Índice 2 para `event`.
-   Para a linha contendo `invalid_log_format` (que não possui o separador), a string não pode ser dividida. Portanto, a string original inteira atua como o Índice 1 (colocada em `event_type`), e como não há Índice 2, a coluna `event` permanece vazia.
-   A coluna original `syslog_record` é totalmente preservada.

<br />