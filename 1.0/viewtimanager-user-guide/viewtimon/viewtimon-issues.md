---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtimon Issues'
id: DCE-8CF-PFV-V6J
slug: viewtimon-issues
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 10:34:57'
---
# **<span align="center">Problemas do Viewtimon</span>**

<br />

A guia **ISSUES** atua como o log interno do sistema e o centro de alertas dedicado especificamente ao mecanismo DPI do Viewtimon. Ela monitora as verificações de status em segundo plano e quaisquer anomalias operacionais que ocorram enquanto a sonda estiver em execução.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/viewtimon-issues.png" align="center"></figure>

<br />

---

## **Entendendo o Log de Problemas**

Sempre que o mecanismo do Viewtimon detecta um problema, ele registra uma entrada nesta seção. Se houver problemas não lidos ou ativos, um selo vermelho contendo o número de alertas aparecerá sobre o ícone da guia "ISSUES", notificando proativamente os administradores de que é necessária atenção.

A tabela fornece um detalhamento claro de cada evento:

-   **Timestamp:** A data e a hora exatas em que o problema foi detectado e registrado.
-   **Level:** A gravidade do alerta (por exemplo, `error`, `warning`, `info`). Isso ajuda a priorizar os esforços de solução de problemas.
-   **Message:** Uma descrição detalhada do problema. Por exemplo, pode relatar avisos de status de segundo plano internos ou mudanças de estado em mecanismos de bypass de hardware (por exemplo, `BYPASS_DISCONNECTED`), que são cruciais para garantir alta disponibilidade.

---

## **Gerenciando Problemas**

Para manter um log limpo e gerenciável ao longo do tempo, você pode arquivar problemas que já foram resolvidos ou reconhecidos.

-   **ARCHIVE PAGE:** Clicar neste botão arquivará todos os alertas atualmente visíveis na página ativa, removendo-os da visualização padrão.
-   **Show archived:** Marcar esta caixa permite que você veja alertas históricos que foram arquivados anteriormente, o que é útil para análise pós-incidente ou para auditar problemas recorrentes.

<br />