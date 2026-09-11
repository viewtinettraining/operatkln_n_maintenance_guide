---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Manual Provisioning'
id: CT2-JXYB-K5I-RKQ
slug: manual-provisioning
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:57:41'
---
# **<span align="center">Provisionamento Manual</span>**

<span align="justify">O provisionamento manual é o último recurso para integrar fontes de dados em seu inventário quando a importação por CSV ou a Autodescoberta não forem viáveis (por exemplo, para dispositivos isolados ou entradas únicas). Ele permite que você adicione dispositivos individuais, um de cada vez, e preencha apenas os campos que você precisa.</span>

---

## **Etapa 1: Abrir a Visão Geral de Dispositivos**

1.  No console web do Viewtinet, clique em **Inventory** no menu esquerdo.
2.  Selecione a aba **OVERVIEW**.
3.  Certifique-se de que **DEVICES** está ativo.
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/0tBi4Nrk7U6B7I4LzHrT.png"><br />
    

---

### **Etapa 2: Adicionar uma Nova Linha de Dispositivo**

Role até a parte inferior da lista de dispositivos e clique em **\+ ADD NEW DEVICE**.<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/F5rfRcbeKTL193zgcOwR.png"></figure>

Uma linha em branco aparece no topo ou na parte inferior da tabela, onde você pode inserir os detalhes do dispositivo.

---

### **Etapa 3: Preencher os Campos Obrigatórios e Opcionais**

Insira as informações necessárias e quaisquer detalhes adicionais:

<table><tbody><tr><th><p>Campo</p></th><th><p>Descrição</p></th><th><p>Obrigatório?</p></th></tr><tr><td><p><strong>IP / Hostname</strong></p></td><td><p>Endereço IP ou nome DNS do dispositivo</p></td><td><p>Sim ⭐</p></td></tr><tr><td><p><strong>oid_group_names</strong></p></td><td><p>Grupo(s) OID separados por vírgula</p></td><td><p>Sim ⭐</p></td></tr><tr><td><p><strong>sw_version</strong></p></td><td><p>Versão do Software/SO (ex: Forti OS 7.10)</p></td><td><p>Não</p></td></tr><tr><td><p><strong>source</strong></p></td><td><p>Origem do inventário (ex: <code>user_defined</code>)</p></td><td><p>Não</p></td></tr><tr><td><p><strong>device</strong></p></td><td><p>Nome amigável do dispositivo</p></td><td><p>Não</p></td></tr><tr><td><p><strong>mac</strong></p></td><td><p>Endereço MAC</p></td><td><p>Não</p></td></tr><tr><td><p><strong>sys_object_id</strong></p></td><td><p>sysObjectID SNMP</p></td><td><p>Não</p></td></tr><tr><td><p><strong>system_name</strong></p></td><td><p>systemName SNMP</p></td><td><p>Não</p></td></tr></tbody></table>

> No exemplo abaixo, os contornos **vermelhos** indicam os campos obrigatórios; os contornos **azuis** mostram os campos opcionais:<br />
> 
> <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/28EBGy32GS1VuH0daxa1.png" align="center"></figure>

---

### **Etapa 4: Salvar a sua Entrada**

Depois de preencher os campos, role para baixo e clique em **SAVE CHANGES** (Salvar Alterações). Um banner de confirmação aparecerá:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/CfVxgjH8g4f4g0NSrgEs.png" align="center"></figure>

<span align="justify">O seu dispositivo agora está no inventário e pronto para a atribuição de credenciais, mapeamento de relações e configuração de plugins, conforme detalhado nos capítulos anteriores.</span>

### **Configurando Credenciais**

<span align="justify">No Viewtinet, as Credenciais definem como o sistema se autentica tanto para coletar contadores e métricas (SNMP e ICMP) quanto para gerenciar configurações (SSH/Telnet) em seus dispositivos. Cada protocolo requer sua própria entrada de credencial:</span>

-   **ICMP**: Verificações básicas de alcance e latência.
-   **SNMP v1/v2c/v3**: Consulta contadores, tabelas e outras métricas de dispositivos.
-   **SSH / Telnet**: Acesso via CLI para configuração avançada.<br />
    

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

<br />

### **Etapa 4: Salvar suas Alterações**

1.  Após preencher todos os campos obrigatórios, clique no botão **SAVE CHANGES** no canto inferior direito.
    
    <br />
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/gATCIy4xaapGL0n371bV.png"><br />
    
2.  Uma notificação de sucesso confirma que suas credenciais foram salvas.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/CfVxgjH8g4f4g0NSrgEs.png" align="center"></figure>
    

---

<br />

## **Mapeando Credenciais para Dispositivos Adicionados Manualmente**

Depois de adicionar dispositivos manualmente, você pode atribuir um ou mais conjuntos de credenciais (ICMP, SNMP, etc.) a eles através da aba **Relations**:

<br />

### 1\. Mudar para a Visualização de Relações (Relations)

Clique em **Relations** sob o cabeçalho do Inventory.<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/M434Wi0r1xSTV0mZ8uVO.png" align="center"></figure>

### **2 Isolar o seu Dispositivo Manual**

Use a caixa de filtro ou o Query Builder (Construtor de Consultas) para selecionar apenas o host que você adicionou manualmente (ex: `dev.ip == '10.10.10.1'`).

-   Clique no ícone do lápis para abrir o Query Builder.
-   Adicione uma regra: **ip == 10.10.10.1** e clique em **OK**.

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/PFvq1gQUmWnNQz9uEcPE.png"><br />
<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/gWZoUG7ischO3WERtMW7.png"><br />
<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/k5J2VLIUXSHI7fwv5tiV.png"><br />
<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/GXCSoUvQJob9PB30VKBy.png"><br />

### **3\. Selecionar o(s) Dispositivo(s)**

Marque a caixa ao lado da(s) linha(s) do(s) dispositivo(s) para os quais deseja mapear as credenciais.<br />

### 4\. Selecionar Credencial(is)

Role para baixo até o painel **Credentials**, aplique filtros, se necessário, e marque as caixas das credenciais a serem atribuídas (ex: ICMP & SNMP).<br />

### 5\. Salvar as Relações

Clique em **SAVE CHANGES** no canto inferior direito. Um banner de confirmação aparecerá.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/kWCwmObEro6HVfTWQHsr.png"><br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/M37UrzvpYxOBhrhKY7bS.png" align="center"></figure>

Os dispositivos adicionados manualmente agora estão corretamente relacionados aos conjuntos de credenciais escolhidos.

---

## **Instalando Plugins**

A etapa final no provisionamento das suas fontes de dados é instalar — ou modificar — um ou mais plugins do Viewtinet. Neste guia, demonstraremos a instalação do plugin **Network Monitoring** para os dispositivos que você acabou de definir.

> **Nota:** Neste exemplo, estamos instalando **todos** os plugins de fontes de dados sob **Network Monitoring**, por isso não aplicamos um filtro de dispositivo. No entanto, você _pode_ usar filtros quando precisar instalar plugins apenas para um fabricante específico ou grupo de dispositivos.

<br />

### **1\. Mudar para a Aba Plugins**

Clique em **PLUGINS** no cabeçalho do Inventory.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/EuzQxt95Yl2BNABFbOFA.png">

<br />

### **2\. Definir um Filtro para o Escopo do seu Plugin**

Se desejar apenas modificar/instalar para um grupo de dispositivos específico, clique em **\+ ADD NEW FILTER** (Adicionar Novo Filtro), dê um nome, abra o Query Builder, adicione uma regra (ex: `dev.ip == '10.10.10.1'`) e clique em **OK**.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/MPI9StDO2yZmtp92gmyp.png"><br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/d6mgL8jo92Cx4c8K7O0Y.png" align="center"></figure>

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/cBQ7Ml5ZS0kfJHMiFZI1.png"><br />

<br />

### **3\. Associar Dispositivos aos Plugins**

Na lista de PLUGINS, expanda network monitoring e marque as caixas para:

-   snmp\_device\_config
-   snmp\_if\_config
-   icmp

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/MHwRhXZFN3Of76WJw4mV.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/EIfmkGcsTFdR7XBQrY0J.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/LEBBavUUpm7aaeOOlLHP.png" align="center"></figure>

<br />

### **4\. Iniciar o Processo de Modificar & Instalar**

<br />

Clique em **MODIFY AND INSTALL PLUGINS** no canto inferior direito.<br />

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/njWjunon8KXcL25Cizes.png"><br />

<br />

### **5\. Confirmar as Ações de Plugin**

Na caixa de diálogo “Select plugins” (Selecionar plugins):

-   Verifique se **Network Monitoring** está marcado em **PLUGINS TO BE MODIFIED**
-   Marque **Also INSTALL them** (Também instalá-los)
-   Marque **Unattended installation** (Instalação autônoma)
-   Clique em **OK**

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/5OhwEfQMIXOOSf0Nwvxh.png" align="center"></figure>

<br />

### **6\. Concluir a Instalação**

Um banner de sucesso confirma que o plugin foi modificado. Você será redirecionado ao console Visual Smart Data Broker—clique em **FINISH INSTALLATION** (Concluir Instalação) para finalizar.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/Y8TUddYn4gzRAFtsIVkg.png" align="center"></figure>

Com isso concluído, os seus pipelines começarão a puxar métricas, contadores e outras dimensões de dados para o banco de dados de acordo com a configuração que você definiu.

<br />
<br />
<br />
<br />
<br />
<br />

<br />