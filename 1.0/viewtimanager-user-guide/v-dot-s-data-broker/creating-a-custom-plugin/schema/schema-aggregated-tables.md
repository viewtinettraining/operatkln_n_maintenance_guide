---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Creating Aggregated Tables'
id: SCH-AGG-TBL-003
slug: schema-aggregated-tables
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 17:36:00'
---
# **<span align="center">Criando Tabelas Agregadas</span>**

<br />

Em ambientes de alto volume, consultar dados brutos abrangendo longos períodos (semanas ou meses) pode consumir muitos recursos. Para otimizar o desempenho e a velocidade de visualização, a **etapa Schema** (Schema Stage) permite a criação de **Tabelas Agregadas** (Aggregated Tables).

<br />

---

## **O que são Tabelas Agregadas?**

Tabelas agregadas armazenam **dados pré-processados e resumidos** derivados de registros brutos detalhados. Em vez de manter milhões de pontos de dados individuais, a plataforma calcula resumos (usando funções como `sum()`, `avg()`, `count()`) em intervalos regulares e armazena os resultados.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-concept.png" align="center"></figure>

<br />

Ao consultar estas tabelas otimizadas em vez dos dados brutos, os dashboards carregam significativamente mais rápido e o volume de dados armazenados é drasticamente reduzido.

<br />

---

## **Granularidades em Tabelas Agregadas**

Tabelas agregadas são criadas com base em diferentes **granularidades** de tempo. A plataforma pode gerar tabelas secundárias automaticamente que resumem os dados em vários intervalos:

-   A cada 60 segundos (detalhe de 1 minuto)
-   A cada 5 minutos (granularidade média)
-   A cada 1 hora
-   A cada 24 horas (tendência diária)

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-example.png" align="center"></figure>

<br />

Usando a tabela `snmp_interface_records_info` como exemplo, o sistema anexa a granularidade em segundos ao nome da tabela (ex., `_agg_if_300` para 5 minutos, `_agg_if_3600` para 1 hora). O Viewtisight consultará automaticamente a tabela mais apropriada dependendo do intervalo de tempo selecionado no dashboard.

<br />

---

## **Habilitando Tabelas Agregadas**

Você pode habilitar ou desabilitar seletivamente a criação de tabelas agregadas para cada granularidade específica usando as caixas de seleção **Enabled** (Habilitado) nas Configurações de Modelo (Model Settings).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-enabled.png" align="center"></figure>

<br />

> [!WARNING] **Considere a Frequência de Polling**
> É crucial considerar a frequência de coleta de dados antes de habilitar uma tabela agregada.
> - **Granularidade Mínima:** Se a etapa Extract coleta dados via SNMP a cada **5 minutos**, essa representa sua granularidade mínima possível. Não faz sentido habilitar a tabela de agregação de 1 minuto porque nenhum dado novo chega a essa velocidade.
> - **Agregação Inútil:** Para dados como Interfaces SNMP, mesmo que os dados sejam coletados a cada minuto, geralmente há apenas um registro por interface por minuto. Agregar um registro numa tabela de 1 minuto não fornece nenhum benefício de compactação ou desempenho, portanto, a agregação de 1 minuto deve ser desativada.

<br />

---

## **Políticas de Retenção por Granularidade**

Por fim, uma das maiores vantagens das tabelas agregadas é que elas permitem manter dados históricos de longo prazo sem consumir quantidades massivas de espaço em disco. 

Usando os menus suspensos de **Retention Period** (Período de Retenção), você pode definir exatamente por quanto tempo os dados devem ser mantidos no disco rígido para cada granularidade específica.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-retention.png" align="center"></figure>

<br />

Uma estratégia de configuração comum é:
-   **1 Minuto:** Mantido apenas por alguns dias (se habilitado).
-   **5 Minutos:** Mantido por vários meses.
-   **1 Hora / 1 Dia:** Mantido por anos, permitindo a análise de tendências históricas de longo prazo e planejamento de capacidade com o mínimo impacto de armazenamento.

<br />

---

## **Configuração Passo a Passo**

Para definir manualmente a estrutura de uma tabela agregada, siga estes passos:

**Passo 1:** Role para baixo até a seção **Aggregated Tables** (Tabelas Agregadas) e clique no botão **ADD AGGREGATED TABLE** (Adicionar Tabela Agregada).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-add-button.png" align="center"></figure>

<br />

**Passo 2:** Um novo bloco de configuração aparecerá. Você pode alterar o nome padrão **Aggregated table name** (Nome da tabela agregada), se necessário.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-name.png" align="center"></figure>

<br />

**Passo 3:** O sistema fornece um campo vazio padrão. Clicar no menu suspenso exibirá todas as Dimensões e Métricas disponíveis a partir da tabela principal. 

> [!IMPORTANT] **Ordem de Configuração**
> Você deve configurar as **Dimensões (Dimensions) primeiro**, seguidas pelas **Métricas (Metrics)**. 

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-field.png" align="center"></figure>

<br />
<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-list.png" align="center"></figure>

<br />

**Passo 4:** Para adicionar dimensões ou métricas adicionais à sua tabela agregada, basta clicar no botão **ADD NEW FIELD** (Adicionar Novo Campo) na parte inferior do bloco da tabela. 

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-new-field.png" align="center"></figure>

<br />

**Passo 5:** Continue adicionando todas as **Dimensões** desejadas primeiro.

> [!TIP] **Campo de Locatário (Tenant) Primeiro**
> É altamente recomendável colocar o campo que identifica o **tenant** (ex., `tenant`, `customer_id`) como a primeiríssima dimensão na lista. Isso otimiza o desempenho das consultas em ambientes multi-inquilino.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-dimensions.png" align="center"></figure>

<br />

**Passo 6:** Uma vez definidas todas as dimensões, você pode começar a adicionar as suas **Métricas**. Para cada métrica que adicionar, você deve selecionar a respectiva **Aggregation Function** (Função de Agregação, ex., `sum`, `avg`, `max`, `count`) necessária que será usada para comprimir os pontos de dados num único valor resumido.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-metric-select.png" align="center"></figure>

<br />
<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-metrics.png" align="center"></figure>

<br />
<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/schema-agg-function.png" align="center"></figure>

<br />
