---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'GUI Overview'
id: FJO-8GB2-32F-P4J
slug: gui-overview
isVisible: true
lastUpdated: '2025-10-15 15:13:30'
---
# **<span align="center">Visual Smart Data Broker na Interface Gráfica (GUI)</span>**

<br />

## **Localização na Interface**

<span align="justify">O Visual Smart Data Broker (VSDB) é acessível através da interface do Viewtimanager.<br>No painel de navegação esquerdo, o módulo aparece como V.S. Data Broker, agrupado com outros componentes centrais da plataforma. Ao selecionar esta opção, o painel central exibe o espaço de trabalho onde todas as operações do VSDB são gerenciadas.</span>

<br />

## **Componentes Principais da GUI**

A interface do VSDB está dividida em várias áreas funcionais:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/ZnBZQMLaCiS4PU2Kgxc5.png" align="center"></figure>

<br />

-   **Painel de Categorias (esquerda)**<br />
    Permite filtrar os plugins por categoria (ex., Network, Windows, SNMP). Isso ajuda os administradores a localizar rapidamente o tipo de integração ou conjunto de dados que desejam gerenciar.
    
    <br />
    
-   **Barra de Pesquisa (topo)**<br />
    Fornece um filtro poderoso para buscar plugins por nome, IP, OID, decorator, model, dashboard, report ou até mesmo usando expressões regulares.
    
    <br />
    
-   **Painel Central (espaço de trabalho principal)**<br />
    Exibe a lista de **plugins** disponíveis. Cada plugin aparece como um cartão (card) mostrando:
    
    -   Seu nome e versão.
    -   As pipelines incluídas.
    -   Alarmes em tempo real associados às pipelines.
    -   Dashboards que estão vinculados ao plugin.
    -   Status de instalação e datas.
        
        <br />
        
-   **Botões de Ação (inferior esquerdo)**
    
    -   **Create New Plugin** (Criar Novo Plugin): Inicia o assistente para definir um novo contêiner de plugin.
    -   **Import Plugin** (Importar Plugin): Permite importar um plugin exportado anteriormente ou fornecido pela Viewtinet.
        
        <br />
        

## **O Papel dos Plugins**

O **plugin** é o **elemento contêiner obrigatório** dentro do Visual Smart Data Broker.

-   Um plugin atua como um agrupamento lógico de pipelines.
-   Cada **pipeline** define uma sequência de operações de ETL (Extract, Transform, Load - Extrair, Transformar, Carregar).
-   **Não é possível criar ou usar uma pipeline sem associá-la a um plugin**. Isso garante que toda a lógica de ETL seja devidamente organizada, gerenciada e vinculada a dashboards, alarmes e relatórios.

Em outras palavras, o **plugin é o ponto de entrada e unidade organizacional** para todas as atividades de ETL no VSDB. Embora as pipelines sejam as que executam os fluxos de dados, o plugin fornece a estrutura onde elas são definidas, documentadas e conectadas ao restante da plataforma.

---

<br />