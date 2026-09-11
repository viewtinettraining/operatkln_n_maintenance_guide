---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Decorador CSV'
id: CSV-DEC0-GH1-TR4
slug: csv-decorator
isVisible: true
isSearchable: true
lastUpdated: '2026-05-20 18:40:04'
---
# **<span align="center">CSV Decorator</span>**

<br />

O handler de grid **CSV Decorator** é um componente poderoso de transformação que permite **mapear dados** ou **adicionar informações extras** à Grid usando um arquivo CSV externo como fonte de pesquisa. Isso permite a injeção de conteúdo dinâmico em um pipeline ETL configurado estaticamente.

Ele funciona realizando um **LEFT OUTER JOIN** entre os dados da Grid e o arquivo CSV: para cada linha na Grid, o handler procura registros correspondentes no arquivo CSV com base em uma coluna de referência obtida durante o processo ETL e preenche as novas colunas com os valores correspondentes.

<br />

---

## **Configuração**

Após selecionar o **CSV Decorator** como Grid Handler Type, o seguinte painel de configuração é exibido:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-empty-config.png" align="center"></figure>

<br />

Os campos de configuração disponíveis são:

<table><tbody><tr><th><p>Campo</p></th><th><p>Descrição</p></th></tr><tr><td><p><strong>CSV File Path</strong></p></td><td><p>Caminho absoluto para o arquivo CSV usado como fonte de pesquisa. Clique no ícone de lápis ✏️ para criar ou editar o arquivo CSV diretamente.</p></td></tr><tr><td><p><strong>Default value if not found</strong></p></td><td><p>Valor padrão atribuído às novas colunas da Grid quando não há linha correspondente no arquivo CSV.</p></td></tr><tr><td><p><strong>Delimiter</strong></p></td><td><p>Caractere delimitador usado no arquivo CSV. O padrão é <code>,</code> (vírgula).</p></td></tr><tr><td><p><strong>Operation</strong></p></td><td><p>Operação lógica usada ao combinar várias colunas de origem (<code>AND</code> exige que todas as colunas correspondam).</p></td></tr><tr><td><p><strong>Source Columns</strong></p></td><td><p>Coluna(s) usada(s) como <strong>chaves de pesquisa</strong> para combinar os registros do CSV com os registros da Grid. Especifique o <strong>CSV Name</strong> (coluna no arquivo CSV) e o <strong>Grid Name</strong> (coluna na Grid).</p></td></tr><tr><td><p><strong>Destination Columns</strong></p></td><td><p>Coluna(s) a ser(em) <strong>criada(s) ou atualizada(s)</strong> na Grid com os valores correspondentes do CSV. Especifique o <strong>CSV Name</strong> e o <strong>Grid Name</strong> desejado.</p></td></tr></tbody></table>

<br />

Para configurar o CSV Decorator, existem duas abordagens principais dependendo do seu objetivo: **Data Mapping** e **Data Enrichment**.

<br />

### **Configuração para Data Mapping**

Para usar o CSV Decorator para mapear valores (por exemplo, substituir um código numérico por um rótulo), siga estas etapas gerais:

<br />

**Passo 1:** Clique no botão **"+ ADD NEW GRID HANDLER"** para adicionar um novo handler à etapa Transform e selecione **CSV Decorator** na lista suspensa Grid Handler Type.

<br />

**Passo 2:** Quando o painel do CSV Decorator aparecer, clique no **ícone de lápis** ✏️ ao lado do campo **CSV File Path** para criar um novo arquivo CSV (ou use **"UPLOAD FILE"** para importar um existente).

<br />

**Passo 3:** Defina o conteúdo do CSV que servirá como tabela de mapeamento. Você pode usar a aba **TABLE** para adicionar colunas e linhas visualmente, ou mudar para a aba **TEXT** para digitar o conteúdo do CSV diretamente como mostrado abaixo:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-csv-text.png" align="center"></figure>

<br />

**Passo 4:** Configure **Source Columns** e **Destination Columns** para definir a relação de pesquisa, em seguida defina o **Default value if not found** e o **Delimiter** conforme necessário.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-mapping-config.png" align="center"></figure>

<br />

**Passo 5:** Clique em **"SAVE"** ✅ para aplicar a configuração.

<br />

**Casos de Uso para Data Mapping:**

-   **Mapeamento de Status de Interface:** Mapear códigos numéricos de status de interface SNMP (por exemplo, `1`, `2`, `3`) para suas descrições legíveis (`up`, `down`, `testing`).
-   **Mapeamento de Protocolo da Camada 4:** Mapear números de protocolo da Camada 4 do modelo OSI (por exemplo, `6`, `17`, `1`) para seus nomes de protocolo correspondentes (`TCP`, `UDP`, `ICMP`).
-   **Qualquer Código Numérico para Descrição:** Qualquer cenário em que um valor numérico ou codificado obtido durante o processo de extração precisa ser traduzido em um rótulo significativo para fins de relatórios ou análises.

<br />

---

### **Configuração para Data Enrichment**

Para usar o CSV Decorator para adicionar novas colunas com informações extras, siga estas etapas gerais. Esta abordagem é comumente usada para enriquecer os dados com informações contextuais de fontes externas. Na maioria dos casos, o **endereço IP** é usado como chave de pesquisa, pois é um campo frequentemente obtido durante o processo de extração do ETL e serve como um identificador confiável para correlacionar com dados de referência externos.

<br />

**Passo 1:** Clique no botão **"+ ADD NEW GRID HANDLER"** para adicionar um novo handler à etapa Transform e selecione **CSV Decorator** na lista suspensa Grid Handler Type.

<br />

**Passo 2:** Clique no **ícone de lápis** ✏️ ao lado do campo **CSV File Path** para criar ou enviar o arquivo CSV contendo os dados de enriquecimento.

<br />

**Passo 3:** Defina o conteúdo do CSV. O CSV deve conter a chave de pesquisa (por exemplo, endereço IP) e as colunas adicionais a serem injetadas:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-enrichment-csv.png" align="center"></figure>

<br />

**Passo 4:** Configure as **Source Columns** (por exemplo, correspondendo ao endereço IP) e várias **Destination Columns** para injetar os dados extras. É recomendável configurar um **Default value if not found**:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-enrichment-config.png" align="center"></figure>

<br />

**Passo 5:** Clique em **"SAVE"** ✅ para aplicar a configuração.

<br />

**Casos de Uso para Data Enrichment:**

-   **Dados Geográficos:** Adicionar informações de país, cidade ou região com base no endereço IP.
-   **Site/Localização:** Associar cada host à sua localização física, prédio ou data center.
-   **Departamento/Área:** Mapear hosts ao departamento, unidade de negócios ou área organizacional a que pertencem.
-   **Funções:** Atribuir funções (por exemplo, `Hypervisor`, `Firewall`, `Active Directory`) a cada host com base em dados de referência externos.
-   **Inventário de Hardware/Software:** Adicionar informações do fornecedor, sistema operacional, versão e tipo de dispositivo para enriquecer os dados de monitoramento.

<br />

---

## **Exemplos Práticos**

As seções seguintes apresentam dois exemplos práticos que ilustram os dois principais casos de uso do CSV Decorator: **Data Mapping** e **Data Enrichment**.

<br />

### **Exemplo 1: Data Mapping**

Neste exemplo, o CSV Decorator é usado para **mapear** os valores de uma coluna da Grid para valores diferentes usando um arquivo CSV externo. Isso é útil quando você precisa substituir valores codificados por rótulos legíveis (por exemplo, substituir um código numérico de status de interface SNMP `1` pelo seu significado `up`).

<br />

O arquivo CSV `ifAdminStatus.csv` contém duas colunas: `value` (o código numérico a ser procurado) e `description` (o rótulo legível a ser retornado):

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-mapping-ifstatus-csv.png" align="center"></figure>

<br />

As **Source Columns** e **Destination Columns** são configuradas da seguinte forma:

-   **Source Columns:** `CSV Name` = `value` e `Grid Name` = `interface-admin-status`. O handler compara os valores na coluna `value` do CSV com a coluna `interface-admin-status` da Grid.
-   **Destination Columns:** `CSV Name` = `description` e `Grid Name` = `interface_admin_status_desc`. O handler cria uma nova coluna `interface_admin_status_desc` na Grid, preenchida com os valores correspondentes de `description` do CSV.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-mapping-ifstatus-config.png" align="center"></figure>

<br />

**Resultado:**

<table><tbody><tr><th><p>interface-admin-status</p></th><th><p>interface_admin_status_desc</p></th></tr><tr><td><p>1</p></td><td><p>up</p></td></tr><tr><td><p>2</p></td><td><p>down</p></td></tr><tr><td><p>3</p></td><td><p>testing</p></td></tr></tbody></table>

<br />

---

### **Exemplo 2: Data Enrichment**

Neste exemplo, o CSV Decorator é usado para **adicionar novas informações** à Grid criando colunas adicionais com base em um campo de referência. Diferente do mapeamento de dados (que substitui valores), o enriquecimento de dados **preserva a coluna original** e adicioniona novas colunas com informações extras.

Esta abordagem é comumente usada para enriquecer os dados com informações como **localização geográfica**, **site físico ou prédio**, **departamento/área/unidade de negócios**, **funções**, **sistema operacional**, **fornecedor** ou quaisquer outros dados contextuais de fontes externas. Na maioria dos casos, o **endereço IP** é usado como chave de pesquisa, pois é um campo frequentemente obtido durante o processo de extração do ETL e serve como um identificador confiável para correlacionar com dados de referência externos.

<br />

O arquivo CSV `inventory_vn_training.csv` contém um inventário completo de hosts de rede com colunas para `ip`, `hostname`, `operating_system`, `role`, `snmp`, `type`, `vendor` e `version`. O endereço IP (`ip`) serve como chave de pesquisa para corresponder os registros na Grid:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-enrichment-inventory-csv.png" align="center"></figure>

<br />

As **Source Columns** e **Destination Columns** são configuradas da seguinte forma:

-   **Source Columns:** `CSV Name` = `ip` e `Grid Name` = `host`. O handler compara a coluna do CSV `ip` (contendo endereços IP) com a coluna `host` da Grid obtida durante a extração.
-   **Destination Columns:** Sete novas colunas são adicionadas: `hostname`, `operating_system`, `role`, `snmp`, `type`, `vendor` e `version`. Cada uma injeta os dados de enriquecimento correspondentes do CSV na Grid.
-   **Default value if not found:** Definido como `No_info` para que as linhas da Grid sem um IP correspondente no arquivo CSV recebam um rótulo padrão claro em vez de ficarem vazias.
-   **Delimiter:** Definido como `:` já que o arquivo CSV usa dois pontos como separador.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-enrichment-inventory-config.png" align="center"></figure>

<br />

**Resultado:**

A Grid agora contém sete novas colunas com os dados de inventário enriquecidos, enquanto a coluna `host` original permanece inalterada:

<table><tbody><tr><th><p>host</p></th><th><p>hostname</p></th><th><p>operating_system</p></th><th><p>role</p></th><th><p>type</p></th><th><p>vendor</p></th><th><p>version</p></th></tr><tr><td><p>192.168.1.10</p></td><td><p>training.view</p></td><td><p>PVE</p></td><td><p>Hypervisor</p></td><td><p>SuperMicro</p></td><td><p>Proxmox</p></td><td><p>8.1.4</p></td></tr><tr><td><p>10.30.23.1</p></td><td><p>cancerbero.v</p></td><td><p>FreeBSD</p></td><td><p>Training Firewall</p></td><td><p>Virtual Machine</p></td><td><p>Netgate-Pfsense</p></td><td><p>14.0</p></td></tr><tr><td><p>10.30.23.2</p></td><td><p>guacamole.v</p></td><td><p>Ubuntu</p></td><td><p>Remote Desktop</p></td><td><p>LX Container</p></td><td><p>Viewtinet</p></td><td><p>24.04</p></td></tr><tr><td><p>10.30.23.99</p></td><td><p><em>(unknown)</em></p></td><td><p>No_info</p></td><td><p>No_info</p></td><td><p>No_info</p></td><td><p>No_info</p></td><td><p>No_info</p></td></tr></tbody></table>

<br />

<div class="sd-callout" data-callout-type="info"><strong>Diferença Principal:</strong> No <strong>Data Mapping</strong> (Exemplo 1), a Destination Column usa o <strong>mesmo Grid Name</strong> que uma coluna existente, para que os valores originais sejam <strong>substituídos</strong>. No <strong>Data Enrichment</strong> (Exemplo 2), a Destination Column usa um <strong>novo Grid Name</strong>, portanto, novas colunas são <strong>adicionadas</strong> enquanto os dados originais são preservados.</div>

<br />

---

## **Pesquisa em Múltiplas Colunas**

O CSV Decorator suporta a correspondência em **várias colunas simultaneamente**. Quando várias Source Columns são configuradas e o **Operation** é definido como `AND`, **todos os valores devem corresponder** para que um registro do CSV seja considerado um acerto válido.

Por exemplo, você pode verificar `transport` e `port` para encontrar o `service` correspondente em um arquivo CSV.

O seguinte arquivo CSV (`iana-port-config.csv`) contém o mapeamento de várias colunas:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-ianaport-csv.png" align="center"></figure>

<br />

As Source Columns estão configuradas para combinar `transport` com `netflow.protocol` e `port` com `netflow.dst_port`. A Destination Column extrai o `service` correspondente para `dst_service`:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/csv-decorator-ianaport-config-v2.png" align="center"></figure>

<div class="sd-callout" data-callout-type="tip"><strong>Melhor Prática:</strong> Use o CSV Decorator para enriquecer dinamicamente os dados do pipeline com informações de fontes externas, como mapear endereços IP para localizações geográficas, traduzir códigos de status SNMP para rótulos legíveis ou adicionar metadados específicos do fornecedor a partir de uma tabela de referência. Isso evita definir valores diretamente na configuração do pipeline e permite atualizar os dados de pesquisa apenas modificando o arquivo CSV sem reimplantar o pipeline.</div>

<br />