---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Date Converter'
id: VKX-UXK-YCI-T8O
slug: date-converter
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 09:03:41'
---
---

# **<span align="center">Date Converter</span>**

<br />

O handler de grid **Date Converter** é um componente crítico usado para analisar, transformar e formatar timestamps durante o processo ETL.

---

## **Contexto: Banco de Dados de Séries Temporais**

O banco de dados Viewtinet é um banco de dados de séries temporais onde o **campo de timestamp obrigatório** é `created_at`. Este campo deve ser sempre fornecido em um **formato epoch de 16 dígitos** (microssegundos).

Por padrão, o sistema lida com o campo `created_at` automaticamente dependendo da fonte de dados:

-   **Protocolos de Polling (por exemplo, ICMP, SNMP):** O processo `viewtilog` preenche automaticamente o campo `created_at` com base no momento exato em que a resposta é recebida do dispositivo consultado.
-   **Protocolos de Escuta (por exemplo, Syslog, NetFlow):** O processo `viewtilog` atribui automaticamente o valor `created_at` com base no momento exato em que o evento é recebido pelo servidor.

### **Por que usar o Date Converter?**

Embora o timestamp automático seja útil, ele representa o momento em que o evento foi _recebido_ pelo Viewtinet, não necessariamente o momento em que o evento _realmente ocorreu_ no dispositivo de origem.

Se a sua carga de dados de entrada já contém um timestamp específico (por exemplo, o horário de uma transação, um horário de início ou o horário de geração de um log), você pode usar o **Date Converter** para extrair esse timestamp da carga e substituir o campo `created_at` para que o evento seja posicionado com precisão no banco de dados de séries temporais.

<br />

---

## **Etapas de Configuração**

A configuração do handler de grid **Date Converter** envolve as seguintes etapas sequenciais:

1.  **Selecionar o Grid-Handler**: Clique no botão "ADD NEW GRID-HANDLER" e selecione **Date Converter** no menu suspenso `Grid Handler Type`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step1a.png" align="center"></figure>

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step1b.png" align="center"></figure>

<br />

2.  **Selecionar a Date Column**: No campo `Date Column`, selecione a coluna a partir da qual você deseja converter o timestamp.
3.  **Definir a New Column**: No campo `New Column`, insira o nome da coluna no banco de dados que armazenará a data convertida. Se você quiser substituir o timestamp inserido pelo Viewtinet, você deve escrever `created_at`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step3.png" align="center"></figure>

<br />

4.  **Definir Date Column Format**: No campo `Date Column Format`, insira o formato exato do timestamp conforme ele vem do ETL.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step4.png" align="center"></figure>

<br />

5.  **Definir New Date Column Format**: No campo `New Date Column Format`, insira o formato desejado para a data convertida. Se você selecionou `created_at` no passo 3, você deve inserir o símbolo `%s` (que é o tempo epoch de 10 dígitos) e concatenar `000000`, deixando como `%s000000`. Em qualquer outro caso, use o formato que deseja exibir.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-step5.png" align="center"></figure>

<br />

---

## **Referência de Configuração e Formatação**

O Date Converter permite extrair um timestamp de uma coluna de origem, analisá-lo usando formatos padrão e enviá-lo para uma nova coluna com um formato diferente.

Para ambos os casos, **Date Column Format** (analisando a entrada) e **New Date Column Format** (escrevendo a saída), você pode usar os filtros de formatação padrão do comando `date` do **Linux** (por exemplo, `%Y`, `%m`, `%d`, `%H`, `%M`, `%S`).

<div class="sd-callout" data-callout-type="info"><strong>Requisito de Epoch de 16 Dígitos:</strong> O curinga <code>%s</code> representa um timestamp epoch padrão de 10 dígitos (segundos). Uma vez que o banco de dados Viewtinet requer um epoch de 16 dígitos para o campo <code>created_at</code>, é extremamente comum anexar seis zeros ao formato de saída assim: <code>%s000000</code>.</div>

<br />

---

## **Exemplos Práticos**

### **Exemplo 1: Convertendo uma Data Padrão para** `created_at`

Neste cenário, uma coluna chamada `sale_date` contém uma data em um formato padrão (por exemplo, `YYYY-MM-DD`). Queremos analisá-la e convertê-la para o formato obrigatório de epoch de 16 dígitos para substituir o timestamp do evento.

-   **Date Column:** `sale_date`
-   **New Column:** `created_at`
-   **Date Column Format:** `%Y-%m-%d` (ou `%D` dependendo da entrada)
-   **New Date Column Format:** `%s000000`

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-example1-v2.png" align="center"></figure>

<br />

### **Exemplo 2: Tempo de Atividade do Sistema Legível (Uptime)**

O Date Converter também suporta formatos de análise especiais como `timeticks-centiseconds`, que é comumente usado para analisar o valor de `system-uptime` fornecido por dispositivos SNMP. Isso permite converter os ticks de tempo de atividade do dispositivo em um timestamp padrão legível ou outro formato exigido.

-   **Date Column:** `system-uptime`
-   **New Column:** `system_uptime_human`
-   **Date Column Format:** `timeticks-centiseconds`
-   **New Date Column Format:** `*` (O asterisco representa um mapeamento de formato padrão legível para humanos)

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-example2-v2.png" align="center"></figure>

<br />

### **Exemplo 3: Analisando uma String de Timestamp Complexa**

Neste exemplo, a carga de dados fornece um timestamp muito específico na coluna `Start Initiation Time` (formato como `20231025143000.123`). Analisamos esse timestamp preciso, incluindo frações de segundos (`%f`), e o convertemos para o epoch de 16 dígitos.

-   **Date Column:** `Start Initiation Time`
-   **New Column:** `timestamp`
-   **Date Column Format:** `%Y%m%d%H%M%S.%f`
-   **New Date Column Format:** `%s000000`

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/date-converter-example3-v2.png" align="center"></figure>

<br />