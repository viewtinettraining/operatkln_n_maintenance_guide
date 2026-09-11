---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Sobre o Guia CLI'
id: 486-TZTP-0YW-J40
slug: about-cli-guide
isVisible: true
lastUpdated: '2025-10-15 15:56:20'
---
# **<span align="center">Introdução</span>**

<span align="justify">O Viewtinet é uma plataforma de observabilidade modular projetada para rodar no Ubuntu Server (20.04 e 24.04), aproveitando uma arquitetura de microsserviços orquestrada com Docker. Sua abordagem baseada em contêineres garante escalabilidade, gerenciamento eficiente de recursos e manutenção simplificada.</span>

<span align="justify">Este guia destina-se a administradores de sistemas, engenheiros de rede e pessoal de suporte que interagem com o Viewtinet através da interface de linha de comando (CLI). Ele fornece uma referência prática para realizar tarefas operacionais essenciais, incluindo:</span>

-   Monitorar o status de serviços e contêineres
-   Acessar e analisar logs do sistema
-   Executar scripts para backups, importações de dados e verificações do sistema
-   Solucionar problemas e resolver questões comuns
-   Atualizar a plataforma inteira ou módulos individuais usando ferramentas de CLI

O objetivo deste guia é simplificar o gerenciamento baseado em CLI de ambientes Viewtinet e fornecer instruções claras e acionáveis para apoiar as operações do dia a dia.

Este guia se aplica às versões **6.3** e **6.3.5** do Viewtinet e é relevante para todas as linhas de produtos: **Viewtilog**, **Viewtimon** e **Viewtify QoS**.

---

### Convenções Utilizadas

-   `$` denota comandos a serem executados em uma sessão de shell
-   `&lt;argument&gt;` indica um espaço reservado para ser substituído por valores específicos do usuário
-   Os scripts podem exigir permissões elevadas (por exemplo, `sudo`), conforme observado — embora a maioria seja projetada para ser executada diretamente pelo usuário `viewtinet`

Ao seguir este guia, você será capaz de operar e manter de forma eficiente sua implantação do Viewtinet usando a CLI — seja realizando verificações de rotina, operações de módulo ou tarefas de manutenção de sistema completo, como atualizações.