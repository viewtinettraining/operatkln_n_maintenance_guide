---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Standalone Installation'
id: OAK-P0VS-SIQ-GDI
slug: standalone-installation
isVisible: true
lastUpdated: '2025-10-15 10:18:48'
---
# **<span align="center">Instalação Autônoma (Standalone) do Viewtilog</span>**

> **Nota:** Este capítulo abrange uma instalação **autônoma** do Viewtilog.<br />
> As instalações de alta disponibilidade (cluster/H.A.) são descritas no Capítulo 2.

---

## **Pré-requisitos**

-   Uma instância em execução do Viewtinet Manager com acesso administrativo à GUI
-   Credenciais SSH para o host de destino (mesma máquina) onde o Viewtilog será instalado
-   Conectividade de rede entre seu navegador e o Viewtinet Manager

---

## **Etapa 1: Abrir o Módulo Viewtilog**

1.  Faça login no Viewtinet Manager como **admin**.
2.  No menu de navegação à esquerda, clique em **Viewtilog**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/CbrW5OtEwUlMXqpQYW4B.png" align="center"></figure>

---

## **Etapa 2: Iniciar o Instalador de Conectores**

1.  Na página do Viewtilog, clique no botão **Install Connectors** (Instalar Conectores).
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/MPBJyXqcAbJCKATEUJce.png"></figure>
    

---

## **Etapa 3: Adicionar o Host**

1.  No painel **Cluster for Connectors** (Cluster para Conectores), clique em **\+ Add New Host** (Adicionar Novo Host).
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/JFvIKa6lD5DOhSV6zIfC.png"></figure>
    
    <br />
    
2.  Como esta é uma instalação autônoma, insira o **mesmo** endereço IP ou nome de host desta máquina nos campos "Hostname or IP Address" e "LAN Hostname or IP Address".
3.  Nos campos **Password** (Senha) e **Password Confirm** (Confirmar Senha), insira sua senha **SSH** para este host (não a senha de administrador da GUI).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/u4QKznxGBMKJjV6OSwKi.png" align="center"></figure>

<br />

---

## **Etapa 4: Salvar e Confirmar**

1.  Clique em **Save Changes** (Salvar Alterações).
2.  Na caixa de diálogo de confirmação, revise o endereço IP de destino e clique em **OK**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/f2fGZb3SVYjEdRSVX5j6.png" align="center"></figure>

<br />
<br />

---

## **Etapa 5: Acompanhar o Progresso da Instalação**

1.  O instalador começará a implantar os serviços de conector via Docker.
2.  Um log ao vivo aparecerá mostrando ações como parada de contêineres antigos, download de imagens e criação de novos serviços.
3.  Aguarde até ver a mensagem:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/S11bPL8FbRAG072W3lL0.png" align="center"></figure>

---

## **Etapa 6: Concluir a Instalação**

1.  Quando o log chegar ao fim, clique em **Finish Installation** (Concluir Instalação).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/1SlW2r00ACE7o9H6OSj9.png" align="center"></figure>

---

**Resultado:** O Viewtilog está instalado no modo autônomo (standalone) e agora está disponível para executar suas tarefas de ETL.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/VIc3sU4DPnY144IRqS4i.png"></figure>

<br />

<br />