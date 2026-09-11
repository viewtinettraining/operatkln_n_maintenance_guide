---
reusableId: 46
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Estrutura de Diretórios'
id: MUJ-O5K1-50I-SFY
slug: directory-structure
isVisible: true
lastUpdated: '2025-10-15 15:57:45'
---
# **<span align="center">Visão Geral da Estrutura de Diretórios</span>**

A plataforma Viewtinet é instalada no diretório `/opt/vn/`, que serve como local central para todos os arquivos de configuração, serviços, scripts e componentes em tempo de execução. Esse layout estruturado permite que administradores de sistema e operadores localizem e gerenciem facilmente os recursos associados a cada módulo da plataforma.

Entender a finalidade de cada diretório é essencial ao trabalhar pela CLI, especialmente para tarefas como:

-   Executar ou revisar scripts de manutenção
-   Inspecionar configurações ou logs específicos de módulos
-   Gerenciar atualizações e implantações

A estrutura de diretórios é consistente entre as implantações e se aplica a todas as linhas de produtos Viewtinet, incluindo **Viewtilog**, **Viewtimon** e **Viewtify QoS**.

Nas seções abaixo, cada diretório será explicado em detalhes, incluindo sua função no sistema e as considerações operacionais relevantes.

## **Descrição dos Diretórios**

<br />

<table><tbody><tr><th><p><strong><span align="center">Diretório</span></strong></p></th><th><p><strong><span align="center">Descrição</span></strong></p></th></tr><tr><td><p><code>ssl/</code></p></td><td><p>Contém certificados SSL/TLS e arquivos relacionados usados para proteger as comunicações entre módulos.</p></td></tr><tr><td><p><code>viewtinet-builder/</code></p></td><td><p>Inclui scripts e utilitários para instalar, atualizar e reiniciar módulos do Viewtinet.</p></td></tr><tr><td><p><code>software/</code></p></td><td><p>Armazena as imagens Docker usadas pela plataforma.</p></td></tr><tr><td><p><code>config/</code></p></td><td><p>Diretório central de configuração para os módulos do Viewtinet. Inclui configurações globais e específicas de cada módulo.</p></td></tr><tr><td><p><code>scripts/</code></p></td><td><p>Scripts executáveis personalizados usados para tarefas operacionais como backup, restauração, importação ou diagnóstico.</p></td></tr><tr><td><p><code>configuration-manager/</code></p></td><td><p>Contém arquivos de configuração e recursos para o recurso <code>configuration-manager</code>. Gerencia configurações centralizadas e sincronização entre módulos.</p></td></tr><tr><td><p><code>viewticore/</code></p></td><td><p>Motor central de processamento de dados. Este diretório inclui serviços e configurações relacionados à agregação, transformação e armazenamento de dados.</p></td></tr><tr><td><p><code>documents/</code></p></td><td><p>Armazena modelos, relatórios exportados ou arquivos de documento temporários gerados pela plataforma.</p></td></tr><tr><td><p><code>probe/</code></p></td><td><p>Armazena arquivos <code>.csv</code> com dados de tráfego de usuário coletados pelo sistema ao implantar o <strong>Viewtimon</strong> ou o <strong>Viewtify QoS</strong>.</p></td></tr><tr><td><p><code>viewtimanager/</code></p></td><td><p>Contém a camada de gerenciamento GUI, incluindo arquivos para orquestração de plugins, autodescoberta e inventário.</p></td></tr><tr><td><p><code>license-checker/</code></p></td><td><p>Gerencia a validação de licenças para a plataforma Viewtinet. Inclui binários e arquivos de configuração.</p></td></tr><tr><td><p><code>dhyana/</code></p></td><td><p>Hospeda as definições de pipeline ETL do módulo Dhyana (baseadas em XML) e a lógica de execução associada.</p></td></tr></tbody></table>

<br />
