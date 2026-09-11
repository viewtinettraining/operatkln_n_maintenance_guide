---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Tarefas'
id: QLK-CBX1-ANW-UDR
slug: tasks
isVisible: true
lastUpdated: '2025-10-15 14:54:13'
---
# **<span align="center">Tarefas (Tasks)</span>**

<span align="justify">A aba Tarefas (Tasks) no Network Configuration Manager permite orquestrar trabalhos recorrentes ou pontuais em grupos de dispositivos. Uma Tarefa (Task) é um agendamento nomeado + filtro de dispositivo, e uma Subtarefa (Subtask) é a invocação de um único comando dentro desse trabalho. Use as Tarefas para automatizar backups, verificações de conformidade (compliance) ou envios de configuração em lote em um cronograma definido por você.</span>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/Szq3m40HWbuIqJjUmGs3.png" align="center"></figure>

1.  **Visualizar tarefas existentes**
    
    -   **Name**: Seu identificador de tarefa.
    -   **Devices Filter**: Um filtro definido anteriormente (por grupo, tag, faixa de IP).
    -   **Cron** / **Date**: Mostra a expressão de agendamento ou o carimbo de data/hora da próxima execução.
    -   **Scheduled**: Ativa/desativa o trabalho cron.
    -   **Allow Individual Failure**: Continua com outros dispositivos se um falhar.
    -   Ícones **Edit**, **Run**, **Results**, **Delete** para ações rápidas.
2.  **Criar uma nova Tarefa**<br />
    Clique em **Add a New Task** na parte inferior da lista.<br />
    
3.  **Definir propriedades da Tarefa**
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/1OZnFoP7XS98lwWcd9n0.png" align="center"></figure>
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/SiyUs5lpBf5rpXSND2YJ.png" align="center"></figure>
    
4.  **Definir propriedades da Tarefa**<br />
    No diálogo **View Task**:
    
    -   **Nome (Name)**: Dê à sua tarefa um título claro e descritivo.
    -   **Filtrar Dispositivos (Filter Devices)**: Escolha um dos seus filtros de dispositivos pré-construídos.
    -   **Permitir falha individual (Allow individual failure)**: Quando marcado, uma falha de dispositivo não interromperá o restante da execução.
    -   **Agendamento Ativado (Schedule Enabled)**: Ative para abrir os controles de agendamento.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/skHcNTghWAfXpePGLvAM.png" align="center"></figure>
    
    <br />
    
5.  **Definir cronograma de execução**
    
    -   **Data da Próxima Execução (Next Execution Date)** (pontual): Ative e escolha uma data/hora.
    -   **Editor Cron**: Quando **Next Execution Date** estiver desativado e **Schedule Enabled** estiver ativado, configure um agendamento recorrente nas abas **Minutes | Hourly | Daily | Weekly | Monthly**.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/Af0kd0e7DQalTBXON92s.png" align="center"></figure>
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/MO9iqvKav1nREqCmzp3o.png" align="center"></figure>
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/AVdE7o1WBza1fJLhnwKT.png" align="center"></figure>
    
    <br />
    
6.  **Construir seu Fluxo de Tarefa**<br />
    Depois de salvo, você será levado ao editor de fluxo. Seu nó (node) de Tarefa aparece em roxo.
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/R4aw8tNfNB8pvylkLX8m.png" align="center"></figure>
    
    <br />
    
    -   **Adicionar uma Subtarefa (Add a Subtask)**: Passe o mouse sobre a alça inferior e clique para gerar um novo nó.
    -   **Conecte (Connect)** o nó Task ao nó Subtask arrastando o ponto conector.
        
        <br />
        
        <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/7gWj8TcWawKgL6B5rtLf.png" align="center"></figure>
        
        <br />
        
7.  **Configurar cada Subtarefa**
    
    -   Clique em **EDIT** no nó Subtask.
    -   No diálogo **View Subtask**, insira:
        
        -   **Name**: Um rótulo descritivo da subtarefa (ex: "Get Startup Configs").
        -   **Devices**: Herdar do filtro da Tarefa principal ou sobrescrever com uma lista separada por vírgulas.
        -   **Command**: Selecione um de seus Comandos predefinidos.
            
            <br />
            
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/8Qa9bqLbMdoeXyRYjvPN.png" align="center"></figure>
    
    <br />
    
8.  **Salvar e Ativar**
    
    -   Depois de configurar todas as subtarefas, clique em **SAVE** no editor de fluxo.
    -   Sua Tarefa agora será executada em sua programação, executando cada Subtarefa em sequência.
        
        <br />
        
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/xlFsjpWa6vVYi5Ws3wXa.png" align="center"></figure>
    
    <br />
    
9.  **Persistir a nova Tarefa**<br />
    Depois de salvar seu fluxo, retorne à lista **Tasks**. Você verá sua nova linha de tarefa preenchida com o nome, filtro de dispositivo e expressão Cron. Clique em **Save Changes** no canto inferior direito para confirmá-la.<br />
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/kEpm3l7JJ2BEdmpw3Idh.png" align="center"></figure>
    
    <br />
    
10.  **Confirmar o agendamento**<br />
    Uma vez salvo, verifique se a coluna **Cron** mostra a expressão correta (ex: `0 0/5 * ?`) e se **Scheduled** está marcado. Sua tarefa agora está ativa e será executada de acordo com o cronograma definido.
    
    ```text
    Name           | Devices Filter           | Cron            | Scheduled
    -----------------------------------------------------------------------
    My Task Name   | Cisco Training Devices   | 0 0/5   * ?   | ✓
    ```
    
11.  **Executar, Editar ou Excluir sob demanda**
    
    -   **Edit (✏️)** – Modifica o nome da tarefa, filtro ou agendamento.
    -   **Run (▶️)** – Aciona a tarefa imediatamente contra o seu conjunto de dispositivos.
    -   **Delete (🗑️)** – Remove a tarefa completamente.
        
        <br />
        
        <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/HDumqVMP31YZirWf94MJ.png" align="center"></figure>
        
        <br />
        
12.  **Visualizar Resultados da Tarefa**<br />
    Clique em **Results (📋)** para inspecionar o histórico de execuções. Você verá para cada execução:
    
    -   Carimbos de data/hora de **Início / Fim (Start / Finish)**
    -   Contagens de **Sucesso / Falha de Hosts (Hosts Success / Failure)**
    -   Contagens de **Comandos Executados / Sucesso / Falha (Commands Run / Success / Failure)**
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/2KrDvj6S0vFToz7QUIDM.png" align="center"></figure>
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/7APhMdiDceOCXQc8a4D2.png"></figure>
    
    <br />
    
    Expanda qualquer execução para aprofundar-se nos detalhes no nível do host, depois expanda um host para ver os **Subtask Results** (Resultados da Subtarefa) e clique em **👁️** na **Command Output** (Saída de Comando) para visualizar a saída bruta do dispositivo (ex: running-config).
    
    <br />
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/uUihXNE4tHptDMkNbKFp.png"></figure>
    
    <figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/K0WkdPEebkwTMb8MVHLW.png"></figure>
    
    <figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/lFloitXerrYPHdrx4ZbI.png" align="center"></figure>
    
    <br />
    

> **Nota:** Esta seção abrange apenas a visualização de saídas de comando. O armazenamento de arquivos e o gerenciamento de arquivos das configurações coletadas serão explicados no capítulo **“Configurations”**.

<br />