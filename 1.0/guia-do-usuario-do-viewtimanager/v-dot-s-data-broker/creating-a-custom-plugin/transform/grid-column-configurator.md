---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Configurador de Coluna de Grade'
id: O3Y-V9O-SQJ-APX
slug: grid-column-configurator
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 11:17:41'
---
# **<span align="center">Grid Column Configurator</span>**

<br />

O handler **Grid Column Configurator** foi projetado para permitir que você defina a ordem estrita e a presença das colunas dentro da sua grid de dados.

Ao especificar explicitamente os campos de saída, você garante que a carga mantenha um esquema consistente e padronizado antes de ser inserida no banco de dados. Isso é especialmente útil para organizar grandes conjuntos de dados ou normalizar estruturas de diferentes fontes de log.

---

## **Parâmetros de Configuração**

Para usar este handler, selecione `Grid Column Configurator` no menu suspenso. A interface exibirá uma string de visualização somente leitura dos seus **Output fields** atuais.

Para definir ou modificar a ordem exata das colunas, clique no ícone de lápis **Edit Output Fields** () localizado no lado direito do handler.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-column-configurator-step1.png" align="center"></figure>

<br />

### **Editando o Esquema**

Clicar no ícone de lápis abre a janela modal **Editing Output Fields**.

Nesta janela, você pode gerenciar livremente suas colunas:

-   **Adicionando Campos**: Digite o nome exato da coluna que deseja incluir e separe-a usando uma vírgula (`,`) ou um ponto e vírgula (`;`). O sistema a converterá automaticamente em uma tag interativa.
-   **Removendo Campos**: Clique no ícone `X` ao lado de qualquer tag para removê-la completamente da saída da grid.
-   **Ordenando Campos**: A ordem em que as tags aparecem aqui determina a sequência estrita da esquerda para a direita das colunas na estrutura final da grid.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-column-configurator-step2.png" align="center"></figure>

<br />

> \[!TIP\] Use este handler como uma das últimas etapas no seu pipeline de transformação para garantir que sua estrutura final da carga esteja limpa e formatada corretamente para ingestão.

<br />