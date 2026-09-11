---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grid Filter'
id: GL2-GM1-6UV-GSJ
slug: grid-filter
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 12:00:00'
---
# **<span align="center">Grid Filter</span>**

<br />

O handler **Grid Filter** é uma ferramenta poderosa projetada para manter ou descartar seletivamente registros recebidos (linhas) com base em condições lógicas específicas antes que sejam enviados ao banco de dados.

Ao configurar os filtros de dimensão (dimension filters), você pode garantir que apenas dados válidos, relevantes ou em conformidade sejam ingeridos. Qualquer linha que não atenda aos critérios especificados é completamente descartada da carga durante a fase de transformação.

---

## **Quando usá-lo?**

Você deve usar este handler para:
- **Descartar anomalias**: Por exemplo, filtrar logs onde uma métrica percentual como uso de CPU ou Armazenamento relata um valor maior que 100%.
- **Reduzir o ruído**: Descartar níveis de log irrelevantes (por exemplo, manter apenas logs de severidade `ERROR` ou `CRITICAL` e descartar `INFO` ou `DEBUG`).
- **Ingestão direcionada**: Ingerir apenas eventos que pertencem a um tenant específico ou sub-rede de IP.

<br />

## **Parâmetros de Configuração**

A configuração é dividida em duas partes: a operação lógica global e as condições individuais.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-filter-step1.png" align="center"></figure>

<br />

### **1. Operação Global**
- **Operation**: Determina como o sistema deve avaliar múltiplas condições se você definir mais de uma. 
  - `AND (match all)`: A linha é mantida *apenas* se satisfizer **todas** as condições simultaneamente.
  - `OR (match any)`: A linha é mantida se satisfizer **pelo menos uma** das condições.

### **2. Condições (Filtros de Dimensão)**
Você pode definir uma ou mais regras clicando no botão **+ ADD NEW DIMENSION FILTER**. Para cada regra, você deve configurar:

- **Column**: O nome da coluna que você deseja avaliar (por exemplo, `storage_utilization`).
- **Filter Type**: Determina como o valor será processado e comparado. Por exemplo, `int-compare` trata o valor como um número inteiro para comparação matemática.
- **Case Sensitive**: Determina se as comparações de string devem distinguir entre letras maiúsculas e minúsculas.
- **Match Mode**: Define os comportamentos de correspondência de string (como correspondência exata, começa com, etc.).
- **Compare Operation**: O operador lógico ou matemático usado para a avaliação (por exemplo, `<=`, `>=`, `==`, `!=`).
- **Value**: O limite, string ou número para comparar com o conteúdo da coluna (por exemplo, `100`).
- **Invert Filter**: Se definido como `true`, nega logicamente a regra (por exemplo, transformando um `<=` em um `>`). Por padrão, deve ser `false`.

Na imagem de exemplo fornecida acima, o handler está configurado para manter **apenas** as linhas onde o `storage_utilization` é menor ou igual a `100` (`<= 100`). Qualquer linha reportando um valor de `101` ou maior será automaticamente descartada.