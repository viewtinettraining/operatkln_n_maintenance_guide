---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Provisioning via CSV'
id: 2A2-7D2C-90M-3P1
slug: provisioning-via-csv
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:57:32'
---
## **<span align="center"><span class="text-large">Provisionamento via Arquivo CSV</span></span>**

<br />

O Viewtinet suporta a integração em massa de dispositivos por meio de uma simples importação de CSV. Você pode criar o layout do CSV para se adequar ao seu ambiente, mas aplicam-se as seguintes regras:

-   **Campo Obrigatório**
    
    -   `ip_address` _ou_ `hostname`<br />
        Uma destas colunas **deve** estar presente em cada linha.
        
        -   Se você escolher `hostname`, certifique-se de que o Viewtinet consiga resolver nomes DNS em sua rede de implantação.
-   **Campos Recomendados**<br />
    Adicionar colunas extras melhorará muito a sua capacidade de filtrar, agrupar e gerenciar dispositivos. Sugestões comuns incluem:
    
    -   `location` (ex: "Data Center 1", "Building A")
    -   `device_type` (ex: "router", "switch", "firewall")
    -   `vendor` (ex: "Cisco", "Juniper", "Arista")
    -   `model` (ex: "ISR4451", "EX4300")
    -   `os_version` (ex: "IOS XE 17.3.1")
    -   `department` (ex: "IT", "Engineering")

<br />

### **Diretrizes para o Arquivo CSV**

1.  **Linha de Cabeçalho**<br />
    A primeira linha deve conter os nomes das colunas. No mínimo, inclua `ip_address` ou `hostname`.
2.  **Delimitador**<br />
    Use vírgula (`,`) como o separador de campos. Strings entre aspas são suportadas.
3.  **Codificação**<br />
    Recomenda-se UTF-8 sem BOM para evitar problemas de análise (parsing).
4.  **Tamanho do Arquivo**<br />
    Para inventários grandes (&gt;10 000 linhas), divida em vários CSVs de no máximo 5 000 linhas cada para garantir uma importação suave.

### **Exemplo de CSV**<br />

```csv
ip,device,vendor,operating_system,sw_version
192.168.1.101,training,LINUX,Ubuntu 22.04,PROXMOX 8.1.4
10.30.23.1,cancerbero,LINUX,Free BSD,PFSense 2.7.2
10.30.23.2,guacamole,LINUX,Ubuntu 23.04,APACHE GUACAMOLE
10.30.23.4,ares,LINUX,Ubuntu 20.04,Viewtinet 6.3.5-Viewtify
10.30.23.5,zeus,LINUX,Ubuntu 20.04,Viewtinet 6.3.5-Viewtilog
10.30.23.6,dante,LINUX,Ubuntu 20.04,Viewtinet 6.3.5-Viewtilog
10.30.23.7,apolo,LINUX,Ubuntu 24.04,Viewtinet 6.3.5-Viewtilog
10.30.23.8,perseo,MICROSOFT,Windows Server,2022
10.30.23.9,hades,LINUX,Ubuntu 24.04,Viewtinet 6.3.5-Viewtilog
10.30.23.10,jupiter,LINUX,Ubuntu 20.04,Apache HTTP
```

---

### **Importação de CSV**

Você pode integrar rapidamente dispositivos ao Viewtinet importando um arquivo CSV. Siga estes passos:

1.  **Faça login e abra a página do Inventory**<br />
    No console web do Viewtinet, clique em **Inventory** no menu à esquerda.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/N6jH7knUvf9zoOcY34yx.png" align="center"></figure>
    

<br />

2.  **Iniciar a importação de CSV**<br />
    Clique em **IMPORT A LIST OF DEVICES AND/OR CREDENTIALS FROM CSV** (Importar uma lista de dispositivos e/ou credenciais via CSV) na parte superior da aba Devices.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Cx0SvdM6m7fGvfYKnXcX.png"></figure>
    
    <br />
    
3.  **Selecionar o seu arquivo CSV**<br />
    Na caixa de diálogo de seleção de arquivo, localize e selecione o seu CSV (por exemplo, `inventory_example_guide.csv`) e, em seguida, clique em **Open**.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/D4zbqtfjdvBxl1Om8KwN.png"></figure>
    
    <br />
    
4.  **Visualizar e mapear colunas**<br />
    A caixa de diálogo "Select which columns are to be imported" (Selecione quais colunas devem ser importadas) mostra uma pré-visualização do seu CSV.
    
    -   Verifique o **Separator** (Separador, `,` por padrão) e o **Source name** (Nome da fonte, o nome do seu arquivo).
    -   Clique em **AUTO-ASSIGN COLUMNS** (Atribuir Colunas Automaticamente) para mapear os cabeçalhos do CSV aos campos de inventário do Viewtinet (`dev.ip`, `dev.hostname`, etc.).
        
        <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/1oWZI2Uhxc8a68bBR0qs.png"></figure>
        
        <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/nWfwLlJoqY3QbNoDdXMI.png"></figure>
        
        <br />
        
5.  **Importar os campos**<br />
    Após todos os campos obrigatórios (IP ou Hostname) e atributos adicionais estarem mapeados, clique em **IMPORT FIELDS** (Importar Campos) para iniciar o provisionamento.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/ihRlKdmQf7gqtinVxyuh.png" align="center"></figure>

6.  **Salvar os dispositivos importados**<br />
    Após a conclusão da importação, clique no botão **SAVE** no canto inferior direito da página de Inventory para finalizar a adição dos dispositivos ao seu inventário.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XgoF5nshV58Sdb50dUdO.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/hvJbPy2IMu4KeCFzLrLq.png" align="center"></figure>

<br />

<span align="justify">Ao terminar, o Viewtinet exibirá um resumo dos dispositivos importados e das linhas que falharam na validação. Agora você pode gerenciar e filtrar seu inventário recém-integrado.</span>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/reTQUSzvvS1jpIg7v8GV.png" align="center"></figure>

---

## **Filtragem de Inventário**

<span align="justify">O Inventory do Viewtinet inclui um poderoso e flexível Filter Builder (Construtor de Filtros) que permite consultar, combinar e salvar filtros de dispositivos em tempo real. Use filtros para restringir grandes inventários por qualquer atributo de dispositivo — IP/Hostname, fabricante, versão de SO e muito mais.</span>

<br />

1.  **Abra o Query Builder (Construtor de Consultas)**<br />
    Clique no ícone de lápis ao lado da caixa de filtro para abrir o avançado Query Builder.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/MXu73yQf9PQRXkztxfqm.png"></figure>
    
    <br />
    
2.  **Adicionar Regras ou Grupos**<br />
    Na janela modal de criação, clique em **\+ Add Rule** (Adicionar Regra) para adicionar uma única condição, ou **\+ Add Group** (Adicionar Grupo) para combinar várias regras com lógica AND/OR (E/OU).
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/tDSps7m7zKJLOrEJklbl.png"></figure>
    
    <br />
    
3.  **Selecionar um Campo**<br />
    Para cada regra, escolha o campo do inventário pelo qual deseja filtrar (ex: `device`, `ip`, `vendor`, `operating_system`).
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/J9yZF7DSaR7OmXmxACea.png"></figure>
    
    <br />
    
4.  **Escolher um Operador**<br />
    Selecione um operador para definir seus critérios de correspondência:
    
    -   `==` (igual a)
    -   `!=` (diferente de)
    -   `Contains` / `Not contains` (Contém / Não contém)
    -   `Starts with` / `Ends with` (Começa com / Termina com)
    -   `Is empty` / `Is not empty` (Está vazio / Não está vazio)
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/YJguyKOwmLxzeQJQyUHg.png" align="center"></figure>
    
    <br />
    
5.  **Inserir um Valor e Aplicar**<br />
    Digite o valor de comparação (ex: `LINUX`) e clique em **OK**. A expressão do filtro aparecerá na visualização principal do Inventory.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/dB67Z20w8MeyW7BM6Vn9.png"></figure>
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/qVnFCJbEAFtP9ThWWk6l.png"></figure>
    
    <br />
    
6.  **Salvar seu Filtro**<br />
    Para reutilizar este filtro mais tarde, clique em **SAVE FILTER** (Salvar Filtro), dê-lhe um nome e clique em **OK**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/eFHC6n7zUpb9Tz27mKS6.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/vLtyFf0e0GAkDSPqPR4n.png" align="center"></figure>

<span align="justify">Com o Filter Builder, você pode detalhar rapidamente seu inventário, combinar condições complexas e salvar as consultas mais utilizadas para acesso em um clique. A seguir, mostraremos como criar grupos dinâmicos baseados nesses filtros.</span>

<br />

---

## **Selecionando e Atribuindo Grupos de OID**

<span align="justify">Um Grupo de OID (OID Group) é uma coleção nomeada de Identificadores de Objeto (OIDs) SNMP que especifica exatamente quais métricas e contadores consultar em um dispositivo. Ao atribuir grupos OID, você garante que o Viewtinet colete o conjunto correto de dados SNMP para cada tipo de dispositivo.</span>

<br />

### **Etapa 1: Adicionar a Coluna OID Groups**

<br />

1.  Na visualização do Inventory, clique no ícone de ajuda **?**, em seguida, escolha **Add New Column** (Adicionar Nova Coluna).
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/sdPthHO5Dg0kgR3mAPX2.png"></figure>
    
    <br />
    
2.  No modal **System Fields**, expanda **VSDB** e clique no **+** ao lado de **oid\_group\_names**, depois clique em **OK**.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Z8nyy9z58mAbOekycAzm.png" align="center"></figure>
    
    <br />
    
    <figure align="center" style="width:44%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Y33N4DyecgDc0zPA5I5h.png" width="44%" align="center"></figure>
    
    <br />
    
3.  A nova coluna **oid\_group\_names** aparecerá agora na sua lista de dispositivos.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/VZArdNK8ZbIiRV1ErQwZ.png" align="center"></figure>
    
    ⚠️ **Nota:** A coluna **oid\_group\_names** precisa ser adicionada **apenas uma vez**; ela permanecerá disponível na visualização do inventário dali em diante.
    
    <br />
    

### **Etapa 2: Filtrar e Atribuir Valores de Grupos OID**<br />

1.  Filtre suas fontes de dados**.** Use os filtros de inventário para restringir os dispositivos que deseja configurar — ex: filtre por operating system `LINUX` — de forma que os grupos OID sejam atribuídos apenas ao subconjunto relevante.<br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/dcS8MkP7PhxomoJYCiiG.png"></figure>
    
2.  Insira o nome do grupo OID**.** No cabeçalho oid\_group\_names (ou na célula individual da linha), digite o nome do grupo OID — separado por vírgula se atribuir múltiplos grupos (ex: `net-SNMPAgent,general`) — e pressione **Enter**. Uma lista suspensa sugerirá nomes de grupos existentes enquanto você digita.<br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/tPKqQ4K0lAUqvLuo4k86.png"></figure>
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/LNtl0YM0YgvSEUias498.png" align="center"></figure>
    
    <br />
    
3.  **Aplicar à sua seleção.** Depois de pressionar **Enter**, o nome do grupo será aplicado a todas as linhas filtradas (selecionadas) ou a linhas individuais, conforme necessário.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/LC7E0ZcptPmlxd8z6bcC.png"></figure>
    

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/VYeFNAJTehxVnmjdiXcM.png" align="center"></figure>

<br />

### **Etapa 3: Salvar suas Alterações**

<br />

Clique em **SAVE CHANGES** (Salvar Alterações) no canto inferior direito para manter suas atribuições de grupo OID.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/DCkyap8nQzAZPY5XjIbx.png" align="center"></figure>

Um banner de confirmação aparecerá quando o inventário for salvo com sucesso.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/b6EsvUPa4hddixDTteBa.png" align="center"></figure>

---

### **Configurando Credenciais**

<span align="justify">No Viewtinet, Credenciais definem como o sistema se autentica nos seus dispositivos e fontes de dados externas. As credenciais são usadas tanto para coletar contadores e métricas (SNMP e ICMP) quanto para gerenciar configurações via SSH/Telnet (através do Configuration Manager, abordado em um capítulo posterior).</span>

<br />
**Protocolos Suportados**

-   **ICMP**
-   **SNMP v1 / v2c / v3**
-   **SSH**
-   **Telnet**

### **Etapa 1: Abrir a Aba de Credenciais**<br />

1.  No console web do Viewtinet, clique em **Inventory → Credentials**.
2.  A tabela de Credenciais exibe as entradas existentes e colunas de protocolos suportados.
    
    <br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/hqDwDbbd9JssBb4T7vcQ.png">

<br />

### **Etapa 2: Adicionar uma Nova Credencial**<br />

1.  Clique em **\+ ADD NEW CREDENTIAL** na parte inferior da tabela.
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/4Iyvj9HhwA7wAEGhMEIN.png"><br />
    
2.  Uma nova linha em branco é adicionada. Em **Protocol**, selecione o protocolo desejado (ex: **snmp**).
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/ZwfBwI3MFDPy4wETiOyx.png"><br />
    

### **Etapa 3: Configurar as Credenciais SNMP**<br />

1.  Na coluna **SNMP Version**, escolha **2c** (ou v1/v3 conforme a necessidade).
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/sL9Qqkc4gIvotWf4RNvL.png"><br />
    
2.  Insira a string de **Community** (obrigatório para v1/v2c).
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XjTleODdmXQNcldspFk8.png"><br />
    <span align="center">(Neste exemplo, nós usamos training.)</span><br />
    
3.  Para **SNMP v3**, você também preencheria **Security Level**, **Auth Protocol**, **Auth Passphrase**, **Priv Protocol** e **Priv Passphrase**.

### **Etapa 4: Salvar suas Alterações**

1.  Após preencher todos os campos obrigatórios, clique no botão **SAVE CHANGES** no canto inferior direito.
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/gATCIy4xaapGL0n371bV.png"><br />
    
2.  Uma notificação de sucesso confirma que suas credenciais foram salvas.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/cPxzfyd6SZPeuSnc7Zr4.png" align="center"></figure>
    

<br />

## **Gerenciando Relações de Dispositivos e Credenciais**

<span align="justify">A aba Relations (Relações) permite atribuir uma ou mais entradas de credenciais a um conjunto de dispositivos. Você pode usar filtros para selecionar exatamente os dispositivos que você precisa — ex: todos os switches que usam SNMP v2c com uma comunidade específica — e depois relacioná-los à credencial SNMP correspondente.</span>

<br />

### **Etapa 1: Abrir a Aba Relations (Relações)**

No console do Inventory, clique em **Relations** para visualizar a interface de mapeamento entre dispositivos e credenciais.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/1NxpXIbO7NMhXE4xJIhq.png" align="center" data-drop-shadow="disabled"></figure>

### **Etapa 2: Filtrar Dispositivos**

Use a caixa de filtro ou o Query Builder (Construtor de Consultas) para restringir a lista de dispositivos. Você pode escolher um subconjunto específico (por exemplo `dev.sw_version == '2c'` ou `dev.vendor == 'LINUX'`), ou selecionar o filtro "All devices" (Todos os dispositivos) se toda fonte de dados utilizar a mesma comunidade SNMP (ou para protocolos simples como ICMP).

<br />

### **Etapa 3: Selecionar Dispositivos**

Após filtrar, use as caixas de seleção na primeira coluna para selecionar todos os dispositivos correspondentes (ou escolha entradas individuais).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/B957jDadVBKuoqvX4pAo.png" align="center"></figure>

### **Etapa 4: Selecionar Credenciais**

Role para baixo até o painel Credentials (Credenciais). Use o seu filtro para encontrar a entrada de credencial desejada (por exemplo, sua comunidade `snmp-2c-training`). Em seguida, marque a caixa de seleção ao lado dessa credencial.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/liOmqW0ZkTVsNPw0xenp.png" align="center"></figure>

### **Etapa 5: Salvar Relações**

Clique em **SAVE CHANGES** (Salvar Alterações) no canto inferior direito para aplicar as suas atribuições. Um alerta de confirmação aparecerá assim que as relações forem salvas.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/rqPy2bh7qTD1TmfvbVPH.png" align="center"></figure>

<span align="justify">Ao usar filtros em conjunto com a seleção em massa, você pode rapidamente atribuir conjuntos específicos de credenciais — comunidades SNMP, chaves SSH, ou configurações de ICMP — exatamente aos dispositivos que necessitam delas, garantindo que cada dispositivo use os parâmetros de autenticação corretos</span>.

---

## **Instalando Plugins**

O Viewtinet utiliza um **framework de plugins** para mapear dados de inventário para pipelines de processamento de dados. Nesta seção, nós instalaremos o plugin **Network Monitoring** (Monitoramento de Rede) para todas as suas fontes de dados.

<br />

> ⚠️ **Aviso:** Como estamos aplicando **todas** as fontes de dados para o plugin **Network Monitoring**, **nenhum filtro** é usado nesta etapa. Filtros se tornam essenciais quando você deseja instalar plugins **específicos de um fabricante** somente em certos dispositivos.

---

<br />

### **Etapa 1: Abrir a Aba de Plugins**

No console do Inventory, clique em **PLUGINS**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/2SiOKpo4yqgk0Y5Stzmb.png" align="center"></figure>

### **Etapa 2: (Sem Filtros) Selecionar "All devices"**

Como nós estamos instalando em todas as fontes de dados, marque o filtro **All devices** (Todos os dispositivos).<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XwzPHTpvcjM6LwxBrGXL.png"><br />

### **Etapa 3: Escolher o Plugin Network Monitoring**

No painel de **Plugins**, expanda **network monitoring** e selecione:

-   **snmp\_device\_config**
-   **snmp\_if\_config**
-   **icmp**<br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/qJQlxOW78mTTJYjCoBL7.png">

### <br />

### **Etapa 4: Modificar e Instalar**

Clique em **MODIFY AND INSTALL PLUGINS** no canto inferior direito.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/kq16Kb1vv4xS6zHgQp2P.png"><br />

### **Etapa 5: Confirmar a Seleção de Plugins**

Na janela modal **Select plugins**:

1.  Certifique-se de que **network monitoring** esteja marcado sob **PLUGINS TO BE MODIFIED**
2.  Marque **Also INSTALL them**
3.  (Opcional) Marque **Unattended installation**
4.  Clique em **OK**<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/aIftba2pgGkskspMAdit.png" align="center"></figure>
    
    <br />
    

### **Etapa 6: Sucesso na Instalação**

Um aviso verde confirmará:

> **1 plugins successfully modified. Redirecting to V.S. Data Broker…** (1 plugins modificados com sucesso. Redirecionando para V.S. Data Broker…)<br />
> 
> <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/HU2IAsKk1LIqnsKJpa6V.png" align="center"></figure>
> 
> <br />

Você será redirecionado para o **Visual Smart Data Broker**. Clique em **FINISH INSTALLATION** (Concluir Instalação) para finalizar o processo.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/BIvAlNoBMTl2Hm4sYHMi.png" align="center"></figure>

Neste ponto, de acordo com a sua configuração de pipeline, as **métricas, os contadores e todas as dimensões** das suas fontes de dados estão sendo ingeridas agora no banco de dados para análise e criação de dashboards.