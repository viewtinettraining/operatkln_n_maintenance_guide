---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Lista de Hosts do Viewtimon'
id: SOA-EQD-8Z7-I99
slug: viewtimon-hosts-list
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:13:22'
---
# **<span align="center">Lista de Hosts do Viewtimon</span>**

<br />

A guia **HOSTS LIST** fornece uma visão geral da appliance física ou virtual onde o mecanismo do Viewtimon está atualmente implantado e em execução.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-hosts-list.png" align="center"></figure>

<br />

---

## **Visão Geral Informativa**

Para a grande maioria dos usuários, esta aba é **puramente informativa**. Ela exibe o Nome do Host subjacente ou o Endereço IP (por exemplo, `10.30.23.5`) e o IP da interface LAN associada ao módulo do Viewtimon. Isso ajuda os administradores a identificar rapidamente qual nó físico ou virtual está processando o tráfego de rede no momento.

Além disso, esta seção exibe o status de Alta Disponibilidade (HA) se aplicável (por exemplo, "No HA will be applied as there are only one host defined" para implantações independentes).

> <div class="sd-callout" data-callout-type="warning"><strong>Mudanças na Arquitetura do Sistema</strong> As configurações dentro desta guia (como a adição de novos hosts ou a desinstalação de nós) manipulam diretamente a arquitetura de cluster do mecanismo Viewtimon.</div>
> 
> **Não faça nenhuma alteração nesta seção**, a menos que você tenha um profundo conhecimento arquitetônico da implantação ou tenha sido explicitamente instruído pelo Suporte da Viewtinet. Modificar esses campos sem cautela pode causar problemas operacionais graves e resultar na interrupção total do processamento de tráfego pelo mecanismo DPI.

<br />