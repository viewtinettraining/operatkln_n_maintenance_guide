---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Inventory Maintenance'
id: WQN-ONVQ-FEA-IOR
slug: inventory-maintenance
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:57:18'
---
## **<span align="center"><span class="text-large">Funções de Manutenção do Inventário</span></span>**

<br />

<span align="justify">Além de provisionar dispositivos e credenciais, o recurso Inventory (Inventário) oferece poderosas capacidades de manutenção para manter seus dados limpos, organizados e adaptados às suas necessidades. Neste capítulo, você aprenderá a gerenciar colunas, mesclar ou excluir registros, exportar conjuntos de dados e realizar outras tarefas de manutenção para garantir que seu inventário permaneça preciso e acionável.</span>

## **Alternando Colunas Visíveis**

O seletor “Visible columns” (Colunas visíveis) permite que você controle quais atributos do dispositivo são exibidos na tabela do Inventory. Esses campos são definidos pelo seu método de provisionamento (importação via CSV, Autodescoberta ou entrada manual). Este **não** é o lugar para adicionar novas colunas — apenas para habilitar ou desabilitar as existentes.

<br />

1.  **Abrir o Seletor de Colunas<br />
    **Clique na seta suspensa (▾) ao lado de **Visible columns** acima da tabela de dispositivos.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/DY2Cg7yu4bKqgoTxWrn5.png" align="center"></figure>
    
    <br />
    
2.  **Habilitar ou Desabilitar Campos<br />
    **Na lista que aparece, basta marcar a caixa ao lado de qualquer coluna que deseja exibir ou desmarcar para ocultá-la. As colunas incluem atributos como `device`, `mac`, `oid_group_names`, `sw_version`, `sys_object_id`, `system_name`, etc.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/rtVWUP5HO07vwh8CGcYW.png" align="center"></figure>
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/xXeLFpEhNYLTZyWJkxhI.png" align="center"></figure>
    
    <br />
    
3.  **Salvar o Layout**<br />
    Por fim, clique em **Save Changes** (Salvar Alterações) para manter a configuração de colunas entre as sessões.

---

## **Adicionando Colunas Personalizadas**

<br />
Você pode estender o esquema do seu Inventory criando novas colunas personalizadas para capturar atributos de dispositivos além daqueles fornecidos por CSV, Autodescoberta ou provisionamento manual.

1.  **Abrir a Janela "Add New Column" (Adicionar Nova Coluna)**<br />
    Na visualização do Inventory, clique em **\+ Add New Column** ao lado da lista suspensa do seletor de colunas.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/nKy2hAosimX1vN0n1gFi.png" align="center"></figure>
    
    <br />
    
2.  **Definir a sua Coluna**<br />
    Na janela modal que aparece:
    
    -   **Name**: Insira uma chave única para a coluna (ex: `example_new_column2`, `rack_label`).
    -   **Copy values from another column** (opcional): Se desejar inicializar seu novo campo com dados de uma coluna existente, marque esta caixa e selecione a origem (ex: `system_name`).
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/emNG7WEfCgkev80asBxJ.png" align="center"></figure>
    
    <br />
    
3.  **Confirmar a Adição**<br />
    Clique em **OK**. A nova coluna aparecerá no final da sua tabela e no seletor "Visible columns":
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/SrtVIIkud1VqINFxJxxZ.png" align="center"></figure>
    
    <br />
    
4.  **Preencher ou Ajustar Valores**
    
    -   Se você copiou os valores na etapa 2, sua nova coluna já estará preenchida.
    -   Caso contrário, clique em **Apply to all** (Aplicar a todos) acima da coluna para definir um padrão ou edite as células individualmente.
5.  **Salvar o Layout**<br />
    Clique em **Save Changes** para manter a nova coluna e seu conteúdo entre as sessões.

> **Dica:** Colunas personalizadas são totalmente integradas — estão disponíveis para filtragem, edição em massa e exportação para CSV, assim como os campos embutidos.

---

## **Mesclando Linhas Duplicadas**

<br />

Quando várias linhas representam o mesmo dispositivo, você pode mesclá-las:

1.  Marque a caixa de seleção ao lado de cada linha duplicada.
2.  Clique em **Merge Duplicated Rows** (Mesclar Linhas Duplicadas) na barra de ferramentas.
3.  Confirme quais valores reter para cada coluna.
4.  Clique em **Merge** para consolidar em um único registro.

---

## **Excluindo Registros**

Para remover entradas obsoletas:

1.  Selecione uma ou mais linhas usando as caixas de seleção correspondentes.
2.  Clique em **Delete Selected Rows** (Excluir Linhas Selecionadas, ícone de lixeira).
3.  Confirme a exclusão no aviso.

---

## **Exportando o seu Inventário**

Você pode exportar qualquer visualização atual para CSV:

1.  Aplique filtros e ajuste as colunas conforme necessário.
2.  Clique em **Export** (Exportar) no canto superior direito da tabela de dispositivos.
3.  Baixe o arquivo CSV gerado.

---

## **Encontrando Plugins e Pipelines para um Dispositivo Específico**

Às vezes, você precisa saber exatamente quais plugins de monitoramento (e seus respectivos pipelines) estão coletando dados de um determinado dispositivo. A visualização do Inventory facilita isso:

1.  **Localizar o seu Dispositivo**<br />
    Em **Overview → Devices**, role a página ou filtre até chegar na linha desejada (ex: `10.10.10.1` ou `10.30.23.45`).<br />
    
2.  **Clicar no Ícone de Pesquisa no Nível do Dispositivo**<br />
    Na coluna mais à direita dessa linha, clique no ícone 🔍 **“Show plugins using this device”** (Mostrar plugins usando este dispositivo).
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/6YglcrKNtQFo78sql1bT.png"></figure>
    
    <br />
    
3.  **Ver os Filtros de Atribuição de Plugins**<br />
    Você será levado à aba **Plugins**, onde a caixa de filtro já estará preenchida com o IP do seu dispositivo. Somente os plugins atualmente vinculados àquele dispositivo serão listados.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/uXz7m93Ue00vaqnUqlNj.png"></figure>
    

---

## **Encontrando Dispositivos Associados a um Pipeline**

Se você precisar saber quais dispositivos do inventário estão vinculados a um pipeline de coleta de dados específico, siga estes passos:

1.  **Abrir a Visualização de Plugins**<br />
    Na tela do Inventory, clique na aba **Plugins**.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/FZCZO3yfmANnfZhKN1h8.png" align="center"></figure>
    
    <br />
    
2.  **Expandir o Plugin Desejado**<br />
    Encontre o plugin que contém seu pipeline (ex: **network monitoring**) e clique na seta ▶️ para exibir seus pipelines.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/oUqdKoqIxhHCDwKF8mHU.png" align="center"></figure>
    
3.  **Pesquisar na Linha do Pipeline**<br />
    Localize o pipeline que lhe interessa (ex: `snmp_device_config`) e clique no ícone 🔍 **“Show devices assigned to this pipeline”** (Mostrar dispositivos atribuídos a este pipeline) naquela linha.
    
    <br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/qYi87vjl83SdIacdY4aJ.png" align="center"></figure>
    
4.  **Ver a Lista de Dispositivos Filtrada**<br />
    Um seletor de dispositivos aparece, mostrando apenas as linhas correspondentes ao filtro do pipeline (ex: de “All devices” ou de um filtro personalizado como `dev.ip == '10.10.10.1'`). Você pode rolar a lista ou refiná-la usando a barra de pesquisa.<br />
    
    <img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/CkzMkmJlfIGDBui4/images/TlJWz6vwmnWoy25V77rM.png">
    
    <br />
    
5.  **Inspecionar ou Confirmar**
    
    -   Revise quais IPs/Hostnames, grupos de OID, versões do SNMP, etc., estão ativos.
    -   Quando terminar, clique em **OK** para fechar a lista de dispositivos.

> **Dica:** Use esse detalhamento sempre que quiser auditar ou solucionar problemas para ver exatamente quais ativos de rede um determinado pipeline de coleta está alvejando.

<br />
Com essas ferramentas, você pode manter um inventário enxuto e preciso, que reflita o verdadeiro estado da sua rede, tornando o monitoramento, a análise e a criação de relatórios subsequentes muito mais confiáveis.