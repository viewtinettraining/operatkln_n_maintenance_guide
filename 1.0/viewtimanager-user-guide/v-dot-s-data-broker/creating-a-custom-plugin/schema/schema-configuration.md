---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Schema Configuration'
id: SCH-CNF-STG-002
slug: schema-configuration
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 17:00:00'
---
# **<span align="center">Configuração de Schema</span>**

<br />

Uma vez que as etapas de **Extração (Extract)**, **Transformação (Transform)** e **Carregamento (Load)** foram configuradas com sucesso, é necessário concluir a configuração ajustando a etapa de **Schema**. Esta etapa define como os dados coletados serão estruturados e interpretados pelo banco de dados e pelo Viewtisight.

Para começar, clique no botão **SCHEMA** no menu principal do Plugin Creator.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-button.png" align="center"></figure>

<br />

---

## **Estado Inicial e Configurações de Modelo (Model Settings)**

Ao entrar na configuração de Schema, o sistema tenta preencher automaticamente as **Model Settings** com base no nome da pipeline. Ele pré-preencherá o nome da tabela de destino (`Set`) e as políticas de retenção padrão.

No entanto, se você rolar para baixo até a seção **Fields** (Campos), notará que ela está completamente vazia. A plataforma não sabe automaticamente quais colunas existem em seu fluxo de dados até que você a instrua explicitamente a lê-las a partir das etapas anteriores.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-empty-fields.png" align="center"></figure>

<br />

---

## **Preenchendo Campos (Populating Fields)**

Para importar automaticamente a estrutura dos seus dados, você deve usar o botão **POPULATE FROM PREVIOUS STAGE** (Preencher a Partir da Etapa Anterior) localizado no canto superior direito da tela.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-populate-button.png" align="center"></figure>

<br />

Clicar neste botão aciona a plataforma para ler a grade final gerada pela etapa de **Transformação (Transform)**. Em seguida, o sistema cria automaticamente uma coluna de banco de dados correspondente para cada campo presente naquela grade.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-populated-fields.png" align="center"></figure>

<br />

---

## **Atribuição Automática de Métricas e Dimensões**

Quando os campos são preenchidos, o V.S. Data Broker aplica padrões inteligentes para categorizar cada campo como sendo uma **Métrica (Metric)** ou uma **Dimensão (Dimension)** com base em seu tipo de dados:

-   **Dimensões:** Campos de string (texto) são automaticamente categorizados como Dimensões. Estes são usados para filtrar, agrupar e categorizar seus dados em dashboards (ex., `host`, `interface`, `city`).
-   **Métricas:** Campos numéricos (`int64`, `double`) são automaticamente categorizados como Métricas. Estes são os valores quantificáveis que serão medidos e agregados (ex., `interface-in-octets`, `interface-in-errors`).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-metric-dimension.png" align="center"></figure>

<br />

Embora a plataforma atribua essas funções padrão automaticamente, você mantém o controle total para ajustá-las. Você pode alterar manualmente um campo numérico de Métrica para Dimensão se ele representar um ID e não um valor mensurável.

<br />

---

## **Métricas Calculadas Simples e Unidades**

Para aqueles campos categorizados como **Métricas**, a etapa de Schema oferece a capacidade de criar **métricas calculadas simples** diretamente durante a inserção (o conceito completo de métricas calculadas é explicado em detalhes no guia do Viewtisight). 

Para configurar uma métrica calculada simples a partir desta etapa, basta abrir o menu suspenso na coluna **Agg. Function** (Função de Agregação) para a métrica desejada e selecionar a função de agregação apropriada (ex., `sum`, `avg`, `max`, `count`).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-simple-metrics.png" align="center"></figure>

<br />

Adicionalmente, você pode definir a **Unit** (Unidade) base da métrica na coluna `Units` (ex., `bps`, `bytes`, `ms`). 

> [!NOTE] **Unidades Dimensionadas (Scaled Units)**
> Se a sua unidade de medida requer dimensionamento/escala para fins de exibição (por exemplo, converter `bps` para `Kbps`, `Mbps`, ou `Gbps` automaticamente nos dashboards), essa configuração de escala deve ser feita mais tarde no **Metrics Composer** (a forma como trabalhar com esse recurso é explicada no guia do Viewtisight). A etapa de Schema apenas define a unidade base.

<br />
