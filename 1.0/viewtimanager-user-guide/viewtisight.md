---
reusableId: 97
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtisight'
id: PAF-Y9JF-H1W-92Y
slug: viewtisight
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:49:05'
---
# **<span align="center">Viewtisight</span>**

## **Introdução**

<span align="justify">A partir do Viewtimanager, a seção Viewtisight fornece controle administrativo sobre o módulo Viewtisight — o mecanismo de visualização e painéis (dashboards) da plataforma Viewtinet. Esta interface não permite que os usuários interajam diretamente com os painéis; em vez disso, ela permite que os administradores do sistema:</span>

-   <span align="justify">Monitorem a integridade e o desempenho do serviço Viewtisight.</span>
-   <span align="justify">Iniciem, parem ou reiniciem o módulo.</span>
-   <span align="justify">Configurem parâmetros do servidor e notificações por e-mail.</span>
-   <span align="justify">Gerenciem os nós do cluster.</span>
-   <span align="justify">Revisem avisos, erros e problemas operacionais.</span>

---

## **🖥️ Acessando o Painel de Administração do Viewtisight**

<br />

<div class="sd-callout" data-callout-type="info">A interface do Viewtisight nem sempre está ativa por padrão. O acesso a este módulo depende de o recurso Viewtisight estar devidamente licenciado em sua implantação.</div>

<br />

Para acessar a interface de administração do Viewtisight:

1.  Faça login no **Viewtimanager**.
2.  No menu de navegação à esquerda, clique em **Viewtisight** (ícone: gráfico de barras).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/YOhFgObKsSOcxLdgQBYj.png" align="center"></figure>

Você será redirecionado para o painel de gerenciamento do Viewtisight, que inclui informações do módulo e várias guias para controle operacional.

---

## **🧭 Visão Geral da Interface**

Na parte superior da tela, os seguintes controles gerais e informações estão sempre visíveis:

-   **Informações da Versão (Version Info)**: Exibe a versão e revisão atual (por exemplo, `6.3.5.3966 - Revision b11b8118`).
-   **Tempo de Atividade (Uptime)**: Mostra há quanto tempo o módulo está em execução.
-   **Botões de Controle do Módulo**:
    
    -   🔴 `STOP`
    -   🟠 `RESTART`
    -   🟢 `START`

### Guias Disponíveis:

-   `STATUS`: Monitorar uso de recursos (CPU, memória, IO).
-   `CONFIGURATION`: Editar portas de rede e configurações de e-mail SMTP.
-   `HOSTS LIST`: Gerenciar a configuração do cluster.
-   `ISSUES`: Visualizar alertas ativos e problemas do sistema.

---

## **Guia Status**

A guia Status fornece métricas de desempenho em tempo real do serviço Viewtisight:

-   **Uso de CPU**: Gráfico de linha com percentual de utilização da CPU.
-   **Uso de Memória**: Consumo de RAM atual e tendência histórica.
-   **E/S de Disco**: Taxas de leitura e gravação.

<br />

## **Guia Configuração**

Permite ajustar parâmetros bsicos de operação:

-   Porta HTTP / HTTPS de atendimento
-   Servidor SMTP de envio de alertas e relatórios
-   Endereço de e-mail de remetente e destinatários padrão

---

## **✅ Resumo**

A seção Viewtisight no Viewtimanager é o ponto central para operadores garantirem a disponibilidade e saúde do mecanismo analítico e de painéis da plataforma Viewtinet.
