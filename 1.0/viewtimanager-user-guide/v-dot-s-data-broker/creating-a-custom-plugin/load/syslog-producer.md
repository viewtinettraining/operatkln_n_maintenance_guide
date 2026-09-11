---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Produtor Syslog'
id: SYS-PRD-LG1-TR4
slug: syslog-producer
isVisible: true
isSearchable: true
lastUpdated: '2026-05-22 16:22:00'
---
# **<span align="center">Produtor de Syslog (Syslog Producer)</span>**

<br />

O **Syslog Producer** permite que você exporte a grade final transformada como mensagens Syslog para um servidor remoto usando o protocolo padrão Syslog (UDP). Cada linha da grade processada é formatada e encaminhada como uma mensagem Syslog individual para o destino configurado.

Isso é particularmente útil quando você precisa integrar os dados processados da Viewtinet com plataformas SIEM de terceiros, sistemas de agregação de logs ou qualquer ferramenta externa que suporte a ingestão de Syslog.

<br />

> [!WARNING] **UDP — Protocolo sem Conexão**<br />
> O Syslog opera sobre **UDP**, que é um protocolo de transporte sem conexão e não confiável. Isso significa que a Viewtinet envia as mensagens sem estabelecer uma conexão prévia e **não tem como confirmar se o servidor remoto está de fato recebendo os dados**. Não há mecanismo de confirmação ou feedback de erro do destino.<br /><br />
> Portanto, é **responsabilidade do administrador** garantir a conectividade de rede entre o servidor Viewtinet e o destino Syslog **antes** de habilitar este produtor. É altamente recomendável verificar a acessibilidade (ex., testando com `netcat` ou validando as regras de firewall para o IP e a porta de destino) para garantir que as mensagens estão sendo entregues corretamente.

<br />

---

## **Parâmetros de Configuração**

Depois de selecionar `Syslog Producer` no menu suspenso de Tipo de Produtor, os seguintes parâmetros de conexão e formatação ficam disponíveis:

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/syslog-producer-config.png" align="center"></figure>

<br />

-   **IP Address / Hostname** (Endereço IP / Nome do host): O endereço IP de destino ou nome do host do servidor Syslog remoto para onde as mensagens serão enviadas (ex., `10.30.23.5`).
-   **Syslog port** (Porta Syslog): A porta UDP no servidor de destino escutando mensagens Syslog. O padrão padrão é `514`.
-   **Timestamp position** (Posição do carimbo de data/hora): Define a posição (índice) dentro da mensagem Syslog onde o timestamp será inserido. Um valor de `0` o coloca bem no início da carga útil (payload) da mensagem.
-   **Timestamp format** (Formato do carimbo de data/hora): A string de formatação usada para representar o timestamp em cada mensagem. Segue os curingas (wildcards) padrão do comando `date` do Linux. Por exemplo, `%s%f` produz um timestamp epoch de alta precisão incluindo frações de segundo.
-   **Message severity** (Gravidade da mensagem): O nível de gravidade Syslog atribuído a cada mensagem exportada, seguindo os códigos de gravidade Syslog padrão (RFC 5424). Valores comuns incluem:
    -   `0` — Emergência (Emergency)
    -   `1` — Alerta (Alert)
    -   `2` — Crítico (Critical)
    -   `3` — Erro (Error)
    -   `4` — Aviso (Warning)
    -   `5` — Notificação (Notice)
    -   `6` — Informativo (Informational)
    -   `7` — Depuração (Debug)

<br />
