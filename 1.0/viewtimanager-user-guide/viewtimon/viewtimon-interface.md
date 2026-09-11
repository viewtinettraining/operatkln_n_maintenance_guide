---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'The Viewtimon Interface'
id: Y1G-L34-YR2-JHP
slug: viewtimon-interface
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:48:29'
---
# **<span align="center">A Interface do Viewtimon</span>**

<br />

O módulo **Viewtimon** fornece uma interface dedicada para gerenciar a sonda DPI, monitorar sua integridade e verificar seu desempenho.

> <div class="sd-callout" data-callout-type="info">A interface do Viewtimon nem sempre está ativa por padrão. O acesso a este módulo depende de o recurso Viewtimon estar devidamente licenciado em sua implantação.</div>

Para acessar esta interface, navegue até o menu principal à esquerda do Viewtimanager e clique em **Viewtimon**.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-menu.png" align="center"></figure>

<br />

---

## **Visão Geral e Controles do Módulo**

Ao entrar na seção do Viewtimon, você é recebido com a guia **STATUS**, que atua como o painel principal do módulo.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-performance.png" align="center"></figure>

<br />

### **Informações do Sistema e Controles**

No topo da página, o sistema fornece informações operacionais críticas e botões de controle para o mecanismo Viewtimon:

-   **Version:** Exibe a versão atualmente instalada do Viewtimon (por exemplo, `6.3.5.6369 (Revision)`), juntamente com um link para as **notas de lançamento** mais recentes.
-   **Uptime:** Mostra por quanto tempo o serviço do Viewtimon está em execução contínua sem interrupção.
-   **Botões de Controle (Canto Superior Direito):** Estes botões permitem gerenciar o estado do serviço do mecanismo:
    
    -   **STOP:** Interrompe o mecanismo DPI do Viewtimon.
    -   **RESTART:** Reinicia o serviço com segurança (útil após a aplicação de certas alterações de configuração).
    -   **START:** Inicia o mecanismo se ele estiver interrompido no momento.

### **Guias de Navegação**

Abaixo dos controles superiores, várias guias permitem navegar pelas diferentes áreas de configuração do Viewtimon:

-   **STATUS:** A visualização atual, mostrando o painel de desempenho.
-   **CONFIGURATION:** Para configurar interfaces de rede e parâmetros avançados do mecanismo.
-   **SIGNATURES:** Para gerenciar assinaturas de aplicativos DPI personalizadas ou atualizadas.
-   **BUSINESS GROUPS:** Para definir agrupamentos organizacionais para IPs e sub-redes.
-   **HOSTS LIST:** Exibe os hosts descobertos na rede.
-   **ISSUES:** Um registro de quaisquer avisos internos ou erros detectados pelo módulo.

---

## **Painel de Desempenho do Viewtimon**

A guia **STATUS** apresenta o painel **Viewtimon Performance**, que visualiza a integridade em tempo real e histórica da própria sonda (não o tráfego do usuário). Ele inclui os seguintes indicadores-chave:

-   **CPU Usage:** Monitora a carga de processamento do mecanismo DPI.
-   **Memory Usage:** Acompanha o consumo de RAM do módulo.
-   **IO Wait:** Exibe o tempo que a CPU passa aguardando operações de entrada/saída (por exemplo, gravação em disco), o que é crucial para identificar gargalos.

<br />

### **Configuração do Seletor de Tempo**

Para analisar o desempenho historicamente, você pode usar o robusto **Seletor de Tempo** localizado na parte superior do painel.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-time-selector.png" align="center"></figure>

<br />

Este seletor permite personalizar a visualização:

-   **Dashboard Dropdown:** Permite alternar para diferentes painéis de desempenho, se disponíveis.
-   **Start Date & End Date:** Define um intervalo de tempo personalizado exato.
-   **Time Shortcut:** Um menu suspenso rápido para selecionar períodos comuns (por exemplo, `Last day`, `Last 7 days`, `Last hour`).
-   **Granularity:** Ajusta a resolução dos pontos de dados nos gráficos (por exemplo, `5 minutes`, `1 hour`), permitindo uma análise refinada ou tendências de longo prazo mais suaves.
-   **Ícones de Controle:** Os botões à direita permitem atualizar os dados manualmente, bloquear o intervalo de tempo, habilitar a atualização automática ou acessar outras opções do painel.

---

## **Painéis de Integridade Adicionais**

Usando o **Dashboard Dropdown** no Seletor de Tempo, você pode acessar dois painéis especializados adicionais para analisar ainda mais a integridade e o desempenho da sonda:

<br />

<figure align="center" style="width:45%"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-dashboard-click.png" width="45%" align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-dashboard-dropdown.png" width="45%" align="center"></figure>

<br />

### **1\. Stages Monitoring**

Este painel exibe informações importantes sobre o funcionamento interno da sonda Viewtimon e seu pipeline de processamento de dados.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-stages-monitoring.png" align="center"></figure>

<br />

Ele inclui as seguintes métricas:

-   **Total Throughput:** A quantidade total de dados sendo processada internamente.
-   **Total Dropped Packets:** Identifica se algum pacote está sendo descartado pelo mecanismo.
-   **Total Deduplicated Packets:** Mostra os pacotes que foram identificados como duplicados e tratados adequadamente.
-   **Total Throughput by stage & Total Dropped Packets by stage:** Detalha a taxa de transferência e as perdas em todas as fases internas de processamento específicas do mecanismo (por exemplo, analyze, balancer, qos).

### **2\. Interface Statistics**

Este painel fornece uma visão clara das interfaces de rede físicas ou virtuais que o Viewtimon está monitorando.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-interface-statistics.png" align="center"></figure>

<br />

Ele destaca:

-   **Throughput:** O volume de tráfego medido diretamente no nível da interface.
-   **Input Packets:** O número total de pacotes recebidos pela interface.
-   **Packets with Errors:** O número de pacotes malformados ou corrompidos detectados.
-   **Packets missed:** Pacotes que a interface não conseguiu capturar, o que pode indicar gargalos de hardware ou picos de tráfego excessivos.

<br />