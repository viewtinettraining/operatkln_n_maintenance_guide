---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Kpireference
id: 1NO-SZ5-WYW-QJL
isVisible: true
isSearchable: true
slug: kpireference
lastUpdated: '2026-09-10 19:52:48'
---
﻿---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: KPI_Reference
id: KWS-CP2E-E29-FCN
slug: kpireference
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 18:25:41'
---
# **<span align="center">Guia de Referência de KPIs do Network Traffic Analyzer</span>**

<br />

<span align="justify">Este documento fornece uma descrição abrangente de todos os Indicadores Chave de Desempenho (KPIs) extraídos pelo analisador de sondas a partir do tráfego Ethernet em tempo real. O sistema inspeciona pacotes em todas as camadas da pilha de protocolos, desde o enquadramento Ethernet até os protocolos da camada de aplicação, e calcula um rico conjunto de métricas para monitoramento de rede, garantia de qualidade e solução de problemas.</span>

<span align="justify">Os KPIs são organizados por seção de protocolo. Cada seção lista cada métrica extraída para aquele protocolo, o nome do campo relatado, o tipo de dados, a unidade e uma descrição do que ela mede e como é calculada.</span>

---

## Índice

1.  [KPIs Comuns / Camada IP](#1-common--ip-layer-kpis)
2.  [TCP](#2-tcp)
3.  [UDP](#3-udp)
4.  [HTTP](#4-http)
5.  [TLS / HTTPS](#5-tls--https)
6.  [DNS](#6-dns)
7.  [SIP (Sinalização VoIP)](#7-sip-voip-signaling)
8.  [RTP / RTCP (Mídia VoIP)](#8-rtp--rtcp-voip-media)
9.  [ICMP](#9-icmp)
10.  [ICMPv6](#10-icmpv6)
11.  [DHCP](#11-dhcp)
12.  [DHCPv6](#12-dhcpv6)
13.  [TWAMP](#13-twamp)
14.  [FTP](#14-ftp)
15.  [GRE](#15-gre)
16.  [Camada de Aplicação (DPI)](#16-application-layer-dpi)
17.  [Outros Protocolos L4](#17-other-l4-protocols)

---

## **1\. KPIs Comuns / Camada IP**

Esses KPIs são extraídos nas camadas de inspeção Ethernet, VLAN, IPv4 e IPv6. Eles fornecem a identificação fundamental da rede e métricas de volume de tráfego que são anexadas a cada fluxo relatado, independentemente do protocolo da camada superior.

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>timestamp</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora do último pacote observado no fluxo (microssegundos desde a epoch).</p></td></tr><tr><td><p><code>first_timestamp</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora do primeiro pacote observado no fluxo.</p></td></tr><tr><td><p><code>vlan_id</code></p></td><td><p>uint32</p></td><td><p>—</p></td><td><p>Identificador de tag VLAN IEEE 802.1Q extraído do quadro Ethernet. Suporta tags VLAN empilhadas (QinQ); o ID da VLAN mais interna é relatado.</p></td></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IP de origem (lado do cliente / uplink) na notação decimal com pontos (IPv4) ou hexadecimal com dois pontos (IPv6). A direção é determinada pela configuração do pool de servidores, análise de flag SYN ou heurísticas de número de porta.</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IP de destino (lado do servidor / downlink).</p></td></tr><tr><td><p><code>net_src_ipv6</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Campo explícito de endereço de origem IPv6, relatado quando o fluxo é IPv6.</p></td></tr><tr><td><p><code>net_dst_ipv6</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Campo explícito de endereço de destino IPv6.</p></td></tr><tr><td><p><code>net_ipv6_over_ipv4</code></p></td><td><p>bool</p></td><td><p>—</p></td><td><p>Flag indicando que o fluxo é um pacote IPv6 encapsulado dentro de um túnel IPv4 (protocolo 41).</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta de origem de camada 4 (lado do cliente / uplink).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta de destino de camada 4 (lado do servidor / downlink).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Nome do protocolo legível por humanos (ex: "TCP", "UDP", "ICMP", "ICMPV6").</p></td></tr><tr><td><p><code>volume_uplink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Volume total de carga útil transferido na direção de uplink (cliente → servidor).</p></td></tr><tr><td><p><code>volume_downlink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Volume total de carga útil transferido na direção de downlink (servidor → cliente).</p></td></tr><tr><td><p><code>peak_volume_uplink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Pico de volume de uplink observado em uma única janela de relatório.</p></td></tr><tr><td><p><code>peak_volume_downlink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Pico de volume de downlink observado em uma única janela de relatório.</p></td></tr><tr><td><p><code>net_src_packets</code></p></td><td><p>uint64</p></td><td><p>pacotes</p></td><td><p>Número total de pacotes enviados pela origem (uplink).</p></td></tr><tr><td><p><code>net_dst_packets</code></p></td><td><p>uint64</p></td><td><p>pacotes</p></td><td><p>Número total de pacotes enviados pelo destino (downlink).</p></td></tr><tr><td><p><code>initial_direction</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Direção do primeiro pacote no fluxo: <code>"0"</code> = uplink, <code>"1"</code> = downlink.</p></td></tr></tbody></table>

### Determinação de Direção

A direção do fluxo (uplink vs. downlink) é estabelecida usando uma abordagem baseada em prioridade:

1.  **Pool de Servidores**: Se um pool de servidores configurado contiver um dos endpoints, a direção será definida de acordo.
2.  **Flag SYN TCP**: Para fluxos TCP, o iniciador SYN é classificado como o cliente (uplink).
3.  **Heurística de Porta**: Supõe-se que o endpoint com o número de porta mais alto seja o cliente.
4.  **Comparação de IP**: Como último recurso, o endereço IP mais baixo é atribuído como o lado de uplink.

---

## **2\. TCP**

O inspetor TCP cria um fluxo para cada 5-tupla única (IP de origem, IP de destino, porta de origem, porta de destino, protocolo) e rastreia o ciclo de vida completo da conexão TCP por meio de uma máquina de estado. Ele extrai métricas detalhadas de desempenho tanto para o lado do cliente quanto para o lado do servidor.

### 2.1 KPIs do Ciclo de Vida da Conexão

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>flow_state</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Estado atual da máquina de estado TCP (ex: <code>"syn-sent"</code>, <code>"established"</code>, <code>"fin-wait"</code>, <code>"closed"</code>).</p></td></tr><tr><td><p><code>tcp_connection_id</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Identificador hash único para esta conexão TCP (xxHash da 5-tupla).</p></td></tr><tr><td><p><code>tcp_connection_requests</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de tentativas de iniciação de conexão TCP (pacotes SYN enviados).</p></td></tr><tr><td><p><code>tcp_connections_opened</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de conexões estabelecidas com sucesso (handshake SYN-ACK concluído).</p></td></tr><tr><td><p><code>tcp_connections_failed</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de tentativas de conexão que falharam (ex: RST recebido, tempo limite durante o handshake).</p></td></tr><tr><td><p><code>tcp_connections_active</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de conexões atualmente no estado estabelecido (transferência de dados ativa).</p></td></tr><tr><td><p><code>tcp_connections_closed</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de conexões que foram encerradas graciosamente (handshake FIN concluído).</p></td></tr></tbody></table>

<br />

### **2.2 KPIs de Tempo**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>connection_time</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Tempo de Conexão TCP</strong> — Tempo decorrido desde o SYN inicial até a conclusão do handshake de três vias (SYN → SYN-ACK → ACK). Mede quanto tempo leva para estabelecer a conexão TCP.</p></td></tr><tr><td><p><code>tcp_time_to_first_byte</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Tempo até o Primeiro Byte (TTFB)</strong> — Tempo desde a conclusão do handshake TCP até o primeiro pacote de dados recebido do servidor. Indica a capacidade de resposta de processamento do servidor.</p></td></tr><tr><td><p><code>session_duration</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Duração da Sessão</strong> — Tempo total do primeiro pacote ao último pacote na sessão TCP. Reflete a vida útil geral da conexão.</p></td></tr></tbody></table>

<br />

### **2.3 KPIs de Tempo de Ida e Volta (RTT) e Jitter**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>tcp_rtt_client</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>RTT do Cliente</strong> — Soma acumulada das medições do tempo de ida e volta do lado do cliente. Calculado medindo o tempo entre um segmento de dados enviado pelo cliente e o ACK correspondente do servidor.</p></td></tr><tr><td><p><code>tcp_rtt_client_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras RTT do cliente coletadas. RTT Médio = <code>tcp_rtt_client / tcp_rtt_client_samples</code>.</p></td></tr><tr><td><p><code>tcp_rtt_server</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>RTT do Servidor</strong> — Soma acumulada das medições do tempo de ida e volta do lado do servidor. Medido desde os segmentos de dados do servidor até seus ACKs correspondentes.</p></td></tr><tr><td><p><code>tcp_rtt_server_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras RTT do servidor coletadas.</p></td></tr><tr><td><p><code>tcp_jitter_client</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Jitter do Cliente</strong> — Soma das diferenças absolutas entre as medições consecutivas de RTT no lado do cliente. Mede a variabilidade do RTT / estabilidade da rede da perspectiva do cliente.</p></td></tr><tr><td><p><code>tcp_jitter_client_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras de jitter do cliente. Jitter Médio = <code>tcp_jitter_client / tcp_jitter_client_samples</code>.</p></td></tr><tr><td><p><code>tcp_jitter_server</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Jitter do Servidor</strong> — Soma das diferenças absolutas de RTT no lado do servidor.</p></td></tr><tr><td><p><code>tcp_jitter_server_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras de jitter do servidor.</p></td></tr></tbody></table>

<br />

### **2.4 KPIs de Tempo de Transferência de Dados (DTT)**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>tcp_dtt_client</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Tempo de Transferência de Dados do Cliente</strong> — Tempo total observado para as operações de transferência de dados iniciadas pelo cliente. Captura a latência da entrega de dados do lado do cliente medida através de grupos de pacotes de dados consecutivos.</p></td></tr><tr><td><p><code>tcp_dtt_client_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras DTT do cliente.</p></td></tr><tr><td><p><code>tcp_dtt_server</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Tempo de Transferência de Dados do Servidor</strong> — Tempo total observado para as operações de transferência de dados do lado do servidor. Captura a latência da entrega de dados do servidor através de grupos de pacotes de resposta consecutivos.</p></td></tr><tr><td><p><code>tcp_dtt_server_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras DTT do servidor.</p></td></tr></tbody></table>

<br />

### **2.5 Tempo de Resposta do Servidor (SRT)**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>tcp_srt_server</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Tempo de Resposta do Servidor</strong> — Tempo entre o último pacote de dados do cliente (solicitação) e o primeiro pacote de dados do servidor (resposta). Mede a rapidez com que o servidor começa a responder às solicitações do cliente.</p></td></tr><tr><td><p><code>tcp_srt_server_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras SRT.</p></td></tr></tbody></table>

<br />

### **2.6 KPIs de Retransmissão**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>tcp_retransmissions_client</code></p></td><td><p>uint64</p></td><td><p>contagem (soma)</p></td><td><p><strong>Retransmissões do Cliente</strong> — Número de segmentos TCP retransmitidos detectados no lado do cliente. Detectado ao rastrear números de sequência: se um segmento for enviado com um número de sequência inferior à próxima sequência esperada, ele será sinalizado como uma retransmissão.</p></td></tr><tr><td><p><code>tcp_retransmissions_client_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de períodos de relatório com medições de retransmissão do cliente.</p></td></tr><tr><td><p><code>tcp_retransmissions_server</code></p></td><td><p>uint64</p></td><td><p>contagem (soma)</p></td><td><p><strong>Retransmissões do Servidor</strong> — Número de segmentos retransmitidos no lado do servidor.</p></td></tr><tr><td><p><code>tcp_retransmissions_server_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de períodos de relatório para retransmissões do servidor.</p></td></tr><tr><td><p><code>tcp_retransmission_delay_client</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Atraso de Retransmissão do Cliente</strong> — Atraso acumulado causado por retransmissões no lado do cliente. Mede o tempo entre a transmissão original e a retransmissão do mesmo segmento.</p></td></tr><tr><td><p><code>tcp_retransmission_delay_client_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras de atraso de retransmissão do cliente.</p></td></tr><tr><td><p><code>tcp_retransmission_delay_server</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Atraso de Retransmissão do Servidor</strong> — Atraso de retransmissão acumulado no lado do servidor.</p></td></tr><tr><td><p><code>tcp_retransmission_delay_server_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras de atraso de retransmissão do servidor.</p></td></tr></tbody></table>

<br />

### **2.7 KPIs de Janela e Reset TCP**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>tcp_client_resets</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de segmentos RST (reset) TCP enviados pelo cliente. Indica encerramentos de conexão anormais ou conexões recusadas do lado do cliente.</p></td></tr><tr><td><p><code>tcp_server_resets</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de segmentos RST TCP enviados pelo servidor.</p></td></tr><tr><td><p><code>tcp_window_size_client</code></p></td><td><p>uint64</p></td><td><p>bytes (soma)</p></td><td><p><strong>Tamanho da Janela do Cliente</strong> — Tamanhos da janela de recepção TCP acumulados anunciados pelo cliente. Usado para detectar tendências de tamanho de janela e condições de janela zero.</p></td></tr><tr><td><p><code>tcp_window_size_client_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras do tamanho da janela do cliente.</p></td></tr><tr><td><p><code>tcp_window_size_server</code></p></td><td><p>uint64</p></td><td><p>bytes (soma)</p></td><td><p><strong>Tamanho da Janela do Servidor</strong> — Tamanhos de janela de recepção acumulados anunciados pelo servidor.</p></td></tr><tr><td><p><code>tcp_window_size_server_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras do tamanho da janela do servidor.</p></td></tr></tbody></table>

<br />

### **Configuração TCP**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Tempo Limite de Fluxo</p></td><td><p>30 segundos</p></td><td><p>Tempo após o último pacote antes que um fluxo TCP seja considerado expirado.</p></td></tr><tr><td><p>Período de Relatório</p></td><td><p>30 segundos</p></td><td><p>Intervalo no qual as métricas de fluxo ao vivo são relatadas.</p></td></tr><tr><td><p>Tempo Limite de Reset</p></td><td><p>5 segundos</p></td><td><p>Tempo limite encurtado aplicado quando um RST TCP é detectado.</p></td></tr></tbody></table>

---

## 3\. UDP

O inspetor UDP cria fluxos baseados na 5-tupla e rastreia as métricas básicas da sessão. Como o UDP é sem conexão, as métricas são mais simples que o TCP.

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IP de origem (lado do uplink).</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IP de destino (lado do downlink).</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta de origem (uplink).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta de destino (downlink).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"UDP"</code>.</p></td></tr><tr><td><p><code>session_duration</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Duração da sessão UDP, calculada como a diferença entre os carimbos de data/hora do último e do primeiro pacote. Usada para cálculo de taxa de transferência: Throughput(UP) = volume_uplink / session_duration, Throughput(DOWN) = volume_downlink / session_duration.</p></td></tr><tr><td><p><code>flow_state</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Estado atual do fluxo UDP: <code>"established"</code> (ativo) ou <code>"finished"</code> (expirado ou fechado).</p></td></tr></tbody></table>

<br />

### **Configuração UDP**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Tempo Limite de Fluxo</p></td><td><p>30 segundos</p></td><td><p>Tempo após o último pacote antes que um fluxo UDP seja considerado expirado.</p></td></tr><tr><td><p>Período de Relatório</p></td><td><p>30 segundos</p></td><td><p>Intervalo para relatar as métricas de fluxo ao vivo.</p></td></tr></tbody></table>

---

## **4\. HTTP**

O inspetor HTTP opera no topo do TCP e analisa os pares de solicitação/resposta HTTP usando uma máquina de estado. Ele extrai metadados sobre transações da web.

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>host</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Host HTTP</strong> — Valor do campo de cabeçalho <code>Host</code> HTTP. Caracteres não-ASCII são removidos. Identifica o servidor web ou host virtual sendo acessado.</p></td></tr><tr><td><p><code>url</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>URL Completo</strong> — Construído a partir do esquema HTTP, host e caminho do URI (ex: <code>http://example.com/path/page</code>). Relatado apenas se houver um URI presente. Caracteres não-ASCII são removidos.</p></td></tr><tr><td><p><code>http_status_code</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Código de Status HTTP</strong> — O código de status da resposta e a frase de motivo (ex: <code>"200 OK"</code>, <code>"404 Not Found"</code>, <code>"503 Service Unavailable"</code>). Permite monitorar taxas de erro e a integridade do servidor.</p></td></tr></tbody></table>

<br />

### **Configuração HTTP**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Tempo Limite de Fluxo</p></td><td><p>30 segundos</p></td><td><p>Tempo limite de inatividade para fluxos HTTP.</p></td></tr><tr><td><p>Portas HTTP</p></td><td><p>80</p></td><td><p>Lista configurável de portas TCP para inspecionar tráfego HTTP.</p></td></tr><tr><td><p>Registro de Solicitações da Web</p></td><td><p>Desativado</p></td><td><p>Registro opcional de solicitações da web completas em um diretório de saída.</p></td></tr></tbody></table>

---

## **5\. TLS / HTTPS**

O inspetor TLS analisa o handshake TLS/SSL para extrair metadados de criptografia. Ele inspeciona até os primeiros 4 pacotes de uma conexão para analisar as mensagens ClientHello e ServerHello.

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>tls_version</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Versão TLS Negociada</strong> — A versão TLS/SSL efetiva negociada entre cliente e servidor. Determinada como o mínimo da versão máxima suportada por cada lado. Valores possíveis: <code>"ssl-2.0"</code>, <code>"ssl-3.0"</code>, <code>"tls-1.0"</code>, <code>"tls-1.1"</code>, <code>"tls-1.2"</code>, <code>"tls-1.3"</code>. Para detecção do TLS 1.3, a extensão <code>supported_versions</code> (tipo 43) no ClientHello/ServerHello é inspecionada.</p></td></tr><tr><td><p><code>tls_server_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Indicação de Nome do Servidor TLS (SNI)</strong> — O nome do host solicitado pelo cliente na extensão SNI do TLS ClientHello (tipo de extensão 0). Permite identificar qual site HTTPS está sendo acessado mesmo que o tráfego esteja criptografado. Caracteres não-ASCII são removidos.</p></td></tr><tr><td><p><code>host</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Mesmo que <code>tls_server_name</code>. Relatado no campo genérico <code>host</code> para uniformidade com os fluxos HTTP.</p></td></tr></tbody></table>

<br />

### **Configuração TLS**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Porta TLS</p></td><td><p>443</p></td><td><p>Porta TCP monitorada para tráfego TLS.</p></td></tr><tr><td><p>Tempo Limite de Fluxo</p></td><td><p>5 segundos</p></td><td><p>Tempo limite do fluxo TLS (mais curto já que apenas o handshake é analisado).</p></td></tr></tbody></table>

---

## **6\. DNS**

O inspetor DNS executa a inspeção profunda de pacotes de consultas e respostas DNS, rastreando o desempenho da resolução, estados das flags e condições de erro. Ele combina consultas DNS com respostas usando o ID de transação DNS.

<br />

### **6.1 Contadores de Consulta e Resposta**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>dns_query_count</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número total de pacotes de perguntas DNS observados neste fluxo.</p></td></tr><tr><td><p><code>dns_response_count</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número total de pacotes de respostas DNS observados.</p></td></tr><tr><td><p><code>dns_rcode_ok_count</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de respostas DNS bem-sucedidas (RCODE = 0, Sem Erro). Uma proporção alta de <code>rcode_ok_count / response_count</code> indica resolução DNS saudável.</p></td></tr></tbody></table>

<br />

### **6.2 KPIs de Desempenho**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>app_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>RTT do DNS</strong> — Tempo de ida e volta acumulado de resoluções DNS. Calculado como a diferença de tempo entre uma pergunta DNS e a sua resposta correspondente (correspondida por ID de transação DNS).</p></td></tr><tr><td><p><code>app_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de medições de RTT. RTT Médio do DNS = <code>app_rtt / app_rtt_samples</code>.</p></td></tr><tr><td><p><code>app_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Jitter do DNS</strong> — Soma das diferenças absolutas entre medições consecutivas de RTT do DNS. Indica variabilidade no tempo de resolução DNS.</p></td></tr><tr><td><p><code>app_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras de jitter.</p></td></tr><tr><td><p><code>app_packet_loss</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p><strong>Perda de Pacotes DNS</strong> — Número de consultas DNS que não receberam uma resposta correspondente (para fluxos concluídos), mais as respostas recebidas sem uma consulta correspondente. Indica perda de mensagens DNS ou tempo limite.</p></td></tr></tbody></table>

<br />

### **6.3 KPIs de Erro**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>app_packet_err_up</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de pacotes DNS malformados detectados na direção de uplink (consulta).</p></td></tr><tr><td><p><code>app_packet_err_down</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de pacotes DNS malformados detectados na direção de downlink (resposta).</p></td></tr></tbody></table>

<br />

### **6.4 Flags DNS**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>dns_flag_response</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p><code>1</code> se o último pacote DNS foi uma resposta, <code>0</code> se foi uma consulta.</p></td></tr><tr><td><p><code>dns_flag_opcode</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p><code>1</code> se o OPCODE DNS for diferente de zero (consulta não padrão, ex: consulta inversa ou solicitação de status).</p></td></tr><tr><td><p><code>dns_flag_truncated</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>Flag DNS TC (Truncação). <code>1</code> se a resposta foi truncada por exceder o tamanho máximo de mensagem UDP.</p></td></tr><tr><td><p><code>dns_flag_authoritative</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>Flag DNS AA (Resposta Autoritativa). <code>1</code> se o servidor respondente for autoritativo para o domínio consultado.</p></td></tr><tr><td><p><code>dns_flag_recursion_desired</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>Flag DNS RD (Recursão Desejada). <code>1</code> se o cliente solicitou resolução recursiva.</p></td></tr><tr><td><p><code>dns_flag_recursion_available</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>Flag DNS RA (Recursão Disponível). <code>1</code> se o servidor suportar consultas recursivas.</p></td></tr><tr><td><p><code>dns_flag_z</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>Flag DNS Z (Reservado). Deve ser zero nas implementações compatíveis.</p></td></tr><tr><td><p><code>dns_flag_ad</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>Flag DNS AD (Dados Autenticados). <code>1</code> se os dados de resposta tiverem sido verificados pelo DNSSEC.</p></td></tr><tr><td><p><code>dns_flag_cd</code></p></td><td><p>uint8</p></td><td><p>flag</p></td><td><p>Flag DNS CD (Verificação Desabilitada). <code>1</code> se a validação DNSSEC foi desabilitada para esta consulta.</p></td></tr><tr><td><p><code>dns_flag_reply_code</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Representação em string do RCODE DNS (ex: <code>"No Error"</code>, <code>"NXDomain"</code>, <code>"ServFail"</code>, <code>"Refused"</code>).</p></td></tr></tbody></table>

<br />

### **6.5 Detalhes de Consulta e Resposta**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>dns_query_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Nome(s) de domínio na consulta DNS. Vários nomes são separados por barra vertical (pipe) (ex: `"example.com</p></td></tr><tr><td><p><code>dns_query_type</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Tipo(s) de consulta DNS (ex: <code>"A"</code>, <code>"AAAA"</code>, <code>"MX"</code>, <code>"CNAME"</code>, <code>"SRV"</code>, <code>"PTR"</code>, <code>"TXT"</code>). Vários tipos são separados por barra vertical.</p></td></tr><tr><td><p><code>dns_query_class</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Classe de consulta DNS (normalmente <code>"IN"</code> para Internet). Várias classes são separadas por barra vertical.</p></td></tr><tr><td><p><code>dns_answer_address</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço(s) IP retornado(s) na seção de resposta DNS. Vários endereços são separados por barra vertical.</p></td></tr></tbody></table>

<br />

### **6.6 Identificação de Aplicação**

<table><tbody><tr><th><p>Campo Relatado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Nome da aplicação. Definido como <code>"DNS"</code> para fluxos DNS. Além disso, os nomes de host DNS são comparados com regras de assinatura de regex configuráveis (específicas do cliente e comuns) para classificar as aplicações através das suas pesquisas de DNS. Entradas correspondentes são armazenadas em cache e associadas aos endereços IP resolvidos para subsequente classificação de fluxo.</p></td></tr></tbody></table>

<br />

### **Configuração DNS**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Porta DNS</p></td><td><p>53</p></td><td><p>Porta UDP monitorada para tráfego DNS.</p></td></tr><tr><td><p>Configuração Regex do Cliente</p></td><td><p>—</p></td><td><p>Caminho para regras de assinatura regex de nome de host DNS específicas do cliente.</p></td></tr><tr><td><p>Configuração Regex Comum</p></td><td><p>—</p></td><td><p>Caminho para regras de assinatura regex de nome de host DNS comuns.</p></td></tr></tbody></table>

---

## **7\. SIP (Sinalização VoIP)**

O inspetor SIP fornece uma análise abrangente de sinalização VoIP. Ele rastreia todo o ciclo de vida dos diálogos SIP e produz KPIs alinhados com os padrões da indústria de telecomunicações (ASR, NER, NEC). Cada fluxo SIP é identificado por um UUID único e suporta o rastreamento de Call-ID de múltiplos diálogos.

<br />

### **7.1 KPIs de Tentativa e Conclusão de Chamadas**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_call_attempts</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Call Attempts</strong> — Número total de tentativas de iniciação de chamadas (mensagens INVITE enviadas), independentemente de serem bem-sucedidas.</p></td></tr><tr><td><p><code>sip_answered_calls</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Answered Calls</strong> — Número de chamadas atendidas pela parte chamada (INVITE seguido de 200 OK). Usado nos cálculos de NER (Network Effectiveness Ratio) e ASR (Answer-Seizure Ratio).</p></td></tr><tr><td><p><code>sip_successfully_ended_calls</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Successfully Ended Calls</strong> — Chamadas que concluíram todo o ciclo de vida: INVITE → 200 OK → BYE. Indica conclusão limpa da chamada sem término anormal.</p></td></tr><tr><td><p><code>sip_dropped_call</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Dropped Calls</strong> — Chamadas em que o INVITE foi bem-sucedido (200 OK recebido) mas nenhum BYE foi observado, indicando um término anormal/prematuro.</p></td></tr><tr><td><p><code>sip_user_busy</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>User Busy</strong> — Chamadas rejeitadas com SIP 486 (Busy Here). Usado em cálculos de NEC (Network Effectiveness Classification) e NER.</p></td></tr><tr><td><p><code>sip_no_answer</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>No Answer</strong> — Chamadas canceladas ou que esgotaram o tempo de limite sem serem atendidas. Usado em cálculos de NEC e NER.</p></td></tr><tr><td><p><code>sip_terminal_reject</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Terminal Reject</strong> — Chamadas rejeitadas com SIP 480 (Temporarily Unavailable). Usado em cálculos de NEC e NER.</p></td></tr></tbody></table>

<br />

### **7.2 KPIs de Duração da Chamada**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_call_duration</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Call Duration</strong> — Duração da chamada de voz desde o INVITE até o BYE. Usado para calcular a Duração Média da Chamada (ACD).</p></td></tr><tr><td><p><code>sip_short_duration_call</code></p></td><td><p>bool</p></td><td><p>flag</p></td><td><p><strong>Short Duration Call</strong> — Flag indicando que a duração da chamada esteve abaixo de um limite configurável. Chamadas curtas podem indicar problemas de qualidade da rede ou padrões de chamadas automatizadas (robocall).</p></td></tr><tr><td><p><code>sip_setup_duration</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Call Setup Duration</strong> — Tempo desde o primeiro INVITE aceito até o recebimento do 200 OK (atendimento da chamada). Reflete a latência de configuração da chamada / Atraso Pós-Discagem (PDD).</p></td></tr></tbody></table>

<br />

### **7.3 KPIs de Resposta ao INVITE**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_invite_any</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de solicitações INVITE enviadas (qualquer).</p></td></tr><tr><td><p><code>sip_invite_200</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs respondidos com 200 OK (configuração de chamada bem-sucedida).</p></td></tr><tr><td><p><code>sip_invite_3xx</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs recebendo respostas de redirecionamento 3XX.</p></td></tr><tr><td><p><code>sip_invite_480</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs recebendo 480 (Temporarily Unavailable).</p></td></tr><tr><td><p><code>sip_invite_486</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs recebendo 486 (Busy Here).</p></td></tr><tr><td><p><code>sip_invite_600</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs recebendo 600 (Busy Everywhere).</p></td></tr><tr><td><p><code>sip_invite_603</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>INVITEs recebendo 603 (Decline).</p></td></tr><tr><td><p><code>sip_re_invite_attempts</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Re-INVITE Attempts</strong> — Número de pacotes INVITE enviados após a primeira configuração de chamada bem-sucedida (Re-INVITE). Usado para alterações durante a chamada, como renegociação de codec ou transferência de chamada.</p></td></tr></tbody></table>

<br />

### **7.4 KPIs de REGISTER**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_register_any</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de solicitações REGISTER com qualquer status de resposta (excluindo os desafios de autenticação 401/402/407).</p></td></tr><tr><td><p><code>sip_register_ira</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Initial Registration Attempts</strong> — Solicitações REGISTER seguidas de respostas de falha 4XX/5XX/6XX (excluindo os desafios de autenticação 401/402/407). Indica falhas de registro.</p></td></tr><tr><td><p><code>sip_re_register_attempts_failed</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Failed Re-Registration Attempts</strong> — Solicitações REGISTER subsequentes que falharam após o registro inicial.</p></td></tr><tr><td><p><code>sip_re_register_time</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>Re-Registration Time</strong> — Tempo decorrido para os procedimentos de re-registro.</p></td></tr></tbody></table>

<br />

### **7.5 KPIs de Outros Métodos SIP**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_update_any</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de solicitações UPDATE enviadas. O UPDATE modifica os parâmetros da sessão.</p></td></tr><tr><td><p><code>sip_update_200</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Solicitações UPDATE respondidas com 200 OK.</p></td></tr><tr><td><p><code>sip_subscribe_attempts</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de solicitações SUBSCRIBE (notificações de eventos).</p></td></tr><tr><td><p><code>sip_notify_attempts</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de solicitações NOTIFY (entrega de notificações de eventos).</p></td></tr></tbody></table>

<br />

### **7.6 Carimbos de Data/Hora de Eventos SIP**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_invite_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora (timestamp) da solicitação INVITE.</p></td></tr><tr><td><p><code>sip_trying_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora da resposta 100 Trying.</p></td></tr><tr><td><p><code>sip_ringing_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora da resposta 180 Ringing.</p></td></tr><tr><td><p><code>sip_invite_ok_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora da resposta 200 OK do INVITE (chamada atendida).</p></td></tr><tr><td><p><code>sip_invite_failure_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora da resposta de falha do INVITE (4XX–6XX, excluindo a autenticação 407).</p></td></tr><tr><td><p><code>sip_bye_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora da solicitação BYE (início do encerramento da chamada).</p></td></tr><tr><td><p><code>sip_bye_ok_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora da resposta 200 OK do BYE.</p></td></tr><tr><td><p><code>sip_cancel_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora da solicitação CANCEL.</p></td></tr><tr><td><p><code>sip_cancel_ok_ts</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>Carimbo de data/hora da resposta 200 OK do CANCEL.</p></td></tr></tbody></table>

<br />

### **7.7 Campos de Cabeçalho SIP e KPIs de Erro**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_from</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Campo de cabeçalho SIP <code>From</code> identificando o autor da chamada. Analisado uma vez por diálogo.</p></td></tr><tr><td><p><code>sip_to</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Campo de cabeçalho SIP <code>To</code> identificando a parte chamada.</p></td></tr><tr><td><p><code>sip_user_agent_client</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Cabeçalho User-Agent do UAC (cliente). Identifica o software do cliente SIP (ex., modelo de telefone, aplicação de softphone).</p></td></tr><tr><td><p><code>sip_user_agent_server</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Cabeçalho User-Agent do UAS (servidor). Identifica o servidor SIP ou o software do PBX.</p></td></tr><tr><td><p><code>sip_failure_response_code</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>Primeiro código de resposta de falha recebido (4XX–6XX, excluindo a autenticação 407). Salvo uma vez por diálogo.</p></td></tr><tr><td><p><code>sip_reason</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Cabeçalho SIP <code>Reason</code> (RFC 3326) fornecendo a causa legível por máquina para o término da chamada. Pode estar vazio.</p></td></tr><tr><td><p><code>sip_temporary_error_count</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Número de respostas de erro temporário recebidas durante uma transação INVITE.</p></td></tr><tr><td><p><code>sip_call_state</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Estado final da chamada. Reportado uma vez por chamada: <code>"COMPLETED"</code>, <code>"BUSY"</code>, <code>"CANCELLED"</code>, <code>"NOT_AVAILABLE"</code>, <code>"TIMEDOUT"</code>.</p></td></tr></tbody></table>

<br />

### **7.8 Contadores de Pacotes SIP**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>sip_packet_count_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de pacotes SIP na direção uplink (envio).</p></td></tr><tr><td><p><code>sip_packet_count_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de pacotes SIP na direção downlink (recebimento).</p></td></tr><tr><td><p><code>sip_packet_count_segmented_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes SIP segmentados (incompletos/divididos) no uplink. Indica mensagens SIP que abrangem múltiplos segmentos TCP.</p></td></tr><tr><td><p><code>sip_packet_count_segmented_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes SIP segmentados no downlink.</p></td></tr><tr><td><p><code>sip_packet_count_error_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes SIP malformados / vazios / corrompidos no uplink.</p></td></tr><tr><td><p><code>sip_packet_count_error_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes SIP malformados no downlink.</p></td></tr><tr><td><p><code>sip_packet_count_retrans_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes SIP retransmitidos no uplink. A retransmissão SIP é detectada na camada de aplicação.</p></td></tr><tr><td><p><code>sip_packet_count_retrans_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes SIP retransmitidos no downlink.</p></td></tr><tr><td><p><code>sip_packet_count_compound_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes SIP compostos (múltiplas mensagens SIP num único pacote) no uplink.</p></td></tr><tr><td><p><code>sip_packet_count_compound_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes SIP compostos no downlink.</p></td></tr></tbody></table>

<br />

### **7.9 Diagrama de Sequência de Chamada VoIP**

O inspetor SIP também gera um Diagrama de Sequência de Chamada VoIP como um arquivo XDR no formato CSV para a análise visual do fluxo de chamadas:

<table><tbody><tr><th><p>CSV Field</p></th><th><p>Description</p></th></tr><tr><td><p><code>timestamp</code></p></td><td><p>Carimbo de data/hora do pacote</p></td></tr><tr><td><p><code>sip_call_id</code></p></td><td><p>Cabeçalho Call-ID SIP</p></td></tr><tr><td><p><code>ip_src</code> / <code>ip_dst</code></p></td><td><p>Endereços IP de origem e destino</p></td></tr><tr><td><p><code>srcport</code> / <code>dstport</code></p></td><td><p>Portas de origem e destino</p></td></tr><tr><td><p><code>proto</code></p></td><td><p>Protocolo de transporte (TCP/UDP)</p></td></tr><tr><td><p><code>phone_from</code> / <code>phone_to</code></p></td><td><p>Números de telefone extraídos dos cabeçalhos SIP From/To</p></td></tr><tr><td><p><code>sip_from</code> / <code>sip_to</code></p></td><td><p>Campos SIP From/To completos</p></td></tr><tr><td><p><code>msg</code></p></td><td><p>Mensagem SIP (nome do método de solicitação ou código de status de resposta)</p></td></tr><tr><td><p><code>comment</code></p></td><td><p>Anotação no diagrama de sequência</p></td></tr><tr><td><p><code>raw_sip_line</code></p></td><td><p>Primeira linha da mensagem SIP bruta</p></td></tr></tbody></table>

<br />

### **Configuração do SIP**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>SIP Port</p></td><td><p>5060</p></td><td><p>Porta monitorada para o tráfego SIP (TCP e UDP).</p></td></tr><tr><td><p>Flow Timeout</p></td><td><p>5 seconds</p></td><td><p>Tempo de inatividade limite para fluxos SIP. Configurável via XML.</p></td></tr></tbody></table>

---

## **8\. RTP / RTCP (Mídia VoIP)**

O inspetor RTP fornece o conjunto mais abrangente de KPIs no sistema, medindo a qualidade da mídia em tempo real para as chamadas VoIP. Todas as métricas são reportadas por direção (uplink/downlink) para permitir uma avaliação independente de cada fluxo de áudio. O inspetor está fortemente integrado ao inspetor SIP através de estruturas de dados compartilhadas para a correlação de chamadas.

<br />

### **8.1 Identificação & KPIs de Codec**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Rótulo da aplicação: <code>"RTP"</code> para fluxos RTP, <code>"RTCP"</code> para fluxos apenas RTCP.</p></td></tr><tr><td><p><code>voip_uuid</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>UUID que vincula esse fluxo RTP ao seu fluxo SIP pai.</p></td></tr><tr><td><p><code>sip_call_id</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Call-ID SIP da chamada VoIP associada.</p></td></tr><tr><td><p><code>rtp_ssrc_up</code></p></td><td><p>string</p></td><td><p>hex</p></td><td><p><strong>SSRC (Synchronization Source)</strong> — Identificador SSRC do fluxo no uplink em hexadecimal. Identifica de forma única o fluxo RTP na sessão.</p></td></tr><tr><td><p><code>rtp_ssrc_down</code></p></td><td><p>string</p></td><td><p>hex</p></td><td><p>Identificador SSRC no downlink.</p></td></tr><tr><td><p><code>rtp_encoding_name_up</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Codec Name</strong> — Codec de áudio usado na direção do uplink (ex., <code>"PCMU"</code>, <code>"PCMA"</code>, <code>"G729"</code>, <code>"OPUS"</code>, <code>"AMR"</code>). Para tipos de carga útil dinâmica, reportado como <code>"RTP-Type-XX"</code> onde XX é o número do tipo da carga útil.</p></td></tr><tr><td><p><code>rtp_encoding_name_down</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Codec de áudio usado na direção de downlink.</p></td></tr><tr><td><p><code>rtp_payload_type_up</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>Número do tipo de carga útil RTP no uplink (0–127). Tipos estáticos (0–95) possuem mapeamentos fixos de codec; tipos dinâmicos (96–127) são resolvidos via negociação SDP.</p></td></tr><tr><td><p><code>rtp_payload_type_down</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>Número do tipo de carga útil RTP no downlink.</p></td></tr><tr><td><p><code>rtp_sample_rate_up</code></p></td><td><p>int</p></td><td><p>Hz</p></td><td><p>Taxa de amostragem de áudio para o codec no uplink (ex., 8000, 16000, 48000 Hz).</p></td></tr><tr><td><p><code>rtp_sample_rate_down</code></p></td><td><p>int</p></td><td><p>Hz</p></td><td><p>Taxa de amostragem de áudio no downlink.</p></td></tr><tr><td><p><code>rtp_channels_up</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>Número de canais de áudio no uplink (1 = mono, 2 = estéreo).</p></td></tr><tr><td><p><code>rtp_channels_down</code></p></td><td><p>int</p></td><td><p>—</p></td><td><p>Número de canais de áudio no downlink.</p></td></tr></tbody></table>

<br />

### **8.2 KPIs de Contagem de Pacotes**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_packet_count_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de pacotes RTP recebidos na direção uplink.</p></td></tr><tr><td><p><code>rtp_packet_count_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de pacotes RTP recebidos na direção downlink.</p></td></tr><tr><td><p><code>rtp_rtcp_packet_count_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de pacotes RTCP na direção uplink.</p></td></tr><tr><td><p><code>rtp_rtcp_packet_count_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Total de pacotes RTCP na direção downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_lost_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Lost Packets</strong> — Pacotes RTP perdidos no uplink, detectados pelas lacunas no número de sequência RTP. Usa o algoritmo RFC 3550 com tratamento de wrap-around.</p></td></tr><tr><td><p><code>rtp_packet_count_lost_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes perdidos no downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_dup_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Duplicate Packets</strong> — Pacotes RTP com um número de sequência já visto (duplicados).</p></td></tr><tr><td><p><code>rtp_packet_count_dup_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes duplicados no downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_ooo_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Out-of-Order Packets</strong> — Pacotes RTP chegando fora de ordem de sequência no uplink.</p></td></tr><tr><td><p><code>rtp_packet_count_ooo_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes fora de ordem no downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_error_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Invalid RTP Packets</strong> — Pacotes que falharam na validação RTP no uplink.</p></td></tr><tr><td><p><code>rtp_packet_count_error_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes RTP inválidos no downlink.</p></td></tr><tr><td><p><code>rtcp_packet_count_error_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes RTCP inválidos no uplink.</p></td></tr><tr><td><p><code>rtcp_packet_count_error_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes RTCP inválidos no downlink.</p></td></tr></tbody></table>

<br />

### **8.3 Contadores Específicos de Carga Útil**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_packet_count_codec_change_real_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Real Codec Changes</strong> — Número de vezes que o codec de áudio foi alterado durante o fluxo (excluindo Ruído de Conforto e DTMF). Indica a renegociação do codec no meio da chamada.</p></td></tr><tr><td><p><code>rtp_packet_count_codec_change_real_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Mudanças reais de codec no downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_codec_change_any_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Any Codec Changes</strong> — Todas as mudanças de tipo de carga útil, incluindo transições de/para o Ruído de Conforto e DTMF.</p></td></tr><tr><td><p><code>rtp_packet_count_codec_change_any_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Qualquer mudança de codec no downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_marker_bit_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Marker Bit Packets</strong> — Pacotes com o bit marcador RTP ativado, indicando tipicamente o início de um surto de fala após um silêncio.</p></td></tr><tr><td><p><code>rtp_packet_count_marker_bit_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes com bit marcador no downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_cn_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Comfort Noise Packets</strong> — Pacotes RTP transportando a carga útil de Ruído de Conforto (CN), gerados durante os períodos de silêncio nas chamadas de voz.</p></td></tr><tr><td><p><code>rtp_packet_count_cn_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes de Ruído de Conforto no downlink.</p></td></tr><tr><td><p><code>rtp_packet_count_dtmf_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>DTMF Packets</strong> — Pacotes RTP que transportam os eventos telefônicos DTMF (RFC 4733).</p></td></tr><tr><td><p><code>rtp_packet_count_dtmf_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Pacotes DTMF no downlink.</p></td></tr></tbody></table>

<br />

### **8.4 KPIs de Jitter**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_jitter_interarrival_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Interarrival Jitter</strong> — O Jitter da RFC 3550, calculado como a variação estatística nos tempos de chegada dos pacotes RTP no uplink. Fórmula: `J(i) = J(i-1) + (</p></td></tr><tr><td><p><code>rtp_jitter_interarrival_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Jitter inter-chegada no downlink.</p></td></tr><tr><td><p><code>rtp_jitter_mean_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Mean Jitter</strong> — Média de todas as medições de jitter ao longo do fluxo no uplink.</p></td></tr><tr><td><p><code>rtp_jitter_mean_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Jitter médio no downlink.</p></td></tr><tr><td><p><code>rtp_jitter_max_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Maximum Jitter</strong> — O maior valor de jitter observado no fluxo de uplink. Indica a pior variação de temporização do caso.</p></td></tr><tr><td><p><code>rtp_jitter_max_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Jitter máximo no downlink.</p></td></tr></tbody></table>

<br />

### **8.5 KPIs de Delta (Intervalo de Chegada de Pacotes)**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_delta_mean_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Mean Delta</strong> — Tempo médio entre chegadas consecutivas de pacotes RTP no uplink. O valor nominal depende do codec (ex., 20 ms para G.711). Desvios indicam atrasos ou buffering na rede.</p></td></tr><tr><td><p><code>rtp_delta_mean_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Delta médio no downlink.</p></td></tr><tr><td><p><code>rtp_delta_max_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Maximum Delta</strong> — A maior lacuna de chegada interpacotes no uplink. Indica a pior rajada de atraso ou lacuna de pacotes.</p></td></tr><tr><td><p><code>rtp_delta_max_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Delta máximo no downlink.</p></td></tr></tbody></table>

<br />

### **8.6 KPIs de Skew (Desvio de Timestamp)**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_skew_mean_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Mean Skew</strong> — Desvio médio entre os timestamps RTP e os tempos reais de chegada dos pacotes no uplink. Um desvio positivo significa que os pacotes chegam mais rápido do que o esperado; um negativo significa mais lento. Medido em unidades da taxa de amostragem do codec.</p></td></tr><tr><td><p><code>rtp_skew_mean_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Skew médio no downlink.</p></td></tr><tr><td><p><code>rtp_skew_max_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Maximum Skew</strong> — O maior desvio de timestamp observado no uplink.</p></td></tr><tr><td><p><code>rtp_skew_max_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Skew máximo no downlink.</p></td></tr></tbody></table>

<br />

### **8.7 KPIs de Largura de Banda**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_bandwidth_mean_up</code></p></td><td><p>double</p></td><td><p>kbps</p></td><td><p><strong>Mean Bandwidth</strong> — Largura de banda média do fluxo RTP no uplink, calculada ao longo de uma janela deslizante de 1 segundo de bytes de carga útil.</p></td></tr><tr><td><p><code>rtp_bandwidth_mean_down</code></p></td><td><p>double</p></td><td><p>kbps</p></td><td><p>Largura de banda média no downlink.</p></td></tr><tr><td><p><code>rtp_bandwidth_max_up</code></p></td><td><p>double</p></td><td><p>kbps</p></td><td><p><strong>Maximum Bandwidth</strong> — Pico de largura de banda de 1 segundo observado no uplink.</p></td></tr><tr><td><p><code>rtp_bandwidth_max_down</code></p></td><td><p>double</p></td><td><p>kbps</p></td><td><p>Largura de banda máxima no downlink.</p></td></tr><tr><td><p><code>rtp_total_volume_up</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p><strong>Total Volume</strong> — Total cumulativo de bytes de carga útil RTP no uplink.</p></td></tr><tr><td><p><code>rtp_total_volume_down</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Volume total de bytes de carga útil no downlink.</p></td></tr></tbody></table>

<br />

### **8.8 KPIs de Qualidade (MOS / R-Factor)**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_mos_up</code></p></td><td><p>double</p></td><td><p>score</p></td><td><p><strong>Mean Opinion Score (MOS)</strong> — Pontuação de qualidade de voz estimada para o uplink (escala de 1,0–5,0). Calculada a partir de estatísticas do Receiver Report RTCP usando o algoritmo E-model. Reportado apenas se ≥ 1,0. Valores maiores indicam melhor qualidade: 4,0+ = Qualidade de pedágio, 3,5+ = Aceitável.</p></td></tr><tr><td><p><code>rtp_mos_down</code></p></td><td><p>double</p></td><td><p>score</p></td><td><p>MOS para o fluxo de downlink.</p></td></tr><tr><td><p><code>rtp_r_factor_up</code></p></td><td><p>double</p></td><td><p>—</p></td><td><p><strong>R-Factor</strong> — O fator R E-model ITU-T G.107 para o uplink (escala de 0–100). Combina os efeitos de codec, atraso, perda e jitter numa única métrica de qualidade. R &gt; 80 = Alta qualidade, R &gt; 70 = Média, R &gt; 60 = Baixa, R &lt; 50 = Ruim.</p></td></tr><tr><td><p><code>rtp_r_factor_down</code></p></td><td><p>double</p></td><td><p>—</p></td><td><p>R-Factor para o downlink.</p></td></tr><tr><td><p><code>rtp_rtt_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Round-Trip Time</strong> — O RTT entre os pontos de extremidade como medido pelos Sender/Receiver Reports (SR/RR) RTCP. Apenas reportado se &gt; 0.</p></td></tr><tr><td><p><code>rtp_rtt_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>RTT no downlink.</p></td></tr><tr><td><p><code>rtp_transit_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Transit Time</strong> — Atraso de trânsito em sentido único, estimado como RTT/2.</p></td></tr><tr><td><p><code>rtp_transit_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Tempo de trânsito no downlink.</p></td></tr></tbody></table>

<br />

### **8.9 KPIs de Desvio de Relógio e Frequência**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_clock_drift_up</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p><strong>Clock Drift</strong> — O desvio acumulado de relógio entre o relógio RTP do remetente e o relógio de parede do receptor no uplink. Calculado através da regressão linear dos tempos de chegada versus os timestamps RTP. Fórmula: <code>drift = 1000 duration (clock_ratio - 1.0)</code>.</p></td></tr><tr><td><p><code>rtp_clock_drift_down</code></p></td><td><p>double</p></td><td><p>ms</p></td><td><p>Desvio de relógio no downlink.</p></td></tr><tr><td><p><code>rtp_freq_drift_hz_up</code></p></td><td><p>double</p></td><td><p>Hz</p></td><td><p><strong>Frequency Drift</strong> — Desvio expresso em Hz relativo à taxa de amostragem nominal. Fórmula: <code>clock_ratio * sample_rate</code>.</p></td></tr><tr><td><p><code>rtp_freq_drift_hz_down</code></p></td><td><p>double</p></td><td><p>Hz</p></td><td><p>Desvio de frequência no downlink.</p></td></tr><tr><td><p><code>rtp_freq_drift_percentage_up</code></p></td><td><p>double</p></td><td><p>%</p></td><td><p><strong>Frequency Drift Percentage</strong> — Desvio como uma porcentagem da taxa de amostragem nominal. Fórmula: <code>100 * (clock_ratio - 1.0)</code>.</p></td></tr><tr><td><p><code>rtp_freq_drift_percentage_down</code></p></td><td><p>double</p></td><td><p>%</p></td><td><p>Porcentagem do desvio de frequência no downlink.</p></td></tr></tbody></table>

<br />

### **8.10 KPIs de Número de Sequência e Duração**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_seq_first_up</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Primeiro número de sequência RTP visto no fluxo uplink.</p></td></tr><tr><td><p><code>rtp_seq_first_down</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Primeiro número de sequência no downlink.</p></td></tr><tr><td><p><code>rtp_seq_last_up</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Último número de sequência RTP visto no uplink.</p></td></tr><tr><td><p><code>rtp_seq_last_down</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Último número de sequência no downlink.</p></td></tr><tr><td><p><code>rtp_seq_err_up</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p><strong>Sequence Errors</strong> — O total de anomalias de sequência (perdidos + duplicados + fora de ordem) no uplink.</p></td></tr><tr><td><p><code>rtp_seq_err_down</code></p></td><td><p>uint64</p></td><td><p>count</p></td><td><p>Erros de sequência no downlink.</p></td></tr><tr><td><p><code>rtp_ts_first_up</code></p></td><td><p>uint32</p></td><td><p>RTP ts</p></td><td><p>Primeiro valor de timestamp RTP no uplink.</p></td></tr><tr><td><p><code>rtp_ts_first_down</code></p></td><td><p>uint32</p></td><td><p>RTP ts</p></td><td><p>Primeiro valor de timestamp RTP no downlink.</p></td></tr><tr><td><p><code>rtp_ts_last_up</code></p></td><td><p>uint32</p></td><td><p>RTP ts</p></td><td><p>Último valor de timestamp RTP no uplink.</p></td></tr><tr><td><p><code>rtp_ts_last_down</code></p></td><td><p>uint32</p></td><td><p>RTP ts</p></td><td><p>Último valor de timestamp RTP no downlink.</p></td></tr><tr><td><p><code>rtp_duration_up</code></p></td><td><p>double</p></td><td><p>seconds</p></td><td><p><strong>Stream Duration</strong> — Duração do fluxo RTP no uplink.</p></td></tr><tr><td><p><code>rtp_duration_down</code></p></td><td><p>double</p></td><td><p>seconds</p></td><td><p>Duração do fluxo no downlink.</p></td></tr></tbody></table>

<br />

### **8.11 KPIs de DTMF (Evento Telefônico)**

<table><tbody><tr><th><p>Reported Field</p></th><th><p>Type</p></th><th><p>Unit</p></th><th><p>Description</p></th></tr><tr><td><p><code>rtp_dtmf_tones_up</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>DTMF Tone Sequence</strong> — A string de eventos DTMF detectados no uplink (ex., <code>"1234567890*#ABCD"</code>). Cada caractere representa um dígito DTMF detectado.</p></td></tr><tr><td><p><code>rtp_dtmf_tones_down</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Tons DTMF no downlink.</p></td></tr><tr><td><p><code>rtp_dtmf_tones_volume_min_up</code></p></td><td><p>int</p></td><td><p>dBm</p></td><td><p><strong>Minimum DTMF Volume</strong> — O nível de volume mais baixo dos eventos DTMF no uplink (valores numéricos maiores indicam menor volume).</p></td></tr><tr><td><p><code>rtp_dtmf_tones_volume_min_down</code></p></td><td><p>int</p></td><td><p>dBm</p></td><td><p>Volume mínimo do DTMF no downlink.</p></td></tr><tr><td><p><code>rtp_dtmf_tones_volume_max_up</code></p></td><td><p>int</p></td><td><p>dBm</p></td><td><p><strong>Maximum DTMF Volume</strong> — O maior nível de volume de eventos DTMF no uplink.</p></td></tr><tr><td><p><code>rtp_dtmf_tones_volume_max_down</code></p></td><td><p>int</p></td><td><p>dBm</p></td><td><p>Volume máximo de DTMF no downlink.</p></td></tr></tbody></table>

<br />

### **Configuração RTP**

<table><tbody><tr><th><p>Parameter</p></th><th><p>Default</p></th><th><p>Description</p></th></tr><tr><td><p>Flow Timeout</p></td><td><p>5 seconds</p></td><td><p>Tempo de inatividade limite para os fluxos RTP.</p></td></tr><tr><td><p>Ports</p></td><td><p>Dynamic</p></td><td><p>As portas RTP não são configuradas estaticamente; elas são descobertas através da negociação SDP na sinalização SIP.</p></td></tr></tbody></table>

---
## **9\. ICMP**

O inspetor ICMP rastreia fluxos de Echo Request/Reply (ping) e calcula métricas de desempenho de ida e volta com base na correspondência de pares de solicitação-resposta.

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>IP de origem (solicitante do echo).</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>IP de destino (respondente do echo).</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Campo Identificador ICMP (usado como uma pseudo-porta para identificação de fluxo).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>O mesmo campo Identificador ICMP.</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"ICMP"</code>.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"ICMP"</code>.</p></td></tr><tr><td><p><code>icmp_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>RTT ICMP</strong> — Soma dos tempos de ida e volta medidos correspondendo Echo Requests ICMP (tipo 8) com Echo Replies (tipo 0).</p></td></tr><tr><td><p><code>icmp_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras RTT.</p></td></tr><tr><td><p><code>app_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p>O mesmo que <code>icmp_rtt</code>, reportado no campo genérico de RTT da aplicação.</p></td></tr><tr><td><p><code>app_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>O mesmo que <code>icmp_rtt_samples</code>.</p></td></tr><tr><td><p><code>icmp_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Jitter ICMP</strong> — Soma das diferenças absolutas entre medições RTT consecutivas.</p></td></tr><tr><td><p><code>icmp_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras de jitter.</p></td></tr><tr><td><p><code>app_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p>O mesmo que <code>icmp_jitter</code>, campo genérico de jitter da aplicação.</p></td></tr><tr><td><p><code>app_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>O mesmo que <code>icmp_jitter_samples</code>.</p></td></tr><tr><td><p><code>icmp_min_rtt</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>RTT Mínimo</strong> — Menor tempo de ida e volta observado no fluxo.</p></td></tr><tr><td><p><code>icmp_max_rtt</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p><strong>RTT Máximo</strong> — Maior tempo de ida e volta observado.</p></td></tr><tr><td><p><code>icmp_packet_loss</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p><strong>Perda de Pacotes ICMP</strong> — Número de Echo Requests sem correspondência (nenhum Reply correspondente recebido).</p></td></tr><tr><td><p><code>app_packet_loss</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>O mesmo que <code>icmp_packet_loss</code>, campo genérico.</p></td></tr></tbody></table>

<br />

### **Lógica de Direção ICMP**

-   ICMP tipo 8 (Echo Request) → classificado como **uplink**
-   Todos os outros tipos ICMP → classificados como **downlink**

<br />

### **Configuração ICMP**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Timeout de Fluxo</p></td><td><p>15 segundos</p></td><td><p>Timeout de inatividade para fluxos ICMP.</p></td></tr><tr><td><p>Período de Relatório</p></td><td><p>30 segundos</p></td><td><p>Intervalo de relatório.</p></td></tr></tbody></table>

---

## **10\. ICMPv6**

O inspetor ICMPv6 espelha a funcionalidade ICMP para redes IPv6, rastreando pares de Echo Request/Reply e calculando métricas de desempenho para operações de ping IPv6.

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IPv6 de origem (solicitante do echo).</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IPv6 de destino (respondente do echo).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"ICMPV6"</code>.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"ICMPV6"</code>.</p></td></tr><tr><td><p><code>icmp_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>RTT ICMPv6</strong> — Soma dos tempos de ida e volta do Echo Request (tipo 128) para o Echo Reply (tipo 129).</p></td></tr><tr><td><p><code>icmp_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras RTT.</p></td></tr><tr><td><p><code>app_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p>Campo genérico RTT.</p></td></tr><tr><td><p><code>app_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Contagem de amostras RTT.</p></td></tr><tr><td><p><code>icmp_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Jitter ICMPv6</strong> — Soma das diferenças absolutas RTT.</p></td></tr><tr><td><p><code>icmp_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Contagem de amostras de jitter.</p></td></tr><tr><td><p><code>app_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p>Campo genérico de jitter.</p></td></tr><tr><td><p><code>app_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Contagem de amostras de jitter.</p></td></tr><tr><td><p><code>icmp_min_rtt</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>RTT Mínimo observado.</p></td></tr><tr><td><p><code>icmp_max_rtt</code></p></td><td><p>uint64</p></td><td><p>µs</p></td><td><p>RTT Máximo observado.</p></td></tr><tr><td><p><code>icmp_packet_loss</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Echo Requests sem correspondência (perda de pacotes).</p></td></tr><tr><td><p><code>app_packet_loss</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Campo genérico de perda de pacotes.</p></td></tr></tbody></table>

<br />

### **Lógica de Direção ICMPv6**

-   ICMPv6 tipo 128 (Echo Request) → classificado como **uplink**
-   Todos os outros tipos → classificados como **downlink**

<br />

### **Configuração ICMPv6**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Timeout de Fluxo</p></td><td><p>15 segundos</p></td><td><p>Timeout de inatividade.</p></td></tr><tr><td><p>Período de Relatório</p></td><td><p>30 segundos</p></td><td><p>Intervalo de relatório.</p></td></tr></tbody></table>

---

## **11\. DHCP**

O inspetor DHCP rastreia transações DHCP combinando pacotes usando a ID da transação (XID). Ele monitora o desempenho do handshake DHCP e detecta erros de pacotes.

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IP do cliente (uplink).</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IP do servidor (downlink).</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta do cliente (tipicamente 68).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta do servidor (tipicamente 67).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"DHCP"</code>.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"DHCP"</code>.</p></td></tr><tr><td><p><code>app_rtt</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>RTT DHCP</strong> — Tempo de ida e volta das transações DHCP (ex., DISCOVER → OFFER, REQUEST → ACK). Correspondido usando a ID da transação DHCP (XID).</p></td></tr><tr><td><p><code>app_rtt_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras RTT.</p></td></tr><tr><td><p><code>app_jitter</code></p></td><td><p>uint64</p></td><td><p>µs (soma)</p></td><td><p><strong>Jitter DHCP</strong> — Variabilidade entre RTTs de transações DHCP consecutivas.</p></td></tr><tr><td><p><code>app_jitter_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de amostras de jitter.</p></td></tr><tr><td><p><code>app_packet_loss</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p><strong>Perda de Pacotes DHCP</strong> — Solicitações DHCP sem correspondência (nenhuma resposta do servidor correspondente).</p></td></tr><tr><td><p><code>app_packet_err_up</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Pacotes DHCP malformados na direção de uplink.</p></td></tr><tr><td><p><code>app_packet_err_down</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Pacotes DHCP malformados na direção de downlink.</p></td></tr></tbody></table>

<br />

### **Configuração DHCP**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Timeout de Fluxo</p></td><td><p>5 segundos</p></td><td><p>Timeout de inatividade para fluxos DHCP.</p></td></tr><tr><td><p>Período de Relatório</p></td><td><p>30 segundos</p></td><td><p>Intervalo de relatório.</p></td></tr><tr><td><p>Tamanho Mín. do Pacote</p></td><td><p>240 bytes</p></td><td><p>Comprimento mínimo aceito do pacote DHCP.</p></td></tr></tbody></table>

---

## **12\. DHCPv6**

O inspetor DHCPv6 lida com DHCP para redes IPv6, rastreando transações pelo campo de ID de transação de 24 bits. Ele valida tipos de mensagens DHCPv6 (1–13 por RFC 8415) e portas (546 cliente, 547 servidor).

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IPv6 do cliente.</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IPv6 do servidor.</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta do cliente (546).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta do servidor (547).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"DHCP"</code>.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"DHCP"</code>.</p></td></tr><tr><td><p><code>app_packet_err_up</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Pacotes DHCPv6 inválidos no uplink (tipo de mensagem errado, comprimento inválido, etc.).</p></td></tr><tr><td><p><code>app_packet_err_down</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Pacotes DHCPv6 inválidos no downlink.</p></td></tr></tbody></table>

<br />

### **Configuração DHCPv6**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Timeout de Fluxo</p></td><td><p>5 segundos</p></td><td><p>Timeout de inatividade.</p></td></tr><tr><td><p>Tamanho Mín. do Pacote</p></td><td><p>4 bytes</p></td><td><p>Tamanho mínimo do pacote (tipo de mensagem + ID da transação).</p></td></tr></tbody></table>

---

## **13\. TWAMP**

O inspetor TWAMP (Two-Way Active Measurement Protocol, RFC 5357) suporta o protocolo de controle (TCP porta 862) e o protocolo de teste (portas UDP dinâmicas). Ele mede atraso de ida (one-way delay) e jitter entre os endpoints sender (remetente) e reflector (refletor) TWAMP.

<br />

### **13.1 Estados do Protocolo de Controle TWAMP**

O inspetor implementa a máquina de estado de controle TWAMP completa:

<table><tbody><tr><th><p>Estado</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>GREETING</code></p></td><td><p>Servidor envia mensagem de saudação de 64 bytes.</p></td></tr><tr><td><p><code>SETUP_RESPONSE</code></p></td><td><p>Cliente responde com parâmetros de setup.</p></td></tr><tr><td><p><code>SERVER_START</code></p></td><td><p>Servidor confirma início de sessão.</p></td></tr><tr><td><p><code>REQUEST_SESSION</code></p></td><td><p>Cliente solicita uma sessão de teste (portas sender/receiver extraídas).</p></td></tr><tr><td><p><code>ACCEPT_SESSION</code></p></td><td><p>Servidor aceita (porta receiver confirmada).</p></td></tr><tr><td><p><code>START_SESSIONS</code></p></td><td><p>Cliente inicia sessões de teste.</p></td></tr><tr><td><p><code>START_SESSIONS_ACK</code></p></td><td><p>Servidor confirma início de teste.</p></td></tr><tr><td><p><code>STOP_SESSIONS</code></p></td><td><p>Cliente interrompe sessões de teste.</p></td></tr></tbody></table>

<br />

### **13.2 KPIs de Teste TWAMP**

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>twamp_sender_packet_number</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de pacotes de teste enviados pelo sender TWAMP. Redefinido após cada relatório.</p></td></tr><tr><td><p><code>twamp_receiver_packet_number</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de pacotes de teste recebidos pelo refletor TWAMP. Redefinido após cada relatório.</p></td></tr><tr><td><p><code>twamp_delay</code></p></td><td><p>int64</p></td><td><p>ns (soma)</p></td><td><p><strong>Atraso One-Way</strong> — Medições de atraso one-way acumuladas. Calculado a partir de timestamps TWAMP: <code>delay = receiver_t2 - sender_t2 - (receiver_t1 - receiver_t0)</code>. Correspondido por números de sequência.</p></td></tr><tr><td><p><code>twamp_delay_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de medições de atraso. Atraso médio = <code>twamp_delay / twamp_delay_samples</code>.</p></td></tr><tr><td><p><code>jitter</code></p></td><td><p>int64</p></td><td><p>ns (soma)</p></td><td><p><strong>Jitter TWAMP</strong> — Soma das diferenças absolutas entre medições de atraso consecutivas. Fórmula: `</p></td></tr><tr><td><p><code>jitter_samples</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Número de medições de jitter.</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Sempre <code>"twamp-test"</code>.</p></td></tr></tbody></table>

<br />

### **Configuração TWAMP**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Porta de Controle</p></td><td><p>862</p></td><td><p>Porta TCP para protocolo de controle TWAMP.</p></td></tr><tr><td><p>Timeout de Fluxo</p></td><td><p>5 segundos</p></td><td><p>Timeout de inatividade.</p></td></tr></tbody></table>

---

## **14\. FTP**

O inspetor FTP identifica conexões de controle e de dados FTP e rastreia o estabelecimento de canal de dados em modo ativo/passivo. Ele classifica fluxos FTP e analisa mensagens de controle para descobrir conexões de dados FTP dinamicamente.

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Assinatura de aplicação FTP. Sempre <code>"ftp"</code> independentemente de ser uma conexão de controle ou dados.</p></td></tr></tbody></table>

<br />

### **Lógica de Detecção FTP**

<table><tbody><tr><th><p>Porta</p></th><th><p>Tipo</p></th><th><p>Descrição</p></th></tr><tr><td><p>21</p></td><td><p>Controle</p></td><td><p>Canal de controle FTP (comandos e respostas).</p></td></tr><tr><td><p>20</p></td><td><p>Dados</p></td><td><p>Canal de dados FTP (transferências de arquivos).</p></td></tr><tr><td><p>Dinâmico</p></td><td><p>Dados (passivo)</p></td><td><p>Descoberto analisando respostas <code>PASV</code> (227) no canal de controle.</p></td></tr><tr><td><p>Dinâmico</p></td><td><p>Dados (ativo)</p></td><td><p>Descoberto analisando comandos <code>PORT</code> no canal de controle.</p></td></tr></tbody></table>

<br />

### **Análise de Mensagens de Controle FTP**

O inspetor analisa mensagens de controle FTP, incluindo:

-   **Comando PORT**: Extrai IP e porta do cliente para conexões de dados em modo ativo (formato: `PORT h1,h2,h3,h4,p1,p2`).
-   **227 (Modo Passivo)**: Extrai IP e porta do servidor para conexões de dados em modo passivo.
-   **226 (Transferência Concluída)**: Detecta conclusão bem-sucedida de transferência de arquivo.
-   **426 (Transferência Abortada)**: Detecta transferências abortadas.

---

## **15\. GRE**

O inspetor GRE (Generic Routing Encapsulation) desencapsula túneis GRE, permitindo a análise do tráfego interno (encapsulado). O inspetor extrai os campos de cabeçalho GRE e encadeia para o inspetor do protocolo interno apropriado.

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>gre_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Tipo de Protocolo GRE</strong> — O EtherType do protocolo encapsulado (ex., <code>0x0800</code> para IPv4, <code>0x86DD</code> para IPv6).</p></td></tr></tbody></table>

<br />

### **Campos de Cabeçalho GRE Analisados**

<table><tbody><tr><th><p>Campo</p></th><th><p>Tamanho</p></th><th><p>Descrição</p></th></tr><tr><td><p>Flags &amp; Versão</p></td><td><p>2 bytes</p></td><td><p>Flags GRE, incluindo presença de checksum (bit 15) e presença de chave (bit 13).</p></td></tr><tr><td><p>Tipo de Protocolo</p></td><td><p>2 bytes</p></td><td><p>EtherType do protocolo interno.</p></td></tr><tr><td><p>Checksum</p></td><td><p>2 bytes</p></td><td><p>Opcional; presente se a flag de checksum estiver definida.</p></td></tr><tr><td><p>Reservado</p></td><td><p>2 bytes</p></td><td><p>Opcional; presente com checksum.</p></td></tr><tr><td><p>Chave</p></td><td><p>4 bytes</p></td><td><p>Chave de túnel opcional; presente se a flag de chave estiver definida.</p></td></tr></tbody></table>

Após o desencapsulamento, o pacote interno é entregue ao inspetor IP apropriado para análise completa do protocolo, portanto, todos os KPIs do protocolo interno (TCP, UDP, etc.) são reportados como métricas aninhadas do fluxo GRE.

---

## **16\. Camada de Aplicação (DPI)**

O inspetor de Camada de Aplicação usa Deep Packet Inspection (DPI) para classificar tráfego por aplicação. Ele combina múltiplas técnicas de identificação: correspondência de assinatura de payload, classificação baseada em DNS e classificação 5-tuple baseada em DPDK.

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Nome da Aplicação</strong> — Nome da aplicação identificada pelo motor DPI ou classificação baseada em DNS (ex., <code>"youtube"</code>, <code>"facebook"</code>, <code>"netflix"</code>). O padrão é <code>"generic-app"</code> se não identificado.</p></td></tr><tr><td><p><code>app_code</code></p></td><td><p>uint32</p></td><td><p>—</p></td><td><p><strong>Código da Aplicação</strong> — Identificador numérico de aplicação que combina um código de grupo (11 bits, até 2048 grupos) e código de aplicação (21 bits, até ~2M apps). Codificado como `(group_code &lt;&lt; 21)</p></td></tr><tr><td><p><code>dpi_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Nome da classificação do motor DPI.</p></td></tr><tr><td><p><code>policy_id</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>ID da política de rede associada ao fluxo (do classificador DPDK).</p></td></tr><tr><td><p><code>policy_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Nome da política legível por humanos.</p></td></tr><tr><td><p><code>first_pph</code></p></td><td><p>uint64</p></td><td><p>—</p></td><td><p><strong>Hash do Payload do Primeiro Pacote</strong> — Hash de 64 bits do payload do primeiro pacote de dados. Usado para fingerprinting de tráfego e correspondência de assinaturas.</p></td></tr><tr><td><p><code>packet_ports</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p><strong>Portas de Pacotes</strong> — Lista separada por ponto e vírgula de nomes de portas observadas no fluxo.</p></td></tr><tr><td><p><code>volume_uplink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Volume de payload da aplicação na direção de uplink.</p></td></tr><tr><td><p><code>volume_downlink</code></p></td><td><p>uint64</p></td><td><p>bytes</p></td><td><p>Volume de payload da aplicação na direção de downlink.</p></td></tr><tr><td><p><code>net_src_packets</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Contagem de pacotes de uplink na camada de aplicação.</p></td></tr><tr><td><p><code>net_dst_packets</code></p></td><td><p>uint64</p></td><td><p>contagem</p></td><td><p>Contagem de pacotes de downlink.</p></td></tr></tbody></table>

<br />

### **Processo de Classificação DPI**

1.  **Inspeção de Payload** (primeiros 8 pacotes): Assinaturas DPI são aplicadas ao payload do pacote até que uma aplicação seja identificada ou 8 pacotes tenham sido inspecionados.
2.  **Pré-classificação DNS**: Hostnames de respostas DNS são correspondidos com regras de assinatura regex configuráveis. IPs resolvidos a partir de hostnames correspondentes são armazenados em cache, e fluxos subsequentes para esses IPs herdam a classificação da aplicação.
3.  **Classificação 5-Tuple DPDK**: Regras de ACL aceleradas por hardware classificam fluxos por 5-tuple para aplicação de políticas.

<br />

### **Configuração DPI da Aplicação**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Timeout de Fluxo</p></td><td><p>30 segundos</p></td><td><p>Timeout de inatividade do fluxo da aplicação.</p></td></tr><tr><td><p>Período de Relatório</p></td><td><p>30 segundos</p></td><td><p>Intervalo de relatório.</p></td></tr><tr><td><p>Recarregamento de Assinatura</p></td><td><p>60 segundos</p></td><td><p>Intervalo para verificar atualizações de arquivos de assinatura DPI.</p></td></tr><tr><td><p>Comprimento Máx. de Verificação</p></td><td><p>2000 bytes</p></td><td><p>Máximo de bytes de payload verificados por pacote para assinaturas regex.</p></td></tr></tbody></table>

---

## **17\. Outros Protocolos L4**

O inspetor "Outros L4" lida com protocolos IP que não são TCP, UDP, ICMP, ICMPv6 ou GRE. Ele fornece rastreamento básico de fluxo e identificação usando uma tabela de pesquisa de protocolo.

<table><tbody><tr><th><p>Campo Reportado</p></th><th><p>Tipo</p></th><th><p>Unidade</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>net_src_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IP de origem.</p></td></tr><tr><td><p><code>net_dst_ip</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Endereço IP de destino.</p></td></tr><tr><td><p><code>net_src_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta de origem (definida como 0 para protocolos sem portas).</p></td></tr><tr><td><p><code>net_dst_port</code></p></td><td><p>uint16</p></td><td><p>—</p></td><td><p>Porta de destino (definida como 0).</p></td></tr><tr><td><p><code>ip_protocol</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Nome do protocolo da tabela de pesquisa (ex., <code>"SCTP"</code>, <code>"OSPF"</code>, <code>"PIM"</code>, <code>"OTHER"</code>).</p></td></tr><tr><td><p><code>app_name</code></p></td><td><p>string</p></td><td><p>—</p></td><td><p>Nome do protocolo em maiúsculas.</p></td></tr></tbody></table>

<br />

### **Configuração de Outros L4**

<table><tbody><tr><th><p>Parâmetro</p></th><th><p>Padrão</p></th><th><p>Descrição</p></th></tr><tr><td><p>Timeout de Fluxo</p></td><td><p>30 segundos</p></td><td><p>Timeout de inatividade.</p></td></tr><tr><td><p>Período de Relatório</p></td><td><p>30 segundos</p></td><td><p>Intervalo de relatório.</p></td></tr></tbody></table>

---

## **Apêndice: Arquitetura da Cadeia de Inspetores**

O sistema processa pacotes através de uma cadeia de inspetores de protocolo, onde cada inspetor lida com uma camada de protocolo e delega para a próxima:

```
Ethernet Inspector
  ├── VLAN Inspector (802.1Q / MPLS)
  │     └── IP Inspector
  ├── IP Inspector (IPv4)
  │     ├── IPv6 Inspector (tunneled)
  │     ├── TCP Inspector
  │     │     ├── HTTP Inspector
  │     │     ├── TLS Inspector
  │     │     ├── SIP Inspector
  │     │     ├── FTP Inspector
  │     │     └── TWAMP Inspector (control)
  │     ├── UDP Inspector
  │     │     ├── DNS Inspector
  │     │     ├── SIP Inspector
  │     │     ├── RTP Inspector
  │     │     ├── DHCP Inspector
  │     │     ├── DHCPv6 Inspector
  │     │     └── TWAMP Inspector (test)
  │     ├── ICMP Inspector
  │     ├── GRE Inspector → (re-enters IP Inspector)
  │     ├── IP Inspector (IP-in-IP)
  │     └── Other L4 Inspector
  └── IPv6 Inspector
        ├── TCP Inspector → (same sub-tree as above)
        ├── UDP Inspector → (same sub-tree as above)
        ├── ICMPv6 Inspector
        └── Other L4 Inspector
```

O **Inspetor de Aplicação (DPI)** opera como uma camada de overlay separada, recebendo fluxos dos inspetores TCP e UDP e realizando inspeção profunda de pacotes (DPI) para identificação da aplicação.

Cada fluxo é identificado unicamente por um hash de sua 5-tuple (IP de origem, IP de destino, porta de origem, porta de destino, protocolo) e ID de VLAN, calculado usando o algoritmo xxHash. O estado do fluxo é mantido através dos pacotes e relatado em intervalos configuráveis ou no encerramento do fluxo.
