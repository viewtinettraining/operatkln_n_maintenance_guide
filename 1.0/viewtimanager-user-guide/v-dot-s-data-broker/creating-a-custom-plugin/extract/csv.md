---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'CSV'
id: 7Z6-GTTH-7QR-S4A
slug: csv
isVisible: true
lastUpdated: '2025-10-15 15:25:17'
---
# **<span align="center">Conector CSV</span>**

<br />

O **Conector CSV** é usado para ingerir registros de arquivos CSV. Embora o nome sugira um formato CSV estrito, o **separador de campos é configurável**, permitindo flexibilidade para se adaptar a diferentes estruturas de arquivos. Este conector é amplamente utilizado para integrações com **sistemas VoIP**, particularmente para a ingestão de **CDRs (Call Detail Records)**, **CMRs (Call Management Records)**, ou qualquer outra fonte de dados que gere logs no formato CSV.

O conector lê os arquivos diretamente de um **diretório local no servidor Viewtilog**, o que significa que deve haver um **processo externo ou agendado** responsável por depositar arquivos CSV no caminho da coleção especificado. Uma vez coletados, os arquivos são processados e depois movidos para um diretório dedicado para garantir rastreabilidade e evitar reprocessamento.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/UFK4rNp2GJqY0IXnwiqC.png" align="center"></figure>

<br />

## **Parâmetros de Configuração**

-   **Tipo de Frequência**<br />
    Mesmo comportamento que nos conectores SNMP e ICMP:
    
    -   **Periódico**: Executa o pipeline em intervalos fixos (definidos em _Tempo de Atualização_).
    -   **Agendado**: Usa uma expressão cron para controlar a execução em horários precisos.
-   **Número de Threads**<br />
    Define quantas threads simultâneas processarão arquivos. Isso é útil para lidar com altos volumes de dados em paralelo.
-   **Nome do Pipeline**<br />
    Um identificador único para o pipeline.
-   **Tempo de Atualização (segs)**<br />
    O intervalo em segundos entre cada execução quando _Periódico_ for selecionado.
-   **Número de Execuções**
    
    -   `-1`: Execução contínua sem limite.
    -   Inteiro positivo: Limita o número de execuções ao valor especificado.
-   **Caminho Coletado**<br />
    Diretório onde os novos arquivos CSV devem ser colocados. Arquivos neste local serão lidos pelo conector.
-   **Caminho de Processamento**<br />
    Diretório temporário para onde os arquivos são movidos durante o processamento.
-   **Caminho Processado**<br />
    Diretório onde os arquivos são armazenados após a conclusão do processamento.
-   **Separador**<br />
    Caractere usado para delimitar os campos (ex.: `,`, `;`, `|`).
-   **Sufixo**<br />
    Extensão dos arquivos a serem processados (ex.: `.csv`).
-   **Máx de Arquivos**<br />
    Número máximo de arquivos a serem processados por ciclo.
-   **Manter Vírgulas**<br />
    Opção que preserva vírgulas dentro dos campos em vez de dividi-las como separadores.
-   **Possui Aspas**<br />
    Se ativado, campos entre aspas (`"`) são tratados como um campo único, mesmo se contiverem o caractere separador.
-   **Tamanho do Bloco**<br />
    Define se o arquivo CSV será lido em blocos (útil para arquivos muito grandes).

<br />

## **Definição de Campos**

Para analisar o arquivo corretamente, **os campos devem ser definidos**. Isso pode ser feito de duas formas:

1.  **Definição manual**: Use o botão **Adicionar Novo Campo** para criar campos um por um, atribuindo-lhes um nome e um tipo.
2.  **Importar do CSV**: Envie um arquivo CSV de amostra contendo apenas a **linha de cabeçalho** (nomes dos campos). O sistema criará automaticamente os campos correspondentes na configuração do conector.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/nzTHsGYKZ2nYSO0pNxfl.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/YS2R089DrTbHW5BXYHiP.png" align="center"></figure>

<br />

**Opções adicionais incluem:**

-   **Nome do Campo**: Nome da coluna a ser analisada.
-   **Tipo de Campo**: Tipo de dado para o campo (string, integer, float, etc.), que pode ser aplicado individualmente ou para todos os campos de uma vez.
-   **Deletar Todos os Campos**: Redefine a configuração, se necessário.

<br />

## **Resumo**

O Conector CSV fornece uma maneira flexível e eficiente de ingerir dados estruturados armazenados em arquivos:

-   Suporta execução **Periódica** e **Agendada**.
-   Requer um processo para depositar os arquivos CSV no diretório de coleta.
-   Pode lidar com separadores de campo e campos entre aspas para estruturas de dados complexas.
-   Os campos podem ser configurados manualmente ou importados diretamente do cabeçalho de um CSV.

Este conector é ideal para ambientes em que sistemas externos exportam logs ou registros de transações no formato CSV e que precisam ser integrados à plataforma Viewtinet para análises posteriores.