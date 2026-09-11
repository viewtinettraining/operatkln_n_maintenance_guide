---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Sobre'
id: AE9-UUBF-A0O-RX1
slug: about
isVisible: true
lastUpdated: '2025-08-28 08:15:30'
---
# **<span align="center">Criando um Plugin Personalizado</span>**

<br />

<span align="justify">Nesta subseção, explicaremos como criar um plugin personalizado a partir do zero. O processo o guiará na definição de cada componente do plugin, enquanto explora todas as etapas do ciclo ETL: Extrair, Transformar e Carregar. Ao final desta seção, você entenderá como configurar conectores, desenhar fluxos de trabalho de transformação usando grid handlers e decidir como e onde os dados processados serão carregados, garantindo que o plugin atenda totalmente aos requisitos do seu ambiente.</span>

<br />

**Esboço do Processo de Criação**

<br />

1.  **Definir o Contêiner do Plugin**
    
    -   Atribuir um nome, descrição e categoria.
    -   Estabelecer o plugin como o contêiner obrigatório para uma ou mais pipelines.
2.  **Configurar a Etapa de Extração (Extract)**
    
    -   Selecionar e configurar os conectores de protocolo (ex., SNMP, ICMP, Syslog, NetFlow, APIs).
    -   Associar conectores com as fontes de dados a serem integradas.
3.  **Desenhar a Etapa de Transformação (Transform)**
    
    -   Adicionar grid handlers para interpretar (parse), normalizar e enriquecer os dados recebidos.
    -   Aplicar operações matemáticas ou regras de mapeamento de dados conforme necessário.
4.  **Configurar a Etapa de Carregamento (Load)**
    
    -   Decidir onde os dados processados serão armazenados ou exportados.
    -   As opções incluem o Viewtinet TSDB (padrão), syslog, SCP ou CSV.
5.  **Integrar Dashboards e Relatórios**
    
    -   Vincular o plugin a dashboards existentes, ou criar novas visualizações.
    -   Garantir que as saídas do pipeline ETL estejam disponíveis para monitoramento e análise.
6.  **Salvar e Validar o Plugin**
    
    -   Implantar (Deploy) o plugin dentro do Visual Smart Data Broker.
    -   Verificar se as fontes de dados estão sendo processadas corretamente através das pipelines definidas.

<br />