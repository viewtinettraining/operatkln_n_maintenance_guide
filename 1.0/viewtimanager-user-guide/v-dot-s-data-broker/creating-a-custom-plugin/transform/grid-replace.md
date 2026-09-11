---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Substituição em Grade'
id: ZDE-USR-M4L-84X
slug: grid-replace
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 09:35:11'
---
# **<span align="center">Grid Replace</span>**

<br />

O handler **Grid Replace** permite que você pesquise por caracteres, substrings ou padrões específicos dentro de uma coluna e os substitua por um novo valor. Você pode escrever o texto modificado resultante na mesma coluna (para sobrescrever os dados originais) ou em uma coluna de destino completamente nova.

Isso é extremamente útil para higienizar dados, padronizar formatos (por exemplo, mudar vírgulas para pontos em valores numéricos) ou remover caracteres indesejados de mensagens de log.

---

## **Parâmetros de Configuração**

Para configurar o handler **Grid Replace**, defina os seguintes campos:

-   **Grid Handler Type**: Selecione `Grid Replace`.
-   **Mode**: Define o comportamento específico e o escopo da operação de substituição (explicado em detalhes abaixo).
-   **Column**: A coluna de origem que contém o texto original que você deseja modificar (por exemplo, `LOC_LATITUD`).
-   **Target Column**: A coluna de destino onde a string modificada será salva. Se você selecionar o mesmo nome da coluna de origem, os dados originais serão sobrescritos.
-   **To Replace**: O caractere exato, string ou padrão de expressão regular que você deseja encontrar e substituir.
-   **Replacement**: O novo texto que tomará o lugar da string correspondente.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-replace-step1.png" align="center"></figure>

<br />

---

## **Modos de Execução**

O poder deste handler está em seus diferentes modos de execução, que permitem que você controle exatamente quais ocorrências da string serão substituídas.

Ao clicar na lista suspensa `Mode`, você verá as seguintes opções:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-replace-step2.png" align="center"></figure>

<br />

-   `all`: Substitui _cada ocorrência_ da string "To Replace" encontrada no texto. Este é o modo mais comum usado para higienização global.
-   `first`: Substitui _apenas a primeira_ ocorrência da string, deixando as correspondências subsequentes intactas.
-   `last`: Substitui _apenas a última_ ocorrência da string encontrada no final do texto.
-   `nth`: Substitui uma ocorrência específica com base em seu índice numérico (por exemplo, substituindo apenas a 3ª ocorrência de uma vírgula). A seleção deste modo normalmente solicitará o valor do índice.
-   `regex`: Trata o campo "To Replace" como uma **Expressão Regular (Regular Expression)** em vez de uma string literal. Isso permite substituições avançadas e dinâmicas baseadas em padrões complexos.

<br />