---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtify Issues'
id: CSQ-424-MV3-UWZ
slug: viewtify-issues
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:34:57'
---
# **<span align="center">Problemas do Viewtify (Viewtify Issues)</span>**

<br />

A aba **ISSUES** atua como o log do sistema interno e central de alertas dedicada especificamente ao motor Viewtify DPI. Ela rastreia verificações de status em segundo plano e quaisquer anomalias operacionais que ocorram enquanto a sonda estiver em execução.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-issues.png" align="center"></figure>

<br />

---

## **Entendendo o Log de Problemas**

Sempre que o motor Viewtify detecta um problema, ele registra uma entrada nesta seção. Se houver problemas não lidos ou ativos, um crachá (badge) vermelho contendo o número de alertas aparecerá sobre o ícone da aba "ISSUES", notificando proativamente os administradores de que é necessária atenção.

A tabela fornece um detalhamento claro de cada evento:

-   **Timestamp:** A data e hora exatas em que o problema foi detectado e registrado.
-   **Level:** A gravidade do alerta (ex., `error`, `warning`, `info`). Isso ajuda a priorizar os esforços de solução de problemas (troubleshooting).
-   **Message:** Uma descrição detalhada do problema. Por exemplo, ele pode relatar avisos internos de status em segundo plano ou mudanças de estado em mecanismos de bypass de hardware (ex., `BYPASS_DISCONNECTED`), que são cruciais para garantir a alta disponibilidade.

---

## **Gerenciando Problemas**

Para manter um log limpo e gerenciável ao longo do tempo, você pode arquivar problemas que já foram resolvidos ou confirmados.

-   **ARCHIVE PAGE:** Clicar neste botão arquivará todos os alertas atualmente visíveis na página ativa, removendo-os da visualização padrão.
-   **Show archived:** Marcar esta caixa permite visualizar alertas históricos que foram arquivados anteriormente, o que é útil para análise pós-incidente ou auditoria de problemas recorrentes.

<br />
