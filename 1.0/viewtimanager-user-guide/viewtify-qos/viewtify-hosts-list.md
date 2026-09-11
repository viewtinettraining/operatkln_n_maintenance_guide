---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtify Hosts List'
id: WD5-4HC-BOB-1YK
slug: viewtify-hosts-list
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:13:22'
---
# **<span align="center">Lista de Hosts Viewtify (Viewtify Hosts List)</span>**

<br />

A aba **HOSTS LIST** fornece uma visão geral do appliance físico ou virtual onde o motor Viewtify está atualmente implantado e em execução.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-hosts-list.png" align="center"></figure>

<br />

---

## **Visão Geral Informativa**

Para a grande maioria dos usuários, esta aba é **puramente informativa**. Ela exibe o Hostname ou Endereço IP subjacente (ex., `10.30.23.5`) e o IP da interface LAN associada ao módulo Viewtify. Isso ajuda os administradores a identificar rapidamente qual nó físico ou virtual está processando o tráfego de rede no momento.

Além disso, esta seção exibe o status de Alta Disponibilidade (HA), se aplicável (ex., "Nenhum HA será aplicado, pois há apenas um host definido" para implantações independentes).

> <div class="sd-callout" data-callout-type="warning"><strong>Alterações na Arquitetura do Sistema</strong> As configurações dentro desta aba (como adicionar novos hosts ou desinstalar nós) manipulam diretamente a arquitetura de cluster do motor Viewtify.</div>
> 
> **Não faça nenhuma alteração nesta seção**, a menos que você tenha um profundo conhecimento arquitetônico da implantação ou tenha sido explicitamente instruído pelo Suporte Viewtinet. Modificar esses campos sem cautela pode causar problemas operacionais graves e resultar na interrupção total do processamento de tráfego do motor DPI.

<br />
