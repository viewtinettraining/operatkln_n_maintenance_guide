---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid handlers intro'
id: DGL-CW6-BNR-HIL
slug: grid-handlers-intro
isVisible: true
isSearchable: true
lastUpdated: '2026-05-20 17:30:00'
---
# **<span align="center">Grid Handlers</span>**

<br />

## Conceito de Grid

Durante a fase de Extração (Extraction), todas as informações obtidas são armazenadas em uma estrutura em memória chamada **Grid**. Para simplificar o processo de compreensão, pense nela como uma matriz ou tabela com linhas e colunas.

A Grid, como estrutura, é enviada ao **processo de Transformação** para realizar ações como adicionar, remover, modificar ou criar novos campos com base nos dados obtidos na etapa de Extração.

<br />

## O que são Grid Handlers?

Os **Grid Handlers** são os componentes individuais ou operações usadas dentro da Etapa de Transformação (Transform Stage) para manipular a Grid. Ao aplicar diferentes handlers, os dados obtidos na etapa anterior podem ser amplamente transformados e refinados antes de passarem para a próxima fase do pipeline.

Esses handlers são incrivelmente versáteis e são capazes de:

-   Filtrar registros com base nas informações extraídas.
-   Aplicar operações matemáticas simples e complexas (especialmente úteis para campos numéricos) para calcular novos campos.
-   Aplicar expressões regulares (regexes) para filtrar informações ou extrair campos específicos.
-   Aplicar técnicas de IA para gerar novas informações com base em dados históricos e atuais.
-   Adicionar informações de fontes externas (como arquivos CSV) para enriquecer dinamicamente dados configurados estaticamente.

<br />

---

### Como Adicionar um Novo Grid Handler

Para adicionar um novo Grid Handler à sua etapa de Transformação, siga estas etapas:

**Passo 1:** Clique no botão **"+ ADD NEW GRID HANDLER"** localizado na parte inferior do painel de configuração da etapa de Transformação.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-handler-add-button.png" align="center"></figure>

<br />

**Passo 2:** Um novo cartão **Grid Handler** aparecerá. Clique no campo suspenso **"Grid Handler Type"** para revelar a lista de todos os handlers disponíveis.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-handler-type-selector.png" align="center"></figure>

<br />

**Passo 3:** Selecione o handler desejado na lista suspensa. Os tipos de Grid Handler disponíveis são:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-handler-dropdown.png" align="center"></figure>

<br />

<div class="sd-callout" data-callout-type="info"><strong>Nota:</strong> Este procedimento se aplica a <strong>todos</strong> os Grid Handlers descritos nas seções seguintes. Cada tipo de handler tem seus próprios campos de configuração específicos que aparecerão uma vez selecionados na lista suspensa.</div>

<br />
