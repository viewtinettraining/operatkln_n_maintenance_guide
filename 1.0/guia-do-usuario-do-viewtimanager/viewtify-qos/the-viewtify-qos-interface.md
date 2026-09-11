---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'A Interface do Viewtify QoS'
id: 6LX-142J-70R-L8Y
slug: the-viewtify-qos-interface
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 11:21:57'
---
# **<span align="center">A Interface Viewtify QoS</span>**

<br />

O módulo **Viewtimon** fornece uma interface dedicada para gerenciar a sonda DPI, monitorar sua integridade e verificar seu desempenho.

> <div class="sd-callout" data-callout-type="info">A interface Viewtify QoS não está sempre ativa por padrão. O acesso a este módulo depende do recurso Viewtify estar devidamente licenciado em sua implantação.</div>

Para acessar esta interface, navegue até o menu principal à esquerda do Viewtimanager e clique em **Viewtify QoS**.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/BKNRu3WdHr3rx4iT0YuP.png" align="center"></figure>

<br />

---

## **Visão Geral do Módulo e Controles**

Ao entrar na seção Viewtimon, você é recebido com a aba **STATUS**, que atua como o painel principal do módulo.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-performance.png" align="center"></figure>

<br />

### **Informações do Sistema & Controles**

No topo da página, o sistema fornece informações operacionais críticas e botões de controle para o motor Viewtimon:

-   **Version:** Exibe a versão atualmente instalada do Viewtimon (ex., `6.3.5.6369 (Revision)`), junto com um link para as últimas **notas de lançamento** (release notes).
-   **Uptime:** Mostra há quanto tempo o serviço Viewtimon está rodando continuamente sem interrupção.
-   **Botões de Controle (Canto Superior Direito):** Estes botões permitem gerenciar o estado do serviço do motor:
    
    -   **STOP:** Interrompe o motor DPI do Viewtimon.
    -   **RESTART:** Reinicia o serviço com segurança (útil após aplicar certas alterações de configuração).
    -   **START:** Inicia o motor se ele estiver parado no momento.

### **Abas de Navegação**

Abaixo dos controles superiores, várias abas permitem navegar pelas diferentes áreas de configuração do Viewtimon:

-   **STATUS:** A visualização atual, mostrando o painel de desempenho.
-   **CONFIGURATION:** Para configurar interfaces de rede e parâmetros avançados do motor.
-   **SIGNATURES:** Para gerenciar assinaturas de aplicativos DPI personalizadas ou atualizadas.
-   **BUSINESS GROUPS:** Para definir agrupamentos organizacionais para IPs e sub-redes.
-   **HOSTS LIST:** Exibe hosts descobertos na rede.
-   **ISSUES:** Um registro de quaisquer avisos ou erros internos detectados pelo módulo.

---

## **Painel de Desempenho do Viewtimon**

A aba **STATUS** apresenta o painel **Viewtimon Performance**, que visualiza a integridade em tempo real e histórica da própria sonda (não o tráfego do usuário). Ele inclui os seguintes indicadores principais:

-   **CPU Usage:** Monitora a carga de processamento do motor DPI.
-   **Memory Usage:** Rastreia o consumo de RAM do módulo.
-   **IO Wait:** Exibe o tempo que a CPU gasta esperando por operações de entrada/saída (ex., gravar no disco), o que é crucial para identificar gargalos.

<br />

### **Configuração do Seletor de Tempo**

Para analisar o desempenho historicamente, você pode usar o robusto **Seletor de Tempo** (Time Selector) localizado na parte superior do painel.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-time-selector.png" align="center"></figure>

<br />

Este seletor permite personalizar a visualização:

-   **Menu Suspenso do Painel (Dashboard Dropdown):** Permite alternar para diferentes painéis de desempenho, se disponíveis.
-   **Data de Início & Data de Término (Start Date & End Date):** Define um intervalo de tempo personalizado exato.
-   **Atalho de Tempo (Time Shortcut):** Um menu suspenso rápido para selecionar períodos comuns (ex., `Last day`, `Last 7 days`, `Last hour`).
-   **Granularidade (Granularity):** Ajusta a resolução dos pontos de dados nos gráficos (ex., `5 minutes`, `1 hour`), permitindo uma análise refinada ou tendências de longo prazo mais suaves.
-   **Ícones de Controle (Control Icons):** Os botões à direita permitem atualizar os dados manualmente, bloquear o intervalo de tempo, ativar a atualização automática ou acessar outras opções do painel.

---

## **Painéis de Integridade Adicionais**

Usando o **Menu Suspenso do Painel** no Seletor de Tempo, você pode acessar dois painéis especializados adicionais para analisar ainda mais a integridade e o desempenho da sonda:

<br />

<figure align="center" style="width:45%"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-dashboard-click.png" width="45%" align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-dashboard-dropdown.png" width="45%" align="center"></figure>

<br />

### **1\. Monitoramento de Estágios (Stages Monitoring)**

Este painel exibe informações importantes sobre o funcionamento interno da sonda Viewtimon e seu pipeline de processamento de dados.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-stages-monitoring.png" align="center"></figure>

<br />

Ele inclui as seguintes métricas:

-   **Total Throughput:** A quantidade total de dados sendo processada internamente.
-   **Total Dropped Packets:** Identifica se algum pacote está sendo descartado pelo motor.
-   **Total Deduplicated Packets:** Mostra pacotes que foram identificados como duplicados e tratados de acordo.
-   **Total Throughput by stage & Total Dropped Packets by stage:** Detalha a taxa de transferência e os descartes nos estágios específicos de processamento interno do motor (ex., analyze, balancer, qos).

### **2\. Estatísticas de Interface (Interface Statistics)**

Este painel fornece uma visão clara das interfaces de rede físicas ou virtuais que o Viewtimon está monitorando.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-interface-statistics.png" align="center"></figure>

<br />

Ele destaca:

-   **Throughput:** O volume de tráfego medido diretamente no nível da interface.
-   **Input Packets:** O número total de pacotes recebidos pela interface.
-   **Packets with Errors:** O número de pacotes malformados ou corrompidos detectados.
-   **Packets missed:** Pacotes que a interface não conseguiu capturar, o que pode indicar gargalos de hardware ou picos excessivos de tráfego.

<br />