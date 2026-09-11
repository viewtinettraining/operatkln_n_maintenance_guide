---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Endereço IP para Código de País'
id: EI8-ME8-7VV-CQB
slug: ip-address-to-country-code
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 16:50:00'
---
# **<span align="center">IP Address to Country Code</span>**

<br />

O handler de grid **IP Address to Country Code** fornece uma maneira rápida e eficiente de realizar geolocalização em dados de rede. 

**Definição:** *Este handler é capaz de adicionar/atualizar uma coluna de string, ipaddress ou ipaddressv6 geolocalizando endereços IP em códigos de país.*

Ao pegar um endereço IP de origem do fluxo de dados, este handler o compara com um banco de dados predefinido e atribui o Código de País de 2 letras correspondente a uma coluna de destino.

<br />

---

## **Pré-requisitos: O Arquivo de Mapeamento**

Antes de configurar o handler de grid, o sistema requer um arquivo de mapeamento CSV estruturado que correlacione faixas de sub-redes IP aos seus respectivos códigos de país. 

Para obter e manter esse arquivo de mapeamento automaticamente, você deve criar um pipeline usando o **conector "IP to Country Code"**. Este conector baixa e atualiza periodicamente o banco de dados de geolocalização. 

<div class="sd-callout" data-callout-type="info"><strong>Referência:</strong> Consulte a seção <strong>Extract</strong> desta documentação para ver exatamente como configurar o conector "IP to Country Code".</div>

Uma vez baixado, o arquivo ficará semelhante a esta estrutura:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/ip-to-country-mapping.png" align="center"></figure>

<br />

Como você pode ver, o arquivo contém a família de IPs, o IP inicial (`from`), o IP final (`to`) e o `country_code` resultante (por exemplo, CN, JP, AU, TH).

<br />

---

## **Configuração**

Uma vez que o arquivo de mapeamento esteja disponível no servidor, você pode configurar o Grid Handler.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/ip-to-country-config.png" align="center"></figure>

<br />

A configuração requer três parâmetros principais:

-   **Column:** A coluna de origem na sua grid que contém o endereço IP que você deseja geolocalizar. No exemplo acima, isso está definido como `remip`.
-   **Target Column:** A coluna de destino onde o handler escreverá o código de país de 2 letras resultante. Se a coluna não existir, ela será criada. No exemplo, ele escreve em `remcountry`.
-   **Mapping File Path:** O caminho absoluto no servidor onde o arquivo CSV de geolocalização está armazenado (por exemplo, `/opt/vn/dhyana/var/data/ip2country/ip2countrysys`). Este arquivo é gerado pelo conector Extract mencionado nos pré-requisitos.

<br />