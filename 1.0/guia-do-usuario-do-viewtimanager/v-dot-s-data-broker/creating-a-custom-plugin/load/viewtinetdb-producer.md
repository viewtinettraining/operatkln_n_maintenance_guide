---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Produtor ViewtinetDB'
id: YUQ-YMR-XKJ-1H8
slug: viewtinetdb-producer
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 11:37:18'
---
# **<span align="center">Produtor ViewtinetDB (ViewtinetDB Producer)</span>**

<br />

O **ViewtinetDB Producer** é o manipulador principal usado para carregar a grade final obtida durante a etapa Extract e processada na etapa Transform diretamente no banco de dados local da Viewtinet.

Este é o destino mais comum quando se deseja ingerir dados processados para armazenamento de longo prazo, permitindo que você posteriormente consulte, visualize e construa dashboards na Console do Viewtinet.

---

## **Parâmetros de Configuração**

Ao selecionar `ViewtinetDB Producer` no menu suspenso, o sistema preenche automaticamente a maioria das variáveis necessárias para você, conectando-se diretamente à engine de banco de dados interna.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtinetdb-producer-step1.png" align="center"></figure>

<br />

### **Variáveis de Conexão (Configuradas Automaticamente)**

-   **Engine** (Motor): Definido como `postgres` por padrão.
-   **Host**: Resolve automaticamente usando a macro `${DEFAULT_CONNECTOR_HOST}`.
-   **Port** (Porta): Porta padrão do banco de dados (`5433`).
-   **Database** (Banco de Dados): O nome do banco de dados central (`viewtinet`).
-   **User / Password** (Usuário / Senha): Pré-configurados com as credenciais internas do sistema para estabelecer uma conexão local segura.

### **Variáveis de Ingestão**

-   **Table** (Tabela): Este é um campo crucial. Por padrão, o nome da tabela de destino é obtido automaticamente a partir do **Pipeline Name** (Nome do Pipeline) configurado na etapa de Extract. No entanto, se desejar, você pode substituir diretamente este campo para especificar um nome de tabela personalizado diferente.
-   **Save Mode** (Modo de Salvar): Determina o comportamento ao gravar dados na tabela de destino. A configuração mais comum é **Append If Exists** (Anexar se Existir), que anexa de forma segura novas linhas se a tabela já estiver presente, ou cria uma nova tabela com as colunas da grade se ela ainda não existir.
-   **Insert Mode** (Modo de Inserção): Define como os dados são injetados no Postgres. Geralmente definido como `copy` para carregamento em massa de alto desempenho.
-   **Batch Size / Null Repr** (Tamanho do Lote / Representação Nula): Usados para o ajuste fino avançado dos pedaços de ingestão de dados e das representações de strings nulas.

<br />

### **Definição Manual de Colunas (Opcional)**

Na parte inferior do produtor, você encontrará um botão **\+ ADD NEW COLUMN** (Adicionar Nova Coluna). Geralmente, o Produtor herda e cria automaticamente as colunas do banco de dados com base na grade gerada pelos handlers de Transformação (Transform). No entanto, você pode definir as colunas e os seus tipos de dados SQL explicitamente aqui, caso precise de um controle manual e estrito sobre a criação do esquema do banco de dados.