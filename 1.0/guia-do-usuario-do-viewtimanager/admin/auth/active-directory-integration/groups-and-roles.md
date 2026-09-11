---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Grupos e Funções'
id: 0QA-TLZ4-4U4-TO8
slug: groups-and-roles
isVisible: true
lastUpdated: '2025-10-15 15:39:00'
---
# **<span align="center">Grupos do AD e Funções do Viewtinet</span>**

<br />

<span align="justify">Este capítulo o guiará através do processo de criação e mapeamento de funções no Viewtimanager, as quais serão vinculadas a grupos em seu Active Directory. Embora a configuração e preparação do Active Directory estejam fora do escopo deste guia, é importante observar que os grupos apropriados já devem existir em seu diretório. Ao configurar funções no Viewtimanager e mapeá-las para esses grupos pré-existentes, você garante que os usuários recebam as permissões e o acesso corretos dentro da interface do Viewtimanager, alinhados com suas funções organizacionais.</span>

Para os propósitos deste guia, uma Unidade Organizacional (OU) chamada **"Viewtinet\_Users"** foi criada no Active Directory. Dentro desta OU, três grupos foram definidos para gerenciar o acesso de usuários no Viewtimanager:

-   **Admins\_Viewtinet**: Este grupo inclui usuários administradores com acesso total ao Viewtimanager e ao Viewtisight.
-   **ReadOnly\_Viewtinet**: Este grupo consiste em usuários com acesso somente leitura ao Viewtisight, sem permissões para criar painéis (dashboards).
-   **Viewtisight\_Viewtinet**: Este grupo contém usuários com acesso administrativo ao Viewtisight, mas sem acesso ao Viewtimanager.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/xEEtWoUK537P4eDPCSbj.png" align="center"></figure>

<br />

## **FUNÇÕES (ROLES)**

<span align="justify">As funções definem as permissões e os níveis de acesso que os usuários têm dentro da plataforma. Elas determinam quais ações um usuário pode realizar, quais módulos ele pode acessar e como ele pode interagir com os diferentes recursos. As funções podem ser personalizadas para se alinharem às políticas de segurança de uma organização, garantindo que os usuários tenham acesso apenas às funcionalidades relevantes para suas responsabilidades. Além disso, as funções podem ser mapeadas para grupos do Active Directory, permitindo a integração perfeita com as estruturas de gerenciamento de usuários existentes.</span>

<br />

<span align="justify">Como primeiro passo, você deve estar logado com o usuário administrador ou um usuário com permissões administrativas no </span> Viewtimanager em `http://x.x.x.x:5000` (modo inseguro) ou `https://x.x.x.x:50001` (modo seguro), onde `x.x.x.x` é o endereço IP de gerenciamento do Viewtimanager.

<br />

Para criar uma função, clique no menu **Admin**, navegue até a seção **Details** e insira as informações necessárias para a função que deseja criar. O nome da função deve corresponder ao grupo do Active Directory ao qual você deseja mapeá-la.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/neD5NA2oab2gjjq8pGMW.png"></figure>

<div class="sd-callout" data-callout-type="info">Existem duas permissões predefinidas: VS_FULL_ACCESS e VM_FULL_ACCESS, que concedem acesso total a todos os elementos da GUI. Todos os outros elementos podem ser selecionados para criar funções com acesso personalizado à GUI.</div>

A seção 'Role Permissions' permite atribuir ou filtrar a visibilidade de elementos na GUI.

As permissões são estruturadas como: **_Módulo\_Menu\_Aba\_Permissão_**, onde:

-   Módulo
    
    -   VM = Viewtimanager
    -   VS = Viewtisight
-   Menu: O menu do Viewtimanager ou do Viewtisight onde a permissão será aplicada
-   Aba: Isso se aplica exclusivamente ao Viewtimanager e se refere a seções dentro dos menus.
-   Permissão: Define a permissão a ser aplicada. Aparecerá apenas quando o acesso à aba for negado, indicado pela palavra 'FILTERED'. Se a palavra 'FILTERED' não estiver presente, o acesso é permitido.

Para este exemplo, atribuiremos as permissões VS\_FULL\_ACCESS e VM\_FULL\_ACCESS à função, pois ela está sendo mapeada para o grupo Admins\_Viewtinet

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/aeLT3nKo3m8nJDcaYJRr.png" align="center"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/P3b4vMMTPpkTkFIgr8y5.png"></figure>

Por fim, salvaremos as alterações clicando no botão 'SAVE'

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/KOFw115qHO2WRtmUUDOS.png" align="center"></figure>

Para cada grupo definido no Active Directory, será necessário criar uma função seguindo o processo indicado e atribuindo as permissões necessárias para cada caso

<br />

Para fins de demonstração, as três funções que mapeiam os grupos do Active Directory foram criadas conforme mostrado abaixo:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/miwrxO52RXzDr4JqNJw0.png" align="center"></figure>

A função 'ReadOnly\_Viewtinet' tem a permissão VS\_READ\_ONLY atribuída, o que concede acesso apenas ao módulo Viewtisight, sem a capacidade de criar painéis (dashboards)

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/gtU8Kj35k8qmxCqp1a2Q.png" align="center"></figure>

<br />

Enquanto isso, a função 'Viewtisight\_Viewtinet' tem a permissão VS\_FULL\_ACCESS, que concede acesso apenas ao módulo Viewtisight com permissão para criar painéis (dashboards)

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/nDag22GB9Wd85nutrc0V.png" align="center"></figure>

<br />