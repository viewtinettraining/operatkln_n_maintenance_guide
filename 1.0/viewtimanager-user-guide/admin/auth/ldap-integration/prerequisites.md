---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Pré-requisitos'
id: TC5-RB9Y-U44-GEU
slug: prerequisites
isVisible: true
lastUpdated: '2025-10-15 15:41:10'
---
# **<span align="center">Pré-requisitos</span>**

<span align="justify">A integração do Viewtimanager com o Servidor LDAP requer configurações específicas para garantir a autenticação e o gerenciamento de usuários sem problemas. Este capítulo descreve os pré-requisitos necessários, incluindo permissões de usuário, requisitos de rede e detalhes de configuração.</span>

<br />

## **1\. Requisitos da Conta de Usuário LDAP**

Para conectar o Viewtimanager ao Servidor LDAP, uma conta de usuário dedicada deve ser criada no domínio. Esta conta deve ter as seguintes propriedades:

-   **Nome de Usuário:** Uma conta de serviço exclusiva (ex: `viewtinet_user`).
-   **Permissões:** Acesso de leitura à estrutura de árvore do LDAP para recuperar informações de usuários e grupos.
-   **Senha que não Expira:** Recomenda-se configurar a conta com uma senha que não expira para evitar falhas de autenticação.
    
    <br />
    

## **2\. Requisitos de Rede e Firewall**

As seguintes portas devem estar abertas para a comunicação adequada entre o Viewtimanager e o servidor LDAP:

-   **TCP 389:** Porta LDAP padrão para consultas de diretório (modo inseguro).
-   **TCP 636:** Porta LDAPS padrão para consultas de diretório (modo seguro).
    
    <br />
    

## **3\. Informações do Servidor LDAP**

Reúna os seguintes detalhes antes de iniciar a integração:

-   **Nome do Domínio:** (ex: `viewtinet.local`)
-   **Endereço IP do Servidor LDAP:** (ex: `10.30.23.8 ou dc01.viewtinet.local`)
-   **Base DN (Nome Distinto):** (ex: `DC=viewtinet,DC=local`)
-   **Admin Access DN (DN da Conta de Serviço):** (ex: `CN=viewtinet_user,DC=viewtinet,DC=local`)
    
    <br />
    

## **4\. Sincronização de Tempo**

Tanto o Viewtimanager quanto o servidor LDAP devem ter configurações de tempo sincronizadas para evitar falhas de autenticação devido à diferença de tempo.

<br />

## **5\. Função por Padrão**

Ao contrário da integração com o Active Directory, esta versão não suporta o mapeamento de grupos do AD para funções específicas do Viewtinet. Os usuários LDAP serão provisionados automaticamente com uma única função padrão no primeiro login. Você pode usar uma das funções predefinidas ou, se uma função específica for necessária, criá-la seguindo os passos na seção Roles do Guia do Usuário do Viewtimanager.

<br />

### **Próximos Passos**

<span align="justify">Assim que esses pré-requisitos forem atendidos, o próximo capítulo o guiará pelo processo passo a passo de configuração do Viewtimanager para se integrar ao Servidor LDAP, incluindo a atribuição de funções para modificar o comportamento da interface gráfica com base nas permissões do usuário.</span>

<br />