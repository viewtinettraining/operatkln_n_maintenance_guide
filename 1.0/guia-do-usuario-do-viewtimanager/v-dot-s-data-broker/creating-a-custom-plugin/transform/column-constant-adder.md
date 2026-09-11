---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Adicionador de Constante de Coluna'
id: 3AE-OBTK-EV6-YSP
slug: column-constant-adder
isVisible: true
lastUpdated: '2026-05-20 15:30:00'
---
# **<span align="center">Column Constant Adder</span>**

<br />

O handler de grid **Column Constant Adder** é um componente de transformação que permite aplicar um valor estático e constante a todos os campos de uma coluna especificada na **Grid** durante o pipeline ETL (Extração, Transformação, Carga).

Esta operação é altamente útil para preencher valores padrão, definir constantes padrão ou anexar rótulos estáticos em colunas inteiras do seu conjunto de dados.

<br />

---

### **Configuração & Exemplos**

A configuração do **Column Constant Adder** requer a especificação de dois campos principais:

- **Column**: Digite ou selecione o nome da coluna em que você deseja operar.
- **Constant**: Especifique o valor estático que será adicionado à coluna.

Este handler suporta tanto valores numéricos quanto texto em string, aplicando as alterações enquanto mantém o nome original da coluna.

<br />

#### **Exemplo 1: Adicionando uma Constante Numérica**
Ao operar em colunas numéricas, você pode adicionar um número fixo a todas as linhas (por exemplo, adicionando `2500` à coluna `bytes_out`):

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/column-constant-adder-1.png" align="center"></figure>

<br />

#### **Exemplo 2: Adicionando uma Constante de String**
Este handler também pode ser usado para anexar texto a uma coluna de string ou baseada em texto (por exemplo, definindo o valor `"MyVendor"` para todas as linhas na coluna `vendor`):

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/column-constant-adder-2.png" align="center"></figure>

<br />

<div class="sd-callout" data-callout-type="tip"><strong>Melhor Prática:</strong> Use o Column Constant Adder quando precisar definir metadados padrão (como nome do fornecedor, códigos de status estáticos ou números de limite base) em todas as linhas antes de carregar o conjunto de dados final no banco de dados.</div>

<br />