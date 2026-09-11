---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtilog'
id: J5H-53DD-UC3-YS6
slug: viewtilog
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:55:21'
---
# **<span align="center">Viewtilog</span>**

<span align="justify">O módulo Viewtilog ingere, analisa sintaticamente (parseia) e armazena logs dos seus dispositivos de rede e segurança. Ele é executado em um ou mais coletores Dhyana e envia os dados de log para a plataforma Viewtinet para análise, visualização e emissão de alertas.</span>

> **Pré-requisito**<br />
> Certifique-se de ter instalado e configurado seu(s) coletor(es) Dhyana de acordo com o capítulo **Viewtilog** do Guia de Instalação antes de adicioná-los aqui.

---

## **Status**

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/N9dvqudCh7Kzg0Sm12uC.png" align="center"></figure>

-   **Versão (Version)**: ex.: `6.3.5.3966 (Revision aaf37d89)`
-   **Tempo de Atividade (Uptime)**: Tempo desde que o serviço ViewtILog foi iniciado.
-   **Controles (Controls)**:
    
    -   **Stop**: Encerra os conectores de forma segura.
    -   **Restart**: Reinicia o serviço sem alterar a configuração.
    -   **Start**: (Desativado quando em execução) Inicia o serviço se estiver parado.

---

## **Configuração (Configuration)**

> **Nota**: Todas as configurações nesta guia são aplicadas **automaticamente** durante a instalação do módulo.
> 
> <br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/oqmHfYqHNcLFKPj7YzpL.png" align="center"></figure>

<br />

-   **Diretório Principal (Main directory)**: Caminho onde o coletor Dhyana armazena os arquivos de log recebidos (ex.: `/opt/vn/dhyana/`).
-   **Tempo do Watchdog (segundos)**: Intervalo para verificações internas de integridade (padrão `60`).

---

## **Lista de Hosts (Hosts List)**

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/lxgxyxBtwxuO9Ig5GhvI.png" align="center"></figure>

Define quais coletores Dhyana alimentam logs no Viewtilog.

1.  **Cluster para Conectores**
    
    -   **Modo de alta disponibilidade (HA mode)**
        
        -   **Sem HA (No HA)** se apenas um host for definido.
        -   **HA** aplica-se quando dois ou mais hosts estão presentes com endereços virtuais.
2.  **Endereços Virtuais do Cluster** (opcional)<br />
    Clique em **+ Add New Virtual Address** para definir um IP flutuante para HA.
3.  **Lista de Hosts do Cluster**
    
    -   **+ Add New Host**: Cria uma nova linha em branco.
    -   Informe para cada coletor:
        
        -   **Hostname ou Endereço IP** (plano de gerenciamento)
        -   **Hostname ou Endereço IP da LAN** (plano de dados)
        -   **Senha** e **Confirmação de Senha** (credenciais SSH do usuário `viewtinet`)
    -   Clique em **Save Changes** para aplicar.

> **Nota**: A instalação e o ajuste dos coletores são abordados no capítulo **Instalação em Cluster do Viewtilog** do Guia de Instalação.

---

## **Problemas (Issues)**

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/g2jfllBnhjXkYQ356sL9.png" align="center"></figure>

Todos os avisos e erros operacionais dos conectores do Viewtilog:

-   **Data/Hora (Timestamp)**: Quando o evento foi registrado.
-   **Nível (Level)**: `warning`, `error`, etc.
-   **Mensagem (Message)**: Descrição detalhada (ex.: adições de chaves de host, falhas de conexão).

Controles:

-   **Show archived**: Alterna para incluir entradas arquivadas.
-   **Archive Page**: Arquiva manualmente a lista atual.

---

> **Reinicialização Após Alterações**<br />
> Se você atualizar hosts ou endereços virtuais, use o botão **Restart** na guia **Status** para aplicar as alterações sem esperar pelo próximo reinício automático.

<br />
