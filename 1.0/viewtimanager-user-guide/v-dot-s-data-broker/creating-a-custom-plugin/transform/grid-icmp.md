---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grade ICMP'
id: JNC-MDX-IUI-QRJ
slug: grid-icmp
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 09:22:00'
---
# **<span align="center">Grid ICMP</span>**

<br />

O handler **Grid ICMP** permite que você realize verificações ativas de ping de rede em um endereço IP ou hostname diretamente durante a etapa de transformação do ETL.

Ao extrair o IP/hostname de destino de uma coluna especificada na grid, o handler executa uma solicitação de eco ICMP (ping) para calcular estatísticas essenciais da rede, como:

-   **Status**: Se o destino está ativo (`alive`) ou inativo (`down`).
-   **Packet Loss**: Porcentagem de pacotes perdidos.
-   **Round Trip Time (RTT)**: Tempos de resposta de latência Médio (Average), Máximo (Maximum) e Mínimo (Minimum).

Essas estatísticas são injetadas dinamicamente na grid como novas colunas e podem então ser carregadas perfeitamente no banco de dados de séries temporais para monitoramento e alertas.

---

## **Parâmetros de Configuração**

Para configurar adequadamente o handler **Grid ICMP**, defina os seguintes valores de configuração:

-   **Host Column**: A coluna existente na grid que contém o endereço IP de destino ou hostname a ser pingado.
-   **New Column Prefix**: Um prefixo de texto personalizado que será adicionado antes de todas as colunas de estatísticas recém-geradas. Por exemplo, se você definir o prefixo como `my_prefix`, o handler criará as seguintes colunas: `my_prefix_status`, `my_prefix_packet_loss`, `my_prefix_rtt_avg`, `my_prefix_rtt_max` e `my_prefix_rtt_min`.
-   **Ping Count**: O número de pacotes de solicitação de eco ICMP a serem enviados para o teste (por exemplo, `4`).
-   **Ping Timeout**: O tempo máximo (em segundos) a aguardar por uma resposta antes de considerar a solicitação como expirada (por exemplo, `2`).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-icmp-step1.png" align="center"></figure>

<br />

---

## **Comportamento Esperado**

Usando a configuração da imagem acima como exemplo:

-   O handler lê o endereço IP da coluna `host`.
-   Ele envia `4` solicitações de ping com um tempo limite de `2` segundos.
-   Os resultados são anexados à grid usando o prefixo `my_prefix`.

### **Exemplo da Grid**

<table><tbody><tr><th><p><strong>Antes da Transformação:</strong></p></th><th><p>host</p></th></tr><tr><td><p><br></p></td><td><p><code>192.168.1.1</code></p></td></tr><tr><td><p><br></p></td><td><p><code>10.0.0.99</code></p></td></tr></tbody></table>

<br />

<table><tbody><tr><th><p><strong>Após a Transformação:</strong></p></th><th><p>host</p></th><th><p>my_prefix_status</p></th><th><p>my_prefix_packet_loss</p></th><th><p>my_prefix_rtt_min</p></th><th><p>my_prefix_rtt_avg</p></th><th><p>my_prefix_rtt_max</p></th></tr><tr><td><p><br></p></td><td><p><code>192.168.1.1</code></p></td><td><p><code>alive</code></p></td><td><p><code>0</code></p></td><td><p><code>1.2</code></p></td><td><p><code>1.5</code></p></td><td><p><code>2.1</code></p></td></tr><tr><td><p><br></p></td><td><p><code>10.0.0.99</code></p></td><td><p><code>down</code></p></td><td><p><code>100</code></p></td><td><p><code>0</code></p></td><td><p><code>0</code></p></td><td><p><code>0</code></p></td></tr></tbody></table>

<br />

Este recurso poderoso elimina a necessidade de plug-ins de sondagem ativa separados, pois você pode medir continuamente métricas de disponibilidade e latência de forma dinâmica, juntamente com a sua ingestão de dados padrão.