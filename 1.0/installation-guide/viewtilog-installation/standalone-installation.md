---
reusableId: 77
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Instalação Standalone'
id: OAK-P0VS-SIQ-GDI
slug: standalone-installation
isVisible: true
lastUpdated: '2025-10-15 10:18:48'
---
# **<span align="center">Instalação Standalone do Viewtilog</span>**

> **Nota:** Este capítulo aborda uma instalação **standalone** do Viewtilog.<br />
> Instalações de alta disponibilidade (cluster/H.A.) são descritas no Capítulo 2.

---

## **Pré-requisitos**

-   Uma instância em execução do Viewtinet Manager com acesso administrativo via GUI
-   Credenciais SSH para o host de destino (mesma máquina) onde o Viewtilog será instalado
-   Conectividade de rede entre o seu navegador e o Viewtinet Manager

---

## **Passo 1: Abrir o Módulo Viewtilog**

1.  Faça login no Viewtinet Manager como **admin**.
2.  No menu de navegação à esquerda, clique em **Viewtilog**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/CbrW5OtEwUlMXqpQYW4B.png" align="center"></figure>

---

## **Passo 2: Iniciar o Instalador de Conectores**

1.  Na página do Viewtilog, clique no botão **Instalar Conectores**.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/MPBJyXqcAbJCKATEUJce.png"></figure>
    

---

## **Passo 3: Adicionar o Host**

1.  No painel **Cluster para Conectores**, clique em **\+ Adicionar Novo Host**.
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/JFvIKa6lD5DOhSV6zIfC.png"></figure>
    
    <br />
    
2.  Como esta é uma instalação standalone, insira o **mesmo** endereço IP ou hostname desta máquina nos campos "Hostname ou Endereço IP" e "Hostname ou Endereço IP LAN".
3.  Nos campos **Senha** e **Confirmar Senha**, insira sua senha **SSH** para este host (não a senha admin da GUI).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/u4QKznxGBMKJjV6OSwKi.png" align="center"></figure>

<br />

---

## **Passo 4: Salvar e Confirmar**

1.  Clique em **Salvar Alterações**.
2.  Na caixa de diálogo de confirmação, revise o endereço IP de destino e clique em **OK**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/f2fGZb3SVYjEdRSVX5j6.png" align="center"></figure>

<br />
<br />

---

## **Passo 5: Acompanhar o Progresso da Instalação**

1.  O instalador começará a implantar os serviços de conector via Docker.
2.  Um log ao vivo será exibido mostrando ações como parar contêineres antigos, baixar imagens e criar novos serviços.
3.  Aguarde até ver a mensagem:

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/S11bPL8FbRAG072W3lL0.png" align="center"></figure>

---

## **Passo 6: Concluir a Instalação**

1.  Após o log chegar ao final, clique em **Finalizar Instalação**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/1SlW2r00ACE7o9H6OSj9.png" align="center"></figure>

---

**Resultado:** O Viewtilog está instalado em modo standalone e agora está disponível para executar suas tarefas ETL.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/VIc3sU4DPnY144IRqS4i.png"></figure>

<br />

<br />
