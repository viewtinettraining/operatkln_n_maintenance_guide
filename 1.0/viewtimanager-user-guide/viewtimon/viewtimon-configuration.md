---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtimon Configuration'
id: D4S-M0QZ-2PC-2AM
slug: viewtimon-configuration
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 18:56:18'
---
# **<span align="center">Configuração do Viewtimon</span>**

<br />

A guia **CONFIGURATION** dentro da interface do Viewtimon é onde você define os parâmetros principais de processamento, ativa inspetores de tráfego específicos e habilita recursos avançados de solução de problemas.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-configuration.png" align="center"></figure>

<br />

---

## **1\. Configuração do Viewtimon (Instâncias)**

Esta seção rege os recursos fundamentais alocados ao mecanismo DPI.

-   **Number of Instances:** Este campo define quantas instâncias do mecanismo DPI serão executadas em paralelo. O dimensionamento recomendado é de **1 instância para cada 500 Mbps de tráfego** que a sonda deverá processar. Dimensionar isso corretamente garante que o sistema possa lidar com o volume de tráfego sem perder pacotes.
-   **Reporting period (secs):** Define a frequência com que o mecanismo agrega e descarrega as métricas obtidas no banco de dados (por exemplo, `1 min`).

## **2\. Inspetores (Inspectors)**

Os inspetores são módulos internos especializados responsáveis por dissecar protocolos de aplicativos específicos.

Ao ativar essas caixas de seleção (TLS, DNS, VOIP, HTTP, DHCP, FTP), você ativa o inspetor correspondente.

> <div class="sd-callout" data-callout-type="info"><strong>Coleta de KPI</strong> Esses inspetores são diretamente responsáveis por obter as ricas métricas específicas de protocolo. Os KPIs que cada inspetor é capaz de extrair são detalhados na página de <a href="kpireference.md" target="_blank">Referência de KPI</a>. Se um inspetor estiver desabilitado, seus KPIs correspondentes não serão coletados.</div>

## **3\. Sniffer do Viewtimon**

O **Viewtimon Sniffer** é um recurso avançado que transforma a sonda em uma ferramenta completa de captura de pacotes (semelhante ao Wireshark), permitindo uma análise forense profunda do tráfego de rede.

Ao marcar a caixa **Enable**, o mecanismo começa a salvar arquivos `pcap` brutos com base no tráfego que ele vê.

Você pode controlar ainda mais esse recurso usando:

-   **Packet Truncation:** Permite limitar o comprimento máximo dos pacotes capturados (por exemplo, `32766` bytes). Truncar pacotes é útil se você precisar inspecionar apenas os cabeçalhos em vez de cargas úteis completas, economizando um espaço em disco significativo.
-   **Capture Filters:** Você pode adicionar filtros específicos (`Type`, `Value`, `Length`) para que o sniffer capture apenas o tráfego que corresponda a determinados critérios (por exemplo, endereços IP ou portas específicas), em vez de capturar todo o tráfego da rede.

<br />