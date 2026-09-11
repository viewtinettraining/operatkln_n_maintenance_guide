---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'SSH'
id: DNT-JX5E-QQ6-D9Q
slug: ssh
isVisible: true
lastUpdated: '2025-09-03 16:05:08'
---
# **<span align="center">Conector de Consulta SSH</span>**

O **Conector de Consulta SSH** permite que o Viewtilog se conecte a dispositivos remotos usando SSH e recupere métricas do sistema ou execute comandos personalizados.<br />
Este conector é particularmente útil quando você precisa monitorar servidores ou dispositivos de rede nos quais o SNMP ou outros protocolos não estão habilitados, mas o acesso SSH está disponível.<br />
Ele é um **conector agendado**, o que significa que é executado periodicamente com base na frequência de execução definida.

<br />

## **Principais Recursos**

-   Estabelece uma sessão SSH com o host de destino.
-   Coleta métricas padrão como:
    
    -   **Uso de CPU**
    -   **Utilização de memória**
    -   **Uso de disco**
    -   **Interfaces de rede**
    -   **Tempo de atividade (Uptime)**
-   Permite a execução de **comandos personalizados** definidos pelo usuário.
-   Suporta **autenticação baseada em senha** ou outros métodos SSH.

<br />

## **Parâmetros de Configuração**

A partir das capturas de tela fornecidas:

1.  **Tipo de Conector**<br />
    Selecione **SSH Query Connector** como o tipo de conector.
2.  **Nome do Pipeline**<br />
    Defina um nome único para o pipeline (ex., `my_ssh_connector`).
3.  **Configuração de Execução**
    
    -   **Tipo de Frequência**: Agendado ou periódico.
    -   **Expressão Cron**: Define com que frequência as consultas serão executadas (ex., a cada minuto).
    -   **Número de Execuções**: `-1` significa execuções ilimitadas.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/Uk3m0c5PZj7X3HsA0hoS.png" align="center"></figure>
    
    <br />
    
4.  **Configuração do Host**
    
    -   **Nome do Host**: Endereço IP ou nome do host do dispositivo (ex., `10.30.23.10`).
    -   **Porta**: A porta SSH padrão é `22`.
    -   **Usuário**: Nome de usuário SSH (ex., `viewtinet`).
    -   **Tipo de Autenticação**: Senha (outros métodos podem estar disponíveis).
    -   **Senha**: A senha correspondente para a autenticação.
    -   Múltiplos hosts podem ser adicionados, se necessário.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/ZkIArSUbkgkn2FhneYLT.png" align="center"></figure>
    
    <br />
    
5.  **Consultas (Queries)**<br />
    Escolha o tipo de consulta a ser executada. As opções disponíveis incluem:
    
    -   `cpu` → Recuperar uso de CPU.
    -   `disk` → Utilização de disco.
    -   `memory` → Uso de memória.
    -   `network` → Métricas da interface de rede.
    -   `service` → Status do serviço.
    -   `uname` → Informações do sistema.
    -   `uptime` → Tempo de atividade do sistema.
    -   `cmd` → Executar um comando personalizado.

<br />

## **Exemplo: Consultando Métricas de CPU**

-   **Nome do Pipeline**: `my_ssh_cpu_monitor`
-   **Host**: `10.30.23.10`
-   **Usuário**: `viewtinet`
-   **Autenticação**: Senha
-   **Tipo de Consulta**: `cpu`

Essa configuração fará a conexão via SSH e recuperará periodicamente os dados de uso de CPU a partir do host especificado.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/nnoeT0qAXnL7T0qi/images/zQwoKveREFPYvSOYQWZk.png" align="center"></figure>

<br />

<br />

---

> ⚠️ **Nota Importante**<br />
> Certifique-se de que as credenciais SSH fornecidas tenham as permissões necessárias para executar as consultas selecionadas. Para ambientes de produção, é recomendável usar contas restritas de leitura (read-only) em vez de usuários root.

<br />