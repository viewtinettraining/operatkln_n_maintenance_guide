---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: Autodiscovery
id: EOY-4ORU-YGC-AEB
slug: autodiscovery
isVisible: false
isSearchable: true
lastUpdated: '2026-09-10 19:57:53'
---
## **<span align="center"><span class="text-large">Provisionamento via Autodescoberta</span></span>**

<br />

<span align="justify">A Autodescoberta (Autodiscovery) permite que você escaneie dinamicamente as faixas da sua rede e integre automaticamente os dispositivos ao Viewtinet — sem a necessidade de um arquivo CSV. Diferente da importação por CSV (que depende de uma lista estática de IPs/hostnames), a Autodescoberta:</span>

-   **Descobre dispositivos desconhecidos** em tempo real
-   **Coleta dados SNMP/ICMP ao vivo** durante a varredura
-   **Preenche automaticamente campos do inventário**, como endereço MAC, sysObjectID e systemName

---

### **Etapa 1: Iniciar a Autodescoberta**

1.  No console web do Viewtinet, clique em **Inventory** → **AUTODISCOVERY**.
2.  Clique em **LAUNCH NEW AUTO DISCOVERY**.<br />
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/ph8kCTL7Ob1x3I4Jk7F5.png" align="center"></figure>

---

### **Etapa 2: Especificar os Alvos**

Insira uma ou mais especificações de alvo compatíveis com o nmap no campo **Targets**. Os formatos suportados incluem:

-   **IP Único**: `10.30.23.41`
-   **Intervalo de IPs**: `10.30.23.41-50`
-   **Bloco CIDR**: `10.30.23.0/24`
-   **Lista separada por vírgulas**: `10.30.23.41,10.30.23.42,10.30.23.50`
-   **Hostname ou nome DNS**: `router1.example.com`
-   Em seguida, preencha **Pipeline Name**, **Depth**, **Execute Timeout** e **Community string**, e clique em **RUN** para iniciar a descoberta.<br />
    

l

---

### **Etapa 3: Revisar e Pré-Processar Resultados**

Assim que a varredura for concluída (ícone ✅):

1.  Selecione o ID de execução no painel esquerdo.
2.  Mude para a aba **DEVICES** em Autodiscovery.
3.  Uma tabela de visualização lista os hosts descobertos com colunas como IP/Hostname, MAC, sw\_version, sys\_object\_id e system\_name.
4.  Use a caixa de filtro ou o Query Builder (Construtor de Consultas) para incluir ou excluir dispositivos antes de importar.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/KqkUIcnfHxf2LnQNavEx.png" align="center"></figure>

---

### **Etapa 4: Importar para o Inventário**

1.  Marque as caixas de seleção dos dispositivos que você deseja integrar (ou use a caixa de seleção do cabeçalho para selecionar todos).
2.  Clique em **IMPORT INTO INVENTORY** (Importar para o Inventário) no canto superior direito.
3.  Os hosts selecionados são adicionados à visualização principal do seu Inventory, prontos para relações de credenciais e atribuições de plugins.
4.  Mude para a aba **OVERVIEW** em **Inventory** para ver os hosts recém-importados.<br />
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/kmSiJa5aXDQgeBSmESFX.png" align="center"></figure>

<br />

<figure align="center" style="width:53%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/M21oAe0BoMhZzRSviYRZ.png" width="53%" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/RAj1n2Zz3yTK9QIhfhjM.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/honsa5vZ8iuUF32xMGZj.png" align="center"></figure>

---

### **Etapa 5: Filtragem de Inventário**

<span align="justify">O Inventory do Viewtinet inclui um poderoso e flexível Filter Builder (Construtor de Filtros) que permite consultar, combinar e salvar filtros de dispositivos em tempo real. Use filtros para restringir grandes inventários por qualquer atributo de dispositivo — IP/Hostname, fabricante, versão de SO e muito mais.</span>

<br />

1.  **Abra o Query Builder**<br />
    Clique no ícone de lápis ao lado da caixa de filtro para iniciar o avançado Query Builder.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/MXu73yQf9PQRXkztxfqm.png"></figure>
    
    <br />
    
2.  **Adicionar Regras ou Grupos**<br />
    No modal do construtor, clique em **\+ Add Rule** (Adicionar Regra) para adicionar uma única condição, ou **\+ Add Group** (Adicionar Grupo) para combinar múltiplas regras com a lógica AND/OR.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/tDSps7m7zKJLOrEJklbl.png"></figure>
    
    <br />
    
3.  **Selecionar um Campo**<br />
    Para cada regra, escolha o campo de inventário pelo qual deseja filtrar (ex: `device`, `ip`, `vendor`, `operating_system`).
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/xlDB8Eocp9EaZu4u55ye.png"></figure>
    
    <br />
    
4.  **Escolher um Operador**<br />
    Selecione um operador para definir seus critérios de correspondência:
    
    -   `==` (igual a)
    -   `!=` (diferente de)
    -   `Contains` / `Not contains` (Contém / Não contém)
    -   `Starts with` / `Ends with` (Começa com / Termina com)
    -   `Is empty` / `Is not empty` (Está vazio / Não está vazio)
    
    <br />
    
5.  **Inserir um Valor e Aplicar**<br />
    Digite o valor de comparação (ex: `contains vlog`) e clique em **OK**. A expressão do filtro aparecerá na visualização principal do Inventory.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/pQiVYiyFoCxueO9OLiWQ.png"></figure>
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/BUObc67Y0idfUhnNYFDb.png"></figure>
    
    <br />
    
6.  **Salvar o seu Filtro**<br />
    Para reutilizar este filtro posteriormente, clique em **SAVE FILTER**, dê um nome a ele e clique em **OK**.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/ETWH7S4Rbm8yYQn3qAX5.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/TyELEQPUtYFvh4oPpzdK.png" align="center"></figure>

<br />
<span align="justify">Com o Filter Builder você pode investigar detalhadamente o seu inventário, combinar condições complexas e salvar suas consultas mais utilizadas para acesso em um clique. A seguir, nós mostraremos como criar grupos dinâmicos com base nesses filtros.</span>

### <br />

**Etapa 6: Selecionando e Atribuindo Grupos de OID**

<span align="justify">Um Grupo de OID (OID Group) é uma coleção nomeada de Identificadores de Objeto (OIDs) SNMP que especifica exatamente quais métricas e contadores consultar a partir de um dispositivo. Ao atribuir grupos de OID, você garante que o Viewtinet colete o conjunto correto de dados SNMP para cada tipo de dispositivo.</span>

### **Adicionar a Coluna OID Groups**<br />

1.  Na visualização do Inventory, clique no ícone de ajuda **?**, e então escolha **Add New Column**.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/sdPthHO5Dg0kgR3mAPX2.png"></figure>
    
    <br />
    
2.  Na modal **System Fields**, expanda **VSDB** e clique no **+** ao lado de **oid\_group\_names**, depois clique em **OK**.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Z8nyy9z58mAbOekycAzm.png" align="center"></figure>
    
    <br />
    
    <figure align="center" style="width:44%"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Y33N4DyecgDc0zPA5I5h.png" width="44%" align="center"></figure>
    
    <br />
    
3.  A nova coluna **oid\_group\_names** aparece agora em sua lista de dispositivos.
    
    <br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/OizNID3L0VLDfPz27pTq.png"></figure>
    
    ⚠️ **Nota:** A coluna **oid\_group\_names** precisa ser adicionada **apenas uma vez**; ela permanecerá disponível na visualização do inventário a partir de então.
    
    <br />
    
    **Filtrar e Atribuir Valores para Grupos de OID**
    
    <br />
    
4.  Filtre suas fontes de dados**.** Use os filtros de inventário para restringir os dispositivos que você deseja configurar — ex: filtrar por system\_name `vlog` — de forma que os grupos de OID sejam atribuídos apenas ao subconjunto relevante.<br />
    
5.  Insira o nome do grupo OID**.** No cabeçalho oid\_group\_names (ou na célula individual por linha), digite o nome do grupo OID — separado por vírgula se atribuir vários grupos (ex: `net-SNMPAgent,general`) — e pressione **Enter**. Uma lista suspensa irá sugerir nomes de grupos existentes à medida que você digita.<br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/rcbmo0FluC7TpecKN6SD.png"></figure>
    
    <br />
    
6.  **Aplicar à sua seleção.** Depois de pressionar **Enter**, o nome do grupo é aplicado a todas as linhas filtradas (selecionadas) ou a linhas individuais conforme necessário.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/4aZZbkyLX9r1YOx9hcBt.png" align="center"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/PZYnOtxUxQ4ZWC29hrjD.png"></figure>

### **Etapa 3: Salvar suas Alterações**

<br />
Clique em **SAVE CHANGES** no canto inferior direito para persistir suas atribuições de grupos de OID.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/DCkyap8nQzAZPY5XjIbx.png" align="center"></figure>

Um banner de confirmação aparecerá assim que o inventário for salvo com sucesso.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/b6EsvUPa4hddixDTteBa.png" align="center"></figure>

---

### **Configurando Credenciais**

No Viewtinet, as **Credenciais** definem como o sistema se autentica tanto para **coletar contadores e métricas** (SNMP, ICMP, WMI) quanto para **gerenciar configurações** (SSH/HTTPS) em seus dispositivos. Cada protocolo requer sua própria entrada de credencial:

-   **ICMP**: Verificações básicas de alcance e latência.
-   **SNMP v1/v2c/v3**: Consultar contadores, tabelas e outras métricas de dispositivos.
-   **SSH / Telnet**: Acesso CLI para configuração avançada.

> ⚠️ **Nota:** Se durante a Autodescoberta você escolheu **Import credentials**, quaisquer credenciais SNMP descobertas serão automaticamente adicionadas ao seu inventário. Nesse caso, a **única credencial** que você precisa criar manualmente é a de **ICMP**

Se as credenciais SNMP **não** foram importadas via Autodescoberta, as etapas a seguir mostrarão como configurá-las manualmente.

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

1.  Na coluna **SNMP Version**, escolha **2c** (ou v1/v3 conforme necessário).
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/sL9Qqkc4gIvotWf4RNvL.png"><br />
    
2.  Insira a string de **Community** (obrigatória para v1/v2c).
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XjTleODdmXQNcldspFk8.png"><br />
    <span align="center">(Neste exemplo, nós usamos training.)</span><br />
    
3.  Para **SNMP v3**, você também preencheria **Security Level**, **Auth Protocol**, **Auth Passphrase**, **Priv Protocol** e **Priv Passphrase**.

<br />

### **Etapa 4: Salvar suas Alterações**

1.  Após concluir todos os campos obrigatórios, clique no botão **SAVE CHANGES** no canto inferior direito.
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/gATCIy4xaapGL0n371bV.png"><br />
    
2.  Uma notificação de sucesso confirmará que suas credenciais foram salvas.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/cPxzfyd6SZPeuSnc7Zr4.png" align="center"></figure>
    

<br />

## **Gerenciando Relações de Dispositivos e Credenciais**

<span align="justify">A aba Relations permite atribuir uma ou mais entradas de credenciais a um conjunto de dispositivos. Você pode usar filtros para selecionar exatamente os dispositivos que você precisa — ex: todos os switches que usam SNMP v2c com uma comunidade específica — e depois relacioná-los à credencial SNMP correspondente.</span>

<br />

### **Etapa 1: Abrir a Aba de Relações (Relations)**

No console do Inventory, clique em **Relations** para visualizar a interface de mapeamento entre dispositivos e credenciais.

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/DFACzLKlGIcuFAkiJkyt.png"></figure>

### **Etapa 2: Filtrar Dispositivos**

Use a caixa de filtro ou o Query Builder para restringir a lista de dispositivos. Você pode escolher um subconjunto específico (por exemplo `dev.sw_version == '2c'` ou `dev.vendor == 'LINUX'`), ou escolher o filtro "All devices" (Todos os dispositivos) se cada fonte de dados usar a mesma comunidade SNMP (ou para protocolos simples como ICMP).

### <br />

**Etapa 3: Selecionar Dispositivos**

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/vJU5IFke2vtFfn3lKfHc.png"></figure>

Uma vez filtrados, use as caixas de seleção na primeira coluna para selecionar todos os dispositivos correspondentes (ou escolha entradas individuais).

### **Etapa 4: Selecionar Credenciais**

Role para baixo até o painel Credentials (Credenciais). Use seu filtro para encontrar a entrada de credencial que você deseja (por exemplo, sua comunidade `snmp-2c-training`). Em seguida, selecione a caixa de seleção ao lado dessa credencial.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/liOmqW0ZkTVsNPw0xenp.png" align="center"></figure>

### **Etapa 5: Salvar as Relações**

Clique em **SAVE CHANGES** (Salvar Alterações) no canto inferior direito para aplicar suas atribuições. Uma notificação de confirmação (toast) aparecerá assim que as relações forem salvas.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/rqPy2bh7qTD1TmfvbVPH.png" align="center"></figure>

<span align="justify">Ao usar filtros em conjunto com a seleção em massa, você pode rapidamente atribuir conjuntos de credenciais específicos — comunidades SNMP, chaves SSH ou configurações ICMP — exatamente aos dispositivos que necessitam deles, garantindo que cada dispositivo use os parâmetros de autenticação corretos</span>.

---

## **Instalando Plugins**

<br />

O Viewtinet usa um **framework de plugins** para mapear dados do inventário em pipelines de processamento de dados. Nesta seção nós vamos instalar o plugin **Network Monitoring** para todas as suas fontes de dados.

<br />

> ⚠️ **Aviso:** Como nós estamos aplicando **todas** as fontes de dados para o plugin **Network Monitoring**, **nenhum filtro** é usado nesta etapa. Os filtros se tornam essenciais quando você quer instalar plugins **específicos de um fabricante** somente em certos dispositivos.

---

<br />

### **Etapa 1: Abrir a Aba de Plugins**

No console do Inventory, clique em **PLUGINS**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/2SiOKpo4yqgk0Y5Stzmb.png" align="center"></figure>

### <br />

**Etapa 2: (Sem Filtros) Selecionar "All devices"**

Já que nós estamos instalando em todas as fontes de dados, marque o filtro **All devices**.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/XwzPHTpvcjM6LwxBrGXL.png"><br />

### **Etapa 3: Escolher o Plugin Network Monitoring**

No painel de **Plugins**, expanda **network monitoring** e selecione:

-   **snmp\_device\_config**
-   **snmp\_if\_config**
-   **icmp**<br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/qJQlxOW78mTTJYjCoBL7.png">

<br />

### **Etapa 4: Modificar e Instalar**

Clique em **MODIFY AND INSTALL PLUGINS** no canto inferior direito.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/kq16Kb1vv4xS6zHgQp2P.png"><br />

### **Etapa 5: Confirmar a Seleção de Plugins**

No modal **Select plugins**:

1.  Certifique-se de que **network monitoring** está marcado em **PLUGINS TO BE MODIFIED**
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

Você será redirecionado para o **Visual Smart Data Broker**. Clique em **FINISH INSTALLATION** para completar o processo.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/BIvAlNoBMTl2Hm4sYHMi.png" align="center"></figure>

Neste ponto, de acordo com a configuração do seu pipeline, as **métricas, contadores e todas as dimensões** das suas fontes de dados estão sendo ingeridas no banco de dados para análise e criação de dashboards.

Com a Autodescoberta, você pode manter o seu inventário atualizado e preciso descobrindo, filtrando e importando dispositivos em um único fluxo de trabalho — não sendo necessária a edição manual de arquivos CSV.<br />