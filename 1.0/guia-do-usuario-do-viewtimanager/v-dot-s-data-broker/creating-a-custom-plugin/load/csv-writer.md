---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Gravador de CSV'
id: GXO-SEQ-ARK-SFV
slug: csv-writer
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 13:24:47'
---
# **<span align="center">Gravador de CSV (CSV Writer)</span>**

<br />

O produtor **CSV Writer** é usado para despejar a grade final transformada diretamente em um local de arquivo específico dentro do Sistema Operacional. Ele formata a saída em um arquivo de valores separados por vírgulas (CSV), tornando-o ideal para criar backups de arquivos simples, exportar logs para ferramentas de análise de terceiros, ou gerar relatórios periódicos estáticos.

---

## **Parâmetros de Configuração**

Ao selecionar `CSV Writer` no menu suspenso de produtores, o sistema irá pré-configurar automaticamente as variáveis necessárias usando o nome do plugin. No entanto, todos esses campos são totalmente personalizáveis.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-writer-step2.png" align="center"></figure>

<br />

-   **CSV Filename** (Nome do arquivo CSV): O nome do arquivo resultante. Por padrão, ele pega a macro `%%%PLUGIN_NAME%%%`, mas você pode especificar o nome do arquivo explicitamente (ex., `icmp`).
-   **CSV Destination Path** (Caminho de Destino do CSV): O diretório onde o arquivo será salvo. Por padrão, ele configura automaticamente uma subpasta baseada no nome do plugin.
-   **CSV Separator** (Separador CSV): O caractere usado para delimitar as colunas no arquivo de saída. O padrão é uma vírgula (`,`).
-   **Use Timestamp in filenames** (Usar Timestamp nos nomes dos arquivos): Uma caixa de seleção (checkbox) que, quando habilitada, anexa automaticamente o carimbo de data/hora (timestamp) da execução atual ao nome do arquivo. Isso é altamente recomendado para evitar que arquivos sejam sobrescritos em execuções subsequentes.

> \[!WARNING\] **Importante: Restrição de Caminho**<br />
> O diretório raiz para a gravação desses arquivos **deve** ser `/opt/vn/dhyana/var/data/`. Se você tentar configurar um caminho de destino fora deste diretório raiz, o processo pode falhar em gravar os arquivos devido a restrições estritas de permissão do Sistema Operacional.

<br />

Aqui está um exemplo de uma configuração personalizada apontando para uma subpasta `icmp/collected` específica:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-writer-step1.png" align="center"></figure>

<br />