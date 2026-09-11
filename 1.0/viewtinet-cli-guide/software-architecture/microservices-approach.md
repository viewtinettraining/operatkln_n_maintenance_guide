---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Abordagem de Microsserviços'
id: OWE-SBWL-ZGV-PXH
slug: microservices-approach
isVisible: true
lastUpdated: '2025-10-15 15:56:46'
---
# **<span align="center">Arquitetura de Microsserviços</span>**

<span align="justify">O Viewtinet é construído sobre uma arquitetura baseada em microsserviços, onde cada módulo é composto por múltiplos contêineres Docker que executam funções específicas e isoladas. Esse design aprimora a escalabilidade, flexibilidade e desempenho, permitindo implantações modulares, solução de problemas simplificada e uso eficiente de recursos.</span>

## **Principais Benefícios da Abordagem de Microsserviços**

-   **Escalabilidade**: Os contêineres podem ser escalados independentemente com base na carga.
-   **Flexibilidade**: Os módulos podem ser atualizados ou reiniciados sem afetar o sistema inteiro.
-   **Isolamento de Falhas**: Erros em um contêiner não derrubam a plataforma completa.
-   **Otimização de Recursos**: Os serviços consomem apenas o que precisam.
-   **Implantação Independente**: Cada componente pode ser implantado, atualizado ou revertido independentemente.

## **Composição Modular**

Cada produto Viewtinet—**Viewtilog**, **Viewtimon** e **Viewtify QoS**—é composto por vários módulos, incluindo:

-   **Viewtimanager**: Gerencia a configuração, manipulação de plugins e orquestração de módulos.
-   **Viewtisight**: Fornece dashboards, relatórios e visualização de dados.
-   **Viewtiauth**: Gerencia autenticação e controle de acesso.
-   **Dhyana**: Implementa pipelines de ETL para coleta e transformação de dados.
-   **Viewticore**: Funciona como o data warehouse e motor de séries temporais.
-   **HA\_Proxy**: Gerencia o balanceamento de carga e serviços de proxy.
-   **License Checker**: Lida com a validação e aplicação de licenciamento.

## **Módulos de GUI e Seus Contêineres**

Cada módulo de GUI (ex.: Viewtimanager, Viewtiauth, Viewtisight) tipicamente inclui:

-   **Contêiner Frontend**: Apresenta a interface do usuário e lida com interações.
-   **Contêiner Backend**: Processa regras de negócios, autenticação ou tarefas de configuração.
-   **Contêiner MongoDB**: Armazena estado persistente, configuração ou preferências do usuário.

Essa separação permite uma arquitetura mais limpa e facilita a depuração ou manutenção de cada função dentro da plataforma.

<br />

## **Camadas de Processamento de Dados no Viewtilog (Dhyana)**

O módulo backend **Dhyana** segue um padrão clássico de microsserviço **ETL (Extract, Transform, Load)**:

-   **Camada de Extração**: Coleta dados de protocolos como SNMP, NetFlow, Syslog, ICMP, etc.
-   **Camada de Transformação**: Aplica filtros, conversões, processamento de regex e cálculos matemáticos.
-   **Camada de Carregamento**: Exporta dados para sistemas de destino em formatos como XDR, UDP, TCP ou bancos de dados personalizados.

Esse processamento baseado em pipeline é definido via arquivos XML e é altamente personalizável com base nas necessidades de rede e observabilidade.

<br />

## **Viewticore: O Motor Central de Dados**

**Viewticore** é o data warehouse de séries temporais que suporta:

-   Escalabilidade multinó e execução paralela de consultas
-   Políticas de retenção de dados
-   Funções SQL (GROUP BY, JOIN, ORDER BY, etc.)
-   Agregação, gerenciamento de alarmes e exportação de documentos (PDF)
-   Capacidades de cancelamento e otimização de consultas

---

A arquitetura de microsserviços no Viewtinet não apenas suporta fluxos de trabalho complexos de observabilidade e análise, mas também torna a plataforma altamente adaptável e fácil de gerenciar através de operações via CLI.