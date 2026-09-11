---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: WMI
id: BAR-U0M4-7C6-7OF
slug: wmi
isVisible: true
lastUpdated: '2025-09-03 16:37:21'
---
# **<span align="center">Conector WMI</span>**

<br />

O **Conector WMI (Instrumentação de Gerenciamento do Windows)** foi projetado para extrair métricas de desempenho, logs e dados de configuração diretamente de servidores Windows por meio da interface WMI.

Este conector opera como um **pipeline agendado**, executando consultas periodicamente para reunir informações como uso de CPU, memória, estatísticas de disco e outros contadores do sistema.

---

### ⚠️ Aviso Importante

Devido a uma **atualização de segurança lançada pela Microsoft em março de 2013**, o uso do WMI para consultas remotas foi restrito.<br />
Como resultado, o **Conector WMI não pode ser utilizado com servidores Windows que tenham este patch instalado**.

Para ambientes com sistemas Windows modernos e atualizados, este conector não é funcional e métodos alternativos (como o **WinRM por HTTPS**) deverão ser usados em seu lugar.

---

### Recomendação

Se você precisar coletar métricas ou logs de servidores Windows:

-   Verifique se a versão do Windows é anterior ao patch de março de 2013 (não recomendado para produção).
-   Caso contrário, configure o ambiente para usar os **conectores WinRM**, que são alternativas suportadas e seguras.

<br />