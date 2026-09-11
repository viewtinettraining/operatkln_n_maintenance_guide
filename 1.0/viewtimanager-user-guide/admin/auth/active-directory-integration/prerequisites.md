---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Pré-requisitos'
id: CHL-R7JE-YJF-9EG
slug: prerequisites
isVisible: true
lastUpdated: '2025-10-15 15:38:04'
---
# **<span align="center">Pré-requisitos</span>**

<span align="justify">A integração do Viewtimanager com o Active Directory requer configurações específicas para garantir a autenticação e o gerenciamento de usuários sem problemas. Este capítulo descreve os pré-requisitos necessários, incluindo permissões de usuário, requisitos de rede e detalhes de configuração.</span>

<br />

## **1\. Requisitos da Conta de Usuário do Active Directory**

Para conectar o Viewtimanager ao Active Directory, uma conta de usuário dedicada deve ser criada no domínio. Esta conta deve ter as seguintes propriedades:

-   **Nome de Usuário:** Uma conta de serviço exclusiva (ex: `viewtinet_user`).
-   **Permissões:** Acesso de leitura à estrutura do Active Directory para recuperar informações de usuários e grupos.
-   **Escopo do Domínio:** Garanta que a conta tenha acesso às Unidades Organizacionais (OUs) necessárias onde os usuários estão armazenados.
-   **Senha que não Expira:** Recomenda-se configurar a conta com uma senha que não expira para evitar falhas de autenticação.

## **2\. Requisitos de Rede e Firewall**

As seguintes portas devem estar abertas para a comunicação adequada entre o Viewtimanager e o servidor Active Directory:

-   **TCP 389:** Porta LDAP padrão para consultas de diretório (modo inseguro).
-   **TCP 636:** Porta LDAPS padrão para consultas de diretório (modo seguro).

## **3\. Considerações sobre a Estrutura do Active Directory**

-   Certifique-se de que os usuários e grupos necessários estejam localizados em uma Unidade Organizacional (OU) ou grupo conhecido para facilitar o gerenciamento.
-   Se o Controle de Acesso Baseado em Funções (RBAC) estiver sendo implementado, predefina os grupos de segurança que serão mapeados para as diferentes funções do Viewtimanager.

## **4\. Informações do Controlador de Domínio**

Reúna os seguintes detalhes antes de iniciar a integração:

-   **Nome do Domínio:** (ex: `viewtinet.local`)
-   **IP ou Hostname do Controlador de Domínio:** (ex: `10.30.23.8 ou dc01.viewtinet.local`)
-   **Base DN (Nome Distinto):** (ex: `DC=viewtinet,DC=local`)
-   **Bind DN (DN da Conta de Serviço):** (ex: `CN=viewtinet_user,DC=viewtinet,DC=local`)

<div class="sd-callout" data-callout-type="info"><span align="justify">A estrutura do usuário de serviço, incluindo seus grupos e Unidades Organizacionais (OUs), apresentada neste manual é apenas para fins informativos e não representa uma configuração obrigatória. Cada empresa deve manter seus usuários, grupos e OUs de acordo com suas próprias políticas e requisitos. No entanto, é obrigatório que o usuário de serviço tenha permissões de leitura na árvore do Active Directory, pois isso é necessário para realizar o mapeamento entre usuários e grupos dentro da plataforma.</span></div>

## **5\. Sincronização de Tempo**

Tanto o Viewtimanager quanto o servidor Active Directory devem ter configurações de tempo sincronizadas para evitar falhas de autenticação devido à diferença de tempo.

<br />

### **Próximos Passos**

Assim que esses pré-requisitos forem atendidos, o próximo capítulo o guiará pelo processo passo a passo de configuração do Viewtimanager para se integrar ao Active Directory, incluindo a atribuição de funções para modificar o comportamento da interface gráfica com base nas permissões do usuário.

<br />