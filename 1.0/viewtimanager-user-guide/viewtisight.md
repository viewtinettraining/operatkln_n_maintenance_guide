---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Viewtisight'
id: V5M-N8MF-JIC-96Z
slug: viewtisight
isVisible: true
isSearchable: true
lastUpdated: '2026-09-10 19:55:02'
---
# **<span align="center">Viewtisight</span>**

## **Introdução**

<span align="justify">A partir do Viewtimanager, a seção Viewtisight fornece controle administrativo sobre o módulo Viewtisight — o mecanismo de visualização e painéis (dashboards) da plataforma Viewtinet. Esta interface não permite que os usuários interajam diretamente com os painéis; em vez disso, ela permite que os administradores do sistema:</span>

-   <span align="justify">Monitorem a integridade e o desempenho do serviço Viewtisight.</span>
-   <span align="justify">Iniciem, parem ou reiniciem o módulo.</span>
-   <span align="justify">Configurem parâmetros do servidor e notificações por e-mail.</span>
-   <span align="justify">Gerenciem os nós do cluster.</span>
-   <span align="justify">Revisem avisos, erros e problemas operacionais.</span>

---

## **🖥️ Acessando o Painel de Administração do Viewtisight**

<br />

<div class="sd-callout" data-callout-type="info"><p>A interface do Viewtisight nem sempre está ativa por padrão. O acesso a este módulo depende de o recurso Viewtisight estar devidamente licenciado em sua implantação.</p></div>

<br />

Para acessar a interface de administração do Viewtisight:

1.  Faça login no **Viewtimanager**.
2.  No menu de navegação à esquerda, clique em **Viewtisight** (ícone: gráfico de barras).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/YOhFgObKsSOcxLdgQBYj.png" align="center"></figure>

Você será redirecionado para o painel de gerenciamento do Viewtisight, que inclui informações do módulo e várias guias para controle operacional.

---

## **🧭 Visão Geral da Interface**

Na parte superior da tela, os seguintes controles gerais e informações estão sempre visíveis:

-   **Informações da Versão (Version Info)**: Exibe a versão e revisão atual (por exemplo, `6.3.5.3966 - Revision b11b8118`).
-   **Tempo de Atividade (Uptime)**: Mostra há quanto tempo o módulo está em execução.
-   **Botões de Controle do Módulo**:
    
    -   🔴 `STOP`
    -   🟠 `RESTART`
    -   🟢 `START`

### Guias Disponíveis:

-   `STATUS`: Monitorar uso de recursos (CPU, memória, IO).
-   `CONFIGURATION`: Editar portas de rede e configurações de e-mail SMTP.
-   `HOSTS LIST`: Gerenciar a configuração do cluster.
-   `ISSUES`: Visualizar alertas recentes e erros.

---

## **📈 Guia STATUS – Desempenho do Módulo**

Esta guia oferece métricas de desempenho do próprio módulo Viewtisight:

-   **Uso de CPU**: Exibe o consumo atual e histórico da CPU em porcentagem.
-   **Uso de Memória**: Acompanha o uso de memória ao longo do tempo.
-   **Gravação em Disco (IO Write)**: Indica a taxa de operações de gravação em disco em kilobytes por segundo (K/s).

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/UeCSP3R0sL99ARMPXXlQ.png" align="center"></figure>

<br />

Essas métricas ajudam a determinar se o módulo está operando dentro dos parâmetros normais e são úteis para solucionar problemas de desempenho.

---

## **⚙️ Guia CONFIGURATION – Configurações de Serviço e E-mail**

Esta guia permite que os administradores configurem as portas de serviço de rede e definam notificações por e-mail.

<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/itd7UzNKH5WXm1xvUdXo.png"><br />

## **🔌 Configuração do Servidor**

Os administradores podem habilitar ou desabilitar os protocolos HTTP/HTTPS e definir as portas correspondentes:

-   **Porta HTTP**: O padrão é `8080`
-   **Porta HTTPS**: O padrão é `8443`

Você pode alternar cada opção por meio das caixas de seleção.

> ⚠️ **Notas Importantes**:
> 
> -   Para **desabilitar a conexão HTTP não segura (porta 8080)**, você deve primeiro acessar a plataforma usando a porta HTTPS segura (geralmente `8443`).<br />
> -   Se você precisar instalar **certificados SSL não autoassinados** (ex.: certificados de uma Autoridade Certificadora confiável), isso deve ser solicitado por meio do **Helpdesk da Viewtinet**.

Desabilitar o HTTP garante que todo o acesso ao Viewtisight seja criptografado e protegido por HTTPS, seguindo as melhores práticas para ambientes de produção.

<br />

## **📧 Notificações por E-mail**

Aqui você pode configurar o servidor SMTP usado para enviar e-mails de alerta e relatórios.

-   **Servidor SMTP**
-   **Usuário / Senha do SMTP**
-   **Segurança da Conexão**: ex.: `Default`
-   **Remetente padrão para alarmes**: `alerts@viewtinet.com`
-   **Remetente padrão para relatórios**: `reports@viewtinet.com`

Botões de controle na parte inferior:

-   ✅ `Save Changes`
-   ❌ `Discard Changes / Reload`
-   🔄 `Reset Default Values`

## **📧 Guia de Integração SMTP para o Viewtinet**

Integrar um servidor SMTP externo permite que o Viewtinet habilite recursos essenciais da plataforma, tais como:

-   🔐 Autenticação Multifator (MFA)
-   📄 Envio agendado de relatórios em PDF
-   🚨 Notificações de alarme por e-mail

Este guia descreve as etapas necessárias para configurar e aplicar as definições de SMTP usando a interface do Viewtisight.

<br />

### **🔧 Etapas de Configuração**

#### **1\. Acessar as Configurações de Notificação por E-mail**

1.  Faça login no **Viewtimanager**.
2.  Clique no módulo **Viewtisight**.
3.  Vá para a guia `CONFIGURATION`.
4.  Localize a seção **Email Notifications**.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/R34Kty9mN7IIqpFvvHQN.png" align="center"></figure>

<br />

**2\. Inserir os Dados do Servidor SMTP**

<table><tbody><tr><th><p>Campo</p></th><th><p>Descrição</p></th></tr><tr><td><p><strong>SMTP Server</strong></p></td><td><p>Nome do host ou endereço IP + porta do seu servidor SMTP (ex.: <code>smtp.office365.com:587</code>)</p></td></tr><tr><td><p><strong>SMTP Username</strong></p></td><td><p>E-mail ou usuário da conta SMTP</p></td></tr><tr><td><p><strong>SMTP Password</strong></p></td><td><p>Senha ou Senha de Aplicativo para autenticação</p></td></tr><tr><td><p><strong>Default Sender for Alarm Emails</strong></p></td><td><p>Endereço de e-mail usado para envio de alertas</p></td></tr><tr><td><p><strong>Default Sender for PDF Reports</strong></p></td><td><p>Endereço de e-mail usado para envio de relatórios PDF</p></td></tr></tbody></table>

<br />
<img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/iDsXYozsge9BripHSN5T.png"><br />

#### **3\. Definir o Nível de Segurança da Conexão**

No menu suspenso `Connection Security`, escolha um dos modos disponíveis:

<table><tbody><tr><th><p>Opção</p></th><th><p>Descrição</p></th></tr><tr><td><p><code>Default</code></p></td><td><p>Conexão TLS com contexto SSL padrão (recomendado para a maioria dos casos)</p></td></tr><tr><td><p><code>Insecure (Disables SSL)</code></p></td><td><p>Sem TLS, sem contexto SSL (<strong>não recomendado</strong>)</p></td></tr><tr><td><p><code>No SSL context creation</code></p></td><td><p>Conexão TLS sem criação de contexto SSL personalizado</p></td></tr></tbody></table>

> 🛡️ Recomendado: Use `Default` a menos que seu provedor SMTP exija outro método.

---

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/dA6N7vp38yHGIy3KYBBs.png"></figure>

#### **4\. Salvar e Confirmar a Configuração**

Após preencher todos os valores:

1.  Clique em ✅ **SAVE CHANGES**
2.  Uma caixa de diálogo de confirmação aparecerá:<br />
    Clique em **YES** para confirmar.

Para aplicar a nova configuração SMTP:

1.  Clique no botão **RESTART**.
2.  Confirme selecionando **YES** na caixa de diálogo.

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/ye0prfSBHms6NsRmjgI8.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/sAYmgHs5oArG5KjQv5Ox.png" align="center"></figure>

<br />

**5\. Reiniciar o Viewtisight para Aplicar Alterações**

Depois de salvo, um banner vermelho será exibido:

> `Please restart Viewtisight to apply config changes`<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/XWtEUeqLhPBLi3VoLuQL.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/6wuO6F2xuOp2cdlS2y8w.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/Cq6Cqdkc6aq4kjvRm5VH.png" align="center"></figure>

<br />

### **⏳ Aguardar o Reinício do Módulo**

<br />

1\. Aguarde aproximadamente **3 minutos**.

2\. Atualize o navegador.

3\. Confirme que o contador de **Uptime** inicia a partir de `0`.

Se você atualizar a página muito cedo, a interface poderá não estar disponível ou apresentar erros.<br />
<br />
**⚠️ Erro Temporário de Carregamento de Modelos**

Imediatamente após o reinício, é normal ver uma mensagem de aviso: “Models have not been loaded yet”

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/NJTdiJwV7MH9TYlcntuQ.png" align="center"></figure>

Esta mensagem aparece nos gráficos de desempenho e **desaparecerá automaticamente após cerca de 5 minutos**, quando todos os componentes estiverem totalmente inicializados.

<br />

## **✅ Integração SMTP Concluída**

Com o Viewtisight em execução e os gráficos visíveis:

-   O MFA poderá enviar códigos de verificação por e-mail.
-   Relatórios agendados serão enviados usando o remetente configurado.
-   Notificações de alarmes serão entregues aos destinatários com base nas regras.

---

## **🛠️ Dicas de Solução de Problemas**

-   Certifique-se de que as credenciais SMTP sejam válidas e autorizadas a enviar a partir do endereço especificado.
-   Confirme a conectividade de rede com o servidor SMTP e a porta correspondente.
-   Verifique se há erros de digitação no endereço do servidor ou na opção de segurança.
-   Use o modo `Default`, a menos que o provedor exija outro método.

---

## **🆘 Precisa de Ajuda?**

Se precisar de suporte com a integração SMTP, gestão de certificados SSL ou entrega de e-mails, entre em contato com o Helpdesk da Viewtinet em:

📧 [support@viewtinet.com](mailto:support@viewtinet.com)

---

## **🗧 Guia HOSTS LIST – Configuração de Cluster**

Nesta guia, os administradores podem definir e gerenciar a lista de hosts do Viewtisight que compõem um cluster.

### Detalhes do Cluster

-   **Endereços Virtuais do Cluster**: Usados para implantações de alta disponibilidade (HA) com IPs virtuais.
-   **Lista de Hosts do Cluster**: Exibe os nós atualmente configurados no cluster do Viewtisight. Cada entrada inclui:
    
    -   `Hostname or IP Address`
    -   `LAN Hostname or IP Address`
    -   Senha e confirmação de senha para registro seguro

#### Ações:

-   ➕ `Add New Host`
-   🗑️ `Uninstall`
-   ✅ `Save Changes`
-   ❌ `Cancel Changes`

> ℹ️ **Nota**:<br />
> Durante a instalação padrão da plataforma Viewtinet, uma única instância do **Viewtisight** é instalada por padrão.<br />
> Esta guia **HOSTS LIST** permite adicionar novas instâncias do Viewtisight para habilitar **Alta Disponibilidade (HA)** ou **ambientes em cluster**.<br />
> Instruções detalhadas para configuração de HA e cluster são fornecidas no **Guia de Instalação em Cluster do Viewtisight**.

Se apenas um host estiver presente, o modo de Alta Disponibilidade **não está ativo**.

---

## **🚨 Guia ISSUES – Registro de Eventos e Erros**

Esta guia mostra uma lista de mensagens operacionais relacionadas ao módulo Viewtisight:

<table><tbody><tr><th><p>Campo</p></th><th><p>Descrição</p></th></tr><tr><td><p>Timestamp</p></td><td><p>Data e hora do evento</p></td></tr><tr><td><p>Level</p></td><td><p>Gravidade (ex.: <code>error</code>, <code>warning</code>)</p></td></tr><tr><td><p>Message</p></td><td><p>Descrição do problema</p></td></tr></tbody></table>

Recursos:

-   Pesquisa e filtro por gravidade ou mensagem.
-   ☑ Caixa de seleção `Show archived`
-   ❌ `Archive Page`
-   Paginação para navegar por registros históricos

---

## **✅ Resumo**

A seção **Viewtisight no Viewtimanager** é dedicada à **administração e gerenciamento do ciclo de vida** do serviço Viewtisight. A partir desta interface, os administradores podem:

-   Monitorar a integridade e o desempenho do Viewtisight
-   Controlar seu estado de execução (start, stop, restart)
-   Configurar portas de serviço e notificações por e-mail
-   Gerenciar a participação em cluster
-   Revisar problemas operacionais e alertas do sistema

Este painel é essencial para garantir que o Viewtisight permaneça estável, integrado e devidamente monitorado dentro da plataforma Viewtinet.

--

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/npZNU5du0pdeIWJtMxkg.png"></figure>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/QG7S1JvWEb4iWs9A/images/EDtw3NRN0LYOgNTUZe7T.png"></figure>

<br />
