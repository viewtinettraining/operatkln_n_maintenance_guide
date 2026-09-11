---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Schema Intro'
id: FC4-5QC6-JEY-R9H
slug: schema-intro
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 14:24:18'
---
# **<span align="center">Etapa de Schema (Schema Stage)</span>**

<br />

A etapa **Schema** é a última etapa de configuração de um plugin dentro do V.S. Data Broker. Esta etapa atende a dois propósitos críticos principais:

1.  **Configuração de Banco de Dados:** Define como a tabela é estruturada, suas políticas de retenção e os períodos de particionamento dentro do banco de dados de séries temporais da Viewtinet.
2.  **Preparação de Dados para o Viewtisight:** Especifica a formatação exata, dimensões, métricas, tabelas agregadas e alarmes em tempo real que estarão disponíveis posteriormente para visualização e análise no Viewtisight.

<br />

---

## **Configurações de Modelo (Model Settings)**

A seção inicial controla a estrutura principal do banco de dados e a lógica de retenção.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-viewticore-config.png" align="center"></figure>

<br />

### **Configuração de Tabela e Dados Brutos**

-   **Set:** O nome da tabela de destino no banco de dados (ex., `snmp_interface_records_info`).
-   **Tenant Field:** Define qual coluna atua como o **identificador de tenant** para separar logicamente os dados dentro da mesma tabela. Isso é comumente definido como `host`.
-   **Retention Period for Raw Data:** Especifica por quanto tempo os **registros brutos (não processados)** serão mantidos antes de serem automaticamente purgados/apagados (ex., `5 days`).
-   **Partition Period for Raw Data:** Define o intervalo de particionamento interno usado pela engine de banco de dados para otimizar o desempenho de consultas (ex., `1 day`).

### **Granularidades e Política de Tabelas Agregadas**

Esta seção controla a criação e retenção de **tabelas agregadas** em diferentes granularidades de tempo.

> \[!NOTE\] **Nem Todos os Dados Devem Ser Agregados**<br />
> Conforme explicado na teoria conceitual, **nem todas as fontes de dados são suscetíveis de serem agregadas**. A agregação é obrigatória para protocolos de escuta de alto volume (NetFlow, Syslog) ou operações de polling frequentes (interfaces SNMP) para compactar os dados, mas normalmente é desabilitada para polling leve (SNMP health, ICMP).

Cada linha representa um nível de agregação que pode ser individualmente **habilitado ou desabilitado**:

<table><tbody><tr><th><p>Granularity</p></th><th><p>Retention Period</p></th><th><p>Partition Period</p></th><th><p>Enabled</p></th></tr><tr><td><p>1 minute</p></td><td><p>3 days</p></td><td><p>1 day</p></td><td><p>☐</p></td></tr><tr><td><p>5 minutes</p></td><td><p>1 week</p></td><td><p>1 day</p></td><td><p>☑</p></td></tr><tr><td><p>1 hour</p></td><td><p>1 week</p></td><td><p>1 day</p></td><td><p>☑</p></td></tr><tr><td><p>1 day</p></td><td><p>1 day</p></td><td><p>1 day</p></td><td><p>☑</p></td></tr></tbody></table>

<br />

---

## **Campos (Fields)**

A seção **Fields** é onde você revisa e configura cada coluna que existirá na tabela do banco de dados. Esses campos são herdados da grade produzida durante a etapa de Transformação (Transform).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-fields-config.png" align="center"></figure>

<br />

Para cada coluna, você pode configurar:

-   **Field Name:** O nome interno da coluna no V.S. Data Broker.
-   **DataBase Name:** O nome real da coluna que será criada no Postgres/ViewtinetDB.
-   **Type:** O tipo de dados SQL (ex., `int64`, `string`, `double`).
-   **Max Length / Precision / Scale:** Restrições opcionais para comprimentos de string ou precisão decimal.
-   **Metric/Dimension:** Uma configuração crucial para o Viewtisight. Uma **Dimensão** é um atributo usado para agrupar ou filtrar dados (ex., `host`, `interface_description`). Uma **Métrica** é um valor numérico no qual podem ser feitas operações matemáticas.
-   **Agg. Function:** Se o campo for marcado como uma Métrica, a atribuição de uma Função de Agregação predefinida (como `sum`, `avg`, `max`) prepara automaticamente esta métrica para ser usada de forma eficiente nos dashboards do Viewtisight.
-   **Units:** Define o rótulo da unidade (ex., `bps`, `bytes`, `ms`).

<br />

---

## **Tabelas Agregadas (Dimensões e Métricas)**

Se você habilitou quaisquer granularidades nas Model Settings (Configurações de Modelo), esta seção permite definir exatamente **como** essas tabelas agregadas serão construídas.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-aggregated-tables-fields.png" align="center"></figure>

<br />

Aqui, você seleciona quais **Dimensões** e **Métricas** específicas da sua tabela principal serão resumidas e empurradas para as tabelas agregadas secundárias.

Por padrão, a plataforma agrupa os registros com base nas dimensões selecionadas no intervalo de tempo definido (ex., a cada 5 minutos), aplica a `Agg. Function` às métricas e armazena os resultados compactados. Isso reduz o volume e acelera drasticamente as consultas de tendências de longo prazo.

<br />

---

## **Alarmes (Alarms)**

A etapa de Schema também permite definir **alarmes em tempo real**.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-alarms-config.png" align="center"></figure>

<br />

Os alarmes configurados aqui são avaliados **no momento da inserção**. Isso significa que assim que o sistema grava o registro no banco de dados, ele avalia instantaneamente a métrica em relação ao limite configurado.

-   **Alarm name:** O identificador do alarme (ex., `Interfaz caído`).
-   **Metrics:** A coluna específica sendo avaliada (ex., `interface-oper-status`).
-   **Dimension Keys:** As dimensões que dão contexto ao alarme, permitindo que você saiba exatamente qual dispositivo ou interface o disparou (ex., `host`, `interface`, `interface-description`).

<br />