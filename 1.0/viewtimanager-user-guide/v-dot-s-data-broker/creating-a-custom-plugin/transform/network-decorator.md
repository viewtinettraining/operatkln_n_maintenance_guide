---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Network Decorator'
id: NET-DEC0-GH1-TR4
slug: network-decorator
isVisible: true
isSearchable: true
lastUpdated: '2026-05-20 20:30:00'
---
# **<span align="center">Network Decorator</span>**

<br />

O handler de grid **Network Decorator** é um componente de transformação poderoso que compartilha o mesmo conceito subjacente que o CSV Decorator, mas é projetado especificamente para **correspondência de endereço IP e sub-rede**. 

Ele pega uma coluna da Grid contendo um endereço IP e o compara com um arquivo CSV de referência contendo sub-redes ou endereços IP específicos em notação CIDR (por exemplo, `/24`, `/16` ou `/32` para um único host). Se o endereço IP da Grid estiver dentro de uma sub-rede definida no arquivo CSV, o handler adiciona as informações descritivas correspondentes em novas colunas da Grid.

<br />

---

## **Casos de Uso**

Este handler é geralmente usado para enriquecer endereços IP com informações contextuais, tais como:
-   **Pertencimento à Sub-rede:** Identificando a qual segmento de rede um endereço IP pertence (por exemplo, `Rede de Madrid`, `Rede de Miami`).
-   **Departamento ou Área:** Mapeando endereços IP para departamentos específicos (por exemplo, `Sub-rede RH`, `Servidores de TI`).
-   **Localização / Site:** Associando tráfego ou logs com locais físicos ou filiais com base no endereço IP.
-   **Identificação de Dispositivo:** Usando uma máscara `/32` para identificar hosts específicos ou dispositivos críticos dentro da rede.

<br />

---

## **Configuração e Exemplo Prático**

Para configurar o Network Decorator, você deve definir o arquivo CSV de pesquisa e mapear a coluna de IP de origem para as colunas descritivas de destino.

<br />

### **Passo 1: O Arquivo CSV de Referência**

O arquivo CSV de pesquisa deve conter pelo menos duas colunas: uma para a rede/IP em notação CIDR, e uma (ou mais) para a informação descritiva a ser adicionada. 

Neste exemplo, o arquivo CSV `network_decorator_example.csv` contém uma coluna `net` com as sub-redes e uma coluna `descriptive_field` com os nomes de localização:

-   `192.168.32.0/24` -> `Madrid Network`
-   `172.16.0.0/16` -> `Miami Network`
-   `10.30.23.1/32` -> `Device Example` (usando `/32` para indicar um host específico)

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/network-decorator-csv.png" align="center"></figure>

<br />

### **Passo 2: Configuração do Grid Handler**

Na etapa de Transformação, adicione um novo handler **Net Decorator** e configure-o da seguinte maneira:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/network-decorator-config.png" align="center"></figure>

<br />

-   **CSV File Path:** Selecione o arquivo CSV de referência contendo as sub-redes.
-   **Source Columns:** Defina a relação de pesquisa.
    -   `CSV Name` = `net` (a coluna contendo as sub-redes CIDR).
    -   `Grid Name` = `net_src_ip` (a coluna na Grid contendo os endereços IP reais a serem avaliados).
-   **Destination Columns:** Defina onde as novas informações serão armazenadas.
    -   `CSV Name` = `descriptive_field` (o valor descritivo do CSV).
    -   `Grid Name` = `descriptive_value` (a nova coluna que será criada na Grid).
-   **Default value if not found:** Defina um rótulo padrão como `No_info_provided` para endereços IP que não correspondem a nenhuma sub-rede no arquivo CSV.

<br />

**Resultado:**

Se a Grid contiver o IP `192.168.32.45` na coluna `net_src_ip`, o handler o avaliará em relação ao arquivo CSV, determinará que ele pertence à sub-rede `192.168.32.0/24`, e criará uma nova coluna `descriptive_value` com o texto `Madrid Network`.

<br />

---

<div class="sd-callout" data-callout-type="info"><strong>Net IPv6 Decorator:</strong> Observe que existe um Grid Handler separado chamado <strong>Net IPv6 Decorator</strong>. Ele aplica exatamente a mesma metodologia e processo de configuração descritos neste documento, com a única diferença sendo que as sub-redes no arquivo CSV devem ser definidas usando a notação IPv6.</div>

<br />
