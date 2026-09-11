---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Codificador UTF-8 de Grade'
id: H4M-8GO-4NZ-VGW
slug: grid-utf8-encoder
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 09:21:08'
---
# **<span align="center">Grid UTF8 Encoder</span>**

<br />

O handler de grid **Grid UTF8 Encoder** foi projetado para codificar explicitamente todo o conteúdo da grid no formato UTF-8 durante a etapa de transformação.

Isso é crucial ao lidar com fontes de dados que exportam logs ou registros em codificações de caracteres legadas ou alternativas (como `iso-8859-1`), garantindo que caracteres e símbolos especiais sejam ingeridos e exibidos corretamente no banco de dados de séries temporais sem corrupção.

---

## **Parâmetros de Configuração**

Para configurar este handler de grid, você só precisa definir o formato de codificação original:

-   **Grid Handler Type**: Selecione `Grid UTF8 Encoder`.
-   **Current Encoding**: No menu suspenso, selecione o formato de codificação original que os dados de entrada estão usando atualmente (por exemplo, `iso-8859-1`). O handler o traduzirá automaticamente para o padrão `UTF-8`.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/grid-utf8-encoder-step1.png" align="center"></figure>

<br />

---

## **Melhores Práticas e Recomendações**

> \[!IMPORTANT\] **Ordem de Execução:** Se você precisar usar o Grid UTF8 Encoder, é altamente recomendável que o coloque como o **primeiríssimo** handler em sua lista de Grid Handlers.
> 
> Você pode reordenar seus handlers clicando no botão azul da seta **Move Up** (), conforme mostrado na imagem acima. Codificar a carga logo no início garante que quaisquer handlers subsequentes (como Split, Regex ou Math Operations) processem os dados com o mapeamento de caracteres UTF-8 correto, evitando erros de análise em caracteres especiais.

<br />