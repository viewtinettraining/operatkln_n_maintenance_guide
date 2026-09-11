---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'IP Address Converter'
id: VRJ-3SH-NUH-NLG
slug: ip-address-converter
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 16:58:00'
---
# **<span align="center">IP Address Converter</span>**

<br />

O handler de grid **IP Address Converter** é usado para realizar conversões entre formatos de string de endereço IP padrão e suas representações matemáticas (Inteiros ou Hexadecimais), e vice-versa. 

Isso é particularmente útil quando fontes de dados brutas fornecem endereços IP como inteiros decimais ou hexadecimais, que precisam ser traduzidos para endereços IP decimais com pontos legíveis para análise, ou quando você precisa compactar IPs em representações inteiras.

<br />

---

## **Configuração**

A configuração do IP Address Converter é simples. Ela requer três parâmetros principais para processar os dados:

-   **Field:** A coluna de origem na sua grid que contém o valor que você deseja converter.
-   **Output column name:** A coluna de destino onde o handler escreverá o valor convertido resultante. Se esta coluna não existir, ela será criada.
-   **Mode:** O tipo de operação de conversão que você deseja realizar.

<br />

### **Modos Disponíveis**

O handler suporta quatro modos de conversão diferentes dependendo das suas necessidades:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/ip-address-converter-modes.png" align="center"></figure>

<br />

-   **IP Address to Int:** Converte um endereço IP decimal com pontos padrão (por exemplo, `192.168.1.1`) para sua representação Inteira de 32 bits.
-   **Int to IP Address:** Converte uma representação Inteira de 32 bits de volta para um endereço IP decimal com pontos padrão.
-   **IP Address to Hexadecimal:** Converte um endereço IP decimal com pontos padrão para sua representação Hexadecimal.
-   **Hexadecimal to IP Address:** Converte uma representação de string Hexadecimal de volta para um endereço IP decimal com pontos padrão.

<br />