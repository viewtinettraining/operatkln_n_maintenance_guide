---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Funções'
id: W27-FT60-N0W-47N
slug: roles
isVisible: true
lastUpdated: '2025-10-15 15:30:41'
---
# **<span align="center">Funções (Roles)</span>**

O recurso de **Funções (Roles)** permite definir conjuntos de permissões personalizadas que controlam quais ações usuários e grupos podem realizar na plataforma Viewtinet. Uma vez criada uma função, você pode atribuí-la a usuários individuais ou a grupos de usuários, adaptando o acesso às funções e aos dados do sistema.

<br />

## **Acessando a Página de Funções**

1.  No menu à esquerda, clique em **Admin**.
2.  Selecione a aba **Roles**.
3.  Clique em **Add New** para criar uma nova função.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/16nOqMXyycj4FF5iFmKc.png" align="center"></figure>

<br />

## **Detalhes da Função (Role Details)**

No painel de **Detalhes da Função**, especifique:

<table><tbody><tr><th><p>Campo</p></th><th><p>Descrição</p></th></tr><tr><td><p><strong>Nome (Name)</strong></p></td><td><p>Um identificador exclusivo para a função (ex: <code>Administrador de Rede</code>).</p></td></tr><tr><td><p><strong>Descrição (Description)</strong></p></td><td><p>Um breve resumo do propósito da função ou caso de uso típico.</p></td></tr><tr><td><p><strong>Criado em (Created at)</strong></p></td><td><p>Carimbo de data/hora de quando a função foi criada (somente leitura).</p></td></tr><tr><td><p><strong>Atualizado em (Updated at)</strong></p></td><td><p>Carimbo de data/hora da modificação mais recente (somente leitura).</p></td></tr></tbody></table>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/BdwbLC0d8KYTorImhfu7.png"></figure>

<br />

## **Permissões da Função (Role Permissions)**

Use a interface de lista dupla para conceder ou revogar permissões granulares. Selecione na esquerda (“Available” - Disponíveis) e mova para a direita (“Selected” - Selecionadas).

<table><tbody><tr><th><p>Permissão</p></th><th><p>Descrição</p></th></tr><tr><td><p>VM_ADMIN_AUTH_FILTERED</p></td><td><p>Remove a aba <strong>Auth</strong> da área Admin</p></td></tr><tr><td><p>VM_ADMIN_AUTH_INTEGRATIONS_FILTERED</p></td><td><p>Filtra para permitir apenas a seção <strong>Integrations</strong> na aba Auth</p></td></tr><tr><td><p>VM_ADMIN_AUTH_ONLY</p></td><td><p>Remove todas as abas de Admin, exceto <strong>Auth</strong></p></td></tr><tr><td><p>VM_ADMIN_GROUPS_FILTERED</p></td><td><p>Remove a aba <strong>Groups</strong> da área Admin</p></td></tr><tr><td><p>VM_ADMIN_MODULE</p></td><td><p>Acesso ao módulo <strong>Admin</strong> do Viewtimanager</p></td></tr><tr><td><p>VM_ADMIN_ROLES_FILTERED</p></td><td><p>Remove a aba <strong>Roles</strong> da área Admin</p></td></tr><tr><td><p>VM_ADMIN_TENANTS_FILTERED</p></td><td><p>Remove a aba <strong>Tenants</strong> da área Admin</p></td></tr><tr><td><p>VM_ADMIN_USERS_FILTERED</p></td><td><p>Remove a aba <strong>Users</strong> da área Admin</p></td></tr><tr><td><p>VM_BACKEND_ACCESS</p></td><td><p>Acesso ao módulo de <strong>Acesso ao Backend (Backend Access)</strong></p></td></tr><tr><td><p>VM_CONFIGURATION_MANAGER_MODULE</p></td><td><p>Acesso ao módulo Configuration Manager</p></td></tr><tr><td><p>VM_DATA_SOURCES_MODULE</p></td><td><p>Acesso ao módulo <strong>Viewtilog</strong> / Data Sources</p></td></tr><tr><td><p>VM_DEVEL_ACCESS</p></td><td><p>Acesso a todo o Viewtimanager, incluindo áreas de P&D (R&amp;D)</p></td></tr><tr><td><p>VS_DEVEL_ACCESS</p></td><td><p>Acesso a todo o Viewtisight, incluindo recursos avançados</p></td></tr><tr><td><p>VM_FULL_ACCESS</p></td><td><p>Acesso total ao Viewtimanager (exceto P&D)</p></td></tr><tr><td><p>VS_FULL_ACCESS</p></td><td><p>Acesso total ao Viewtisight</p></td></tr><tr><td><p>VM_HOME_MODULE</p></td><td><p>Acesso ao <strong>Home</strong> do Viewtimanager</p></td></tr><tr><td><p>VM_INVENTORY_MODULE</p></td><td><p>Acesso ao módulo <strong>Inventory</strong> do Viewtimanager</p></td></tr><tr><td><p>VM_PLUGINS_MODULE</p></td><td><p>Acesso ao <strong>V.S. Data Broker</strong></p></td></tr><tr><td><p>VM_QOS_MODULE</p></td><td><p>Acesso ao módulo Viewtify QoS</p></td></tr><tr><td><p>VS_READ_ONLY</p></td><td><p>Acesso somente leitura a todo o Viewtisight</p></td></tr><tr><td><p>VS_READ_ONLY_ALARMS_NO_EVENTS</p></td><td><p>Viewtisight somente leitura, mas sem eventos de alarmes</p></td></tr><tr><td><p>VM_VIEWTIFYOPT_MODULE</p></td><td><p>Acesso ao módulo ViewtifyOpt</p></td></tr><tr><td><p>VM_VIEWTIMON_INSPECTORS</p></td><td><p>Permite modificar inspetores na aba Viewtimon</p></td></tr><tr><td><p>VM_VIEWTIMON_MODULE</p></td><td><p>Acesso ao módulo Viewtimon</p></td></tr><tr><td><p>VM_VIEWTISIGHT_MODULE</p></td><td><p>Acesso ao módulo Viewtisight</p></td></tr><tr><td><p>VS_NO_CONTROL_CENTER</p></td><td><p>Bloqueia o acesso ao Control Center (Alarmes e Notificações)</p></td></tr><tr><td><p>VM_NO_QOS_CONFIGURATION</p></td><td><p>Desabilita a visualização de configuração de QoS</p></td></tr><tr><td><p>VS_NO_SCHEDULER</p></td><td><p>Nega acesso ao Scheduler (Agendador)</p></td></tr></tbody></table>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/IiaX45FmMuHcHH0JgqkO.png" align="center"></figure>

<br />

## **Conjuntos da Função (Role Sets / Data Access)**

Em **Role Sets**, determine quais tabelas de banco de dados (“conjuntos”/sets) esta função pode consultar. Use a lista dupla para mover itens de **Allowed Sets** (Conjuntos Permitidos) para **Forbidden Sets** (Conjuntos Proibidos).

> **Nota de Personalização:** Quaisquer conjuntos colocados em **Forbidden Sets** não podem ser consultados por esta função, impedindo efetivamente o acesso a essas tabelas subjacentes ou métricas.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/L1mIRhGNajdFQj8D7DJu.png"></figure>

<br />

## **Grupos da Função (Role Groups)**

O painel **Role Groups** lista os grupos de usuários já associados a essa função. Você **não pode** modificar atribuições de grupo aqui — use **Admin → Groups** para adicionar ou remover essa função de qualquer grupo.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/gZFqOWNOMOunTeyzibRH.png" align="center"></figure>

<br />

## **Usuários da Função (Role Users)**

Da mesma forma, o painel **Role Users** mostra os usuários individuais que têm essa função. Para alterar associações de usuário-função, acesse **Admin → Users**.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/BU1hXhfGc2RO1AlvZiia.png" align="center"></figure>

<br />

**Lembre-se:** Depois de atualizar qualquer seção (Details, Permissions, Sets), clique em **Save Changes** na parte inferior da página para aplicar sua configuração.

<br />