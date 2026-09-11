---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Usuários'
id: P4I-KSRN-3QJ-RPV
slug: users
isVisible: true
lastUpdated: '2025-10-15 15:33:55'
---
# **<span align="center">Contas de Usuário</span>**

<span align="justify">A página de Usuários (Users) do Viewtimanager permite criar, gerenciar e auditar contas de usuários locais — sejam eles administradores, analistas do Viewtisight ou operadores do Viewtilog. Siga as etapas abaixo para adicionar um novo usuário e configurar suas definições.</span>

<br />

## **1\. Navegar para a Página de Usuários**

1.  Na barra lateral esquerda, clique em **Admin**.
2.  Nas abas superiores, selecione **Users**.
3.  Clique em **\+ ADD NEW** na parte inferior da lista de usuários.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/uENnMqUEY27o9Qdbey8t.png" align="center"></figure>
    

## **2\. Inserir Detalhes Básicos do Usuário**

Preencha o formulário **User Details** (Detalhes do Usuário):

<table><tbody><tr><th><p>Campo</p></th><th><p>Descrição</p></th></tr><tr><td><p><strong>Nome de Usuário (Username)</strong></p></td><td><p>Nome de login exclusivo (ex: <code>jdoe</code>, <code>analista1</code>).</p></td></tr><tr><td><p><strong>Senha (Password)</strong></p></td><td><p>Deve atender à política de senhas seguras (veja abaixo).</p></td></tr><tr><td><p><strong>Repetir Senha (Repeat Password)</strong></p></td><td><p>Deve corresponder exatamente à Senha (Password).</p></td></tr><tr><td><p><strong>E-mail</strong></p></td><td><p>Endereço de e-mail do usuário (obrigatório para códigos de MFA).</p></td></tr><tr><td><p><strong>Inquilino (Tenant)</strong></p></td><td><p>Atribua um Tenant (Inquilino) se estiver usando o modo Multi-Tenant (veja <a href="#tenants" target="_self">Tenants</a>). Caso contrário, selecione seu inquilino padrão (ex: <code>Viewtinet</code>).</p></td></tr><tr><td><p><strong>Nome/Sobrenome (Name/Last Name)</strong></p></td><td><p>Opcional: campos de nome completo para referência.</p></td></tr></tbody></table>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/UEPNPtnqewIEN0PKcGew.png"></figure>

### **Política de Senhas:**

-   Mínimo de **12** caracteres
-   Pelo menos **1 dígito** (`0`–`9`)
-   Pelo menos **1 letra maiúscula** (`A`–`Z`)
-   Pelo menos **1 caractere especial** (`! " @ # $ % ^ & * ( )`)

---

## **3\. Configurar Sinalizadores da Conta (Account Flags)**

Abaixo dos campos principais estão várias caixas de seleção que controlam o comportamento de login:

<table><tbody><tr><th><p>Caixa de Seleção (Checkbox)</p></th><th><p>Efeito</p></th></tr><tr><td><p><strong>Two Factor Authentication (Autenticação de Dois Fatores)</strong></p></td><td><p>Envia um código de uso único por e-mail a cada login. Requer um E-mail e uma atribuição de Tenant (Inquilino) válidos.</p></td></tr><tr><td><p><strong>Password changed (Senha alterada)</strong></p></td><td><p><em>Desmarque</em> para forçar o usuário a alterar a senha no primeiro login. <em>Marque</em> para desativar esse prompt.</p></td></tr><tr><td><p><strong>Logged in (Logado)</strong></p></td><td><p>Indica se o usuário está logado no momento. <em>Desmarque</em> para desconectá-lo (logout) imediatamente.</p></td></tr><tr><td><p><strong>Session Never Expires (A sessão nunca expira)</strong></p></td><td><p><em>Marque</em> para conceder a este usuário uma sessão imortal (sem timeout automático).</p></td></tr></tbody></table>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Jto9BxEaHjIgf4eJ6qih.png"></figure>

<br />

## **4\. Atribuir Grupos de Usuário _(Opcional)_**

Grupos são uma conveniência organizacional — você pode atribuir usuários a um grupo para que depois você possa gerenciar suas funções (roles) em massa em vez de editar usuários um a um. Esta etapa é **opcional**.

1.  Expanda a seção **User Groups** (Grupos de Usuários).
2.  Selecione um ou mais grupos sob **Available** (Disponíveis).
3.  Clique em **&gt;** para movê-los para **Selected** (Selecionados).

## <br />
**5\. Atribuir Funções de Usuário _(Obrigatório)_**

As funções (roles) definem o que o usuário realmente **vê** e **pode fazer** na GUI. Cada usuário **deve** ter pelo menos uma função.

1.  Expanda a seção **User Roles** (Funções de Usuário).
2.  Selecione a(s) função(ões) desejada(s) em **Available** (Disponíveis).
3.  Clique em **&gt;** para movê-las para **Selected** (Selecionadas).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/WY8FBcwivBSRdjB2Yg7X.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/1lYcZMkWM1ce2BzRPLSf.png" align="center"></figure>

## **6\. Salvar o Novo Usuário**

Depois de configurar os detalhes, sinalizadores, grupos e funções, clique em **✔ SAVE CHANGES** na parte inferior do formulário. O novo usuário agora aparecerá na lista.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/SjJ6uLhOXU1DxhTKJrP0.png" align="center"></figure>

**Dicas:**

-   Grupos são opcionais — mas eles simplificam mudanças de função em massa: altere as funções de um grupo uma vez, e todos os seus membros herdam essas mudanças instantaneamente.
-   As funções são obrigatórias: sem uma função, um usuário não pode fazer login ou visualizar nenhum painel (dashboard).
-   Use o sinalizador "Logged in" para terminar imediatamente a sessão ativa de um usuário (por exemplo, após uma suspeita de vazamento de credenciais).
-   Limite o uso de "Session Never Expires" apenas a contas de serviço ou de máquina.<br />
    

**Nota:** Quando o Viewtinet é integrado ao Active Directory (AD) ou LDAP, os usuários podem ser **provisionados automaticamente** (auto-provisioned), o que significa que as contas são criadas automaticamente no primeiro login sem inserção manual aqui.

<br />