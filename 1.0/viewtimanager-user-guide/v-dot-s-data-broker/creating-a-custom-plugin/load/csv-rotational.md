---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Rotational CSV Writer'
id: 97X-FXC-MZ1-UAZ
slug: csv-rotational
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 13:43:08'
---
# **<span align="center">Gravador de CSV Rotativo (Rotational CSV Writer)</span>**

<br />

O produtor **Rotational CSV Writer** funciona de maneira semelhante ao CSV Writer padrão, despejando os dados da grade transformada no Sistema Operacional local como um arquivo simples (flat file).

No entanto, a sua principal diferença reside no seu **mecanismo de rotação**: em vez de anexar indefinidamente a um único arquivo, ele grava dados continuamente até que um **tempo de rotação** especificado seja atingido. Uma vez que o limite de tempo é alcançado, ele fecha o arquivo atual e cria um novo. Isso é extremamente útil para lidar com fluxos de dados contínuos de alto volume e dividi-los em pedaços baseados no tempo que sejam gerenciáveis.

---

## **Parâmetros de Configuração**

Ao selecionar `Rotational CSV Writer`, o produtor preenche automaticamente as variáveis baseando-se no nome do plugin. Todos os campos continuam totalmente personalizáveis.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-rotational-step2.png" align="center"></figure>

<br />

-   **Output Path** (Caminho de Saída): O diretório onde os arquivos rotacionados serão armazenados. Por padrão, ele usa a macro `%%%PLUGIN_NAME%%%` para criar uma pasta isolada.
    
    -   _Lembrete:_ Assim como com o gravador CSV padrão, este caminho **deve** residir sob o diretório raiz `/opt/vn/dhyana/var/data/` para evitar problemas de permissão do SO.
-   **Rotation Period** (Período de Rotação): O intervalo de tempo exato após o qual o arquivo será rotacionado.
-   **CSV Prefix** (Prefixo CSV): A string base usada para o nome do arquivo antes de anexar os carimbos de data/hora (timestamps) da rotação.

> \[!WARNING\] **Unidade em Microssegundos para o Período de Rotação**<br />
> É extremamente importante observar que a unidade para o **Rotation Period** é **microssegundos (µs)**. Por padrão, a interface do usuário preenche com `60`, o que equivale a apenas 60 microssegundos. Você **deve** modificar esse valor para corresponder ao prazo desejado em microssegundos. Por exemplo, se quiser que o arquivo seja rotacionado a cada 60 segundos (1 minuto), você deve inserir `60000000`.

<br />

Aqui está um exemplo de uma configuração personalizada apontando para uma pasta syslog específica e rotacionando o arquivo a cada 1 minuto (60.000.000 microssegundos):

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-rotational-step1.png" align="center"></figure>

<br />