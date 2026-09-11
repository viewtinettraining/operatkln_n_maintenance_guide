---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Delta'
id: O5N-F9C-S8E-1VL
slug: delta
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 08:29:56'
---
# **<span align="center">Delta</span>**

<br />

O handler de grid **Delta** é um componente poderoso que calcula a diferença (delta) entre o valor de um campo na iteração atual e seu valor na iteração anterior durante o processo ETL.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/delta.png" align="center"></figure>

<br />

---

### **Configuração**

A configuração do handler de grid **Delta** envolve as seguintes etapas sequenciais:

1.  **Selecionar o Grid-Handler**: Clique no botão "ADD NEW GRID-HANDLER" e selecione **Delta** no menu suspenso `Grid Handler Type`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/delta-step1a.png" align="center"></figure>

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/delta-step1b.png" align="center"></figure>

<br />

2.  **Selecionar as Keys**: No menu suspenso `Keys`, selecione a(s) chave(s) que você deseja usar como agrupadores para a métrica ou contador. Essas chaves identificam de forma única a entidade para a qual o delta é calculado (por exemplo, `host` e `interface`).
3.  **Selecionar a Column**: No menu suspenso `Column`, escolha o campo numérico no qual a operação delta será realizada.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/delta-step3.png" align="center"></figure>

<br />

---

### **Exemplo de Caso de Uso: Contadores SNMP**

Um cenário comum para o handler de grid Delta é o processamento de contadores SNMP. Ao coletar métricas como octetos de entrada e saída das interfaces de rede via SNMP, os valores retornados geralmente são **contadores cumulativos** desde a última vez em que o agente SNMP foi reiniciado.

Para obter a quantidade real e absoluta de tráfego (octetos) transmitida entre cada intervalo de polling do ETL, você deve calcular o delta.

#### **Por que combinar múltiplas Keys?**

Neste cenário, um dispositivo de rede (host) pode ter várias interfaces. Portanto, o estado deve ser rastreado usando uma combinação das chaves `host` e `interface` em conjunto:

-   Se apenas a chave `interface` fosse usada, o cálculo do delta poderia ser corrompido, pois vários dispositivos distintos podem compartilhar nomes de interface idênticos (por exemplo, `eth0`).
-   Ao combinar `host` e `interface` como **Keys**, o handler de grid Delta calcula corretamente a diferença para cada interface exclusiva em cada dispositivo exclusivo.

<br />

<div class="sd-callout" data-callout-type="tip"><strong>Melhor Prática:</strong> Sempre avalie seu ambiente e modelo de dados específicos. A combinação de chaves necessária para rastrear o estado de forma exclusiva varia dependendo da natureza das fontes de dados.</div>

<br />