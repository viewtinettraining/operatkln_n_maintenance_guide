---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Operação Matemática'
id: Y8I-WJZ-GMD-5X6
slug: math-operation
isVisible: true
isSearchable: true
lastUpdated: '2026-05-21 12:00:00'
---
# **<span align="center">Math Operation</span>**

<br />

O handler de grid **Math Operation** permite que você realize operações matemáticas usando campos numéricos selecionados do seu fluxo de dados. O resultado calculado da operação é então armazenado em um campo completamente novo adicionado à grid.

Isso é particularmente útil para calcular dinamicamente porcentagens, proporções, deltas ou converter unidades (como bytes para gigabytes) instantaneamente durante o processo ETL.

---

## **Etapas de Configuração**

A configuração do handler de grid **Math Operation** envolve as seguintes etapas sequenciais:

1. **Adicionar o Grid-Handler**: Clique no botão "ADD NEW GRID-HANDLER".
2. **Selecionar o Tipo de Grid Handler**: Escolha **Math Operation** no menu suspenso `Grid Handler Type`.

<br />

3. **Selecionar os Fields**: No menu suspenso `Fields`, selecione os campos numéricos que você deseja incluir em sua operação matemática.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/math-operation-step2.png" align="center"></figure>

<br />

4. **Definir a Expression**: Na caixa de entrada `Expression`, insira a fórmula matemática desejada. Você pode usar operadores matemáticos padrão, condicionais (como `if`) e referenciar os nomes exatos dos campos que você selecionou na etapa anterior.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/math-operation-step3.png" align="center"></figure>

<br />

5. **Definir o Column Name**: Na opção `Column Name`, digite o nome do novo campo onde o resultado da operação matemática será armazenado. Tenha em mente que este é um campo completamente novo que será adicionado ao esquema do banco de dados.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/math-operation-step4.png" align="center"></figure>

<br />