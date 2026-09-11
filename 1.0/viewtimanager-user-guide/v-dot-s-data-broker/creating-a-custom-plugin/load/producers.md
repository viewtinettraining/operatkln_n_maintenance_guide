---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Produtores (Producers)'
id: DWK-9MRZ-IG3-0YN
slug: producers
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 11:33:02'
---
# **<span align="center">Produtores (Producers)</span>**

<br />

Uma vez que os dados tenham passado pelas etapas de **Extração (Extract)** e **Transformação (Transform)** do ciclo ETL, a **etapa de Carregamento (Load)** define onde os registros processados serão armazenados ou exportados.<br />
Na Viewtinet, esses destinos são gerenciados por meio de componentes chamados **Produtores (Producers)**.

Um **Produtor** é responsável por entregar os dados transformados a uma saída específica, seja ela um armazenamento local, um banco de dados, um arquivo ou um sistema externo. Ao configurar um Produtor, os administradores decidem o destino final dos dados e como eles serão disponibilizados para dashboards, relatórios ou integrações externas.

Os Produtores disponíveis incluem:

-   **Aggregator** (Agregador)
-   **CSV Writer** (Gravador de CSV)
-   **Rotational CSV Writer** (Gravador de CSV Rotativo)
-   **Syslog Producer** (Produtor de Syslog)
-   **SCP Producer** (Produtor via SCP)
-   **ViewtinetDB Producer** (Produtor do ViewtinetDB)
-   **Kafka Producer** (Produtor de Kafka)

Cada um desses Produtores oferece diferentes opções para armazenar ou exportar dados, dependendo dos requisitos operacionais e de integração.

---

## **Como Adicionar um Novo Produtor**

Independentemente do tipo de destino, o passo inicial para configurar **qualquer** um dos produtores disponíveis é sempre o mesmo.

1.  Navegue até a etapa **Load** (Carregar) na configuração do seu plugin no V.S. Data Broker.
2.  Clique no botão **\+ ADD NEW PRODUCER** (Adicionar Novo Produtor).

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/add-producer-step1.png" align="center"></figure>

<br />

3.  Uma nova caixa de Produtor vazia aparecerá, indicando que selecionar um Tipo de Produtor (Producer Type) é um campo obrigatório.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/add-producer-step2.png" align="center"></figure>

<br />

4.  Abra o menu suspenso **Producer Type** (Tipo de Produtor) e selecione o produtor específico que deseja configurar.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/add-producer-step3.png" align="center"></figure>

<br />

> \[!NOTE\] Os parâmetros de configuração específicos, casos de uso e exemplos de integração para cada tipo de produtor individual são explicados em detalhes nas seções a seguir.

<br />