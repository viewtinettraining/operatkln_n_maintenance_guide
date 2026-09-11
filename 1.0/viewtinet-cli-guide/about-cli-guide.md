---
reusableId: 43
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Sobre o Guia CLI'
id: 486-TZTP-0YW-J40
slug: about-cli-guide
isVisible: true
lastUpdated: '2025-10-15 15:56:20'
---
# **<span align="center">Introdução</span>**

<span align="justify">O Viewtinet é uma plataforma de observabilidade modular projetada para ser executada no Ubuntu Server (20.04 e 24.04), utilizando uma arquitetura de microsserviços orquestrada com Docker. Sua abordagem baseada em containers garante escalabilidade, gestão eficiente de recursos e manutenção simplificada.</span>

<span align="justify">Este guia é destinado a administradores de sistema, engenheiros de rede e pessoal de suporte que interagem com o Viewtinet por meio da interface de linha de comando (CLI). Fornece uma referência prática para realizar tarefas operacionais essenciais, incluindo:</span>

-   Monitoramento do status de serviços e containers
-   Acesso e análise de logs do sistema
-   Execução de scripts para backups, importação de dados e verificações do sistema
-   Solução de problemas e resolução de questões comuns
-   Atualização de toda a plataforma ou módulos individuais usando ferramentas CLI

O objetivo deste guia é simplificar o gerenciamento baseado em CLI de ambientes Viewtinet e fornecer instruções claras e acionáveis para apoiar as operações diárias.

Este guia se aplica às versões **6.3** e **6.3.5** do Viewtinet e é relevante para todas as linhas de produtos: **Viewtilog**, **Viewtimon** e **Viewtify QoS**.

---

### Convenções Utilizadas

-   `$` denota comandos a serem executados em uma sessão de shell
-   `&lt;argument&gt;` indica um marcador de posição a ser substituído por valores específicos do usuário
-   Os scripts podem exigir permissões elevadas (ex.: `sudo`), conforme indicado — embora a maioria seja projetada para ser executada diretamente pelo usuário `viewtinet`

Seguindo este guia, você poderá operar e manter eficientemente sua implantação do Viewtinet usando a CLI — seja realizando verificações de rotina, operações de módulos ou tarefas de manutenção completa do sistema, como atualizações.
