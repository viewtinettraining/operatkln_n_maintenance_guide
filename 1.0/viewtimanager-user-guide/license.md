---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: License
id: NFD-NF8N-8A9-479
slug: license
isVisible: true
lastUpdated: '2025-10-15 15:51:35'
---
# **<span align="center">Aplicação de Licença (License Enforcement)</span>**

<br />

## **1\. Introdução**

O sistema de aplicação de licenças da Viewtinet garante que apenas os módulos e recursos devidamente licenciados permaneçam ativos, fornecendo avisos claros ou restrições à medida que os termos da licença se aproximam ou excedem seus limites.

<br />

## **2\. Comportamento de Aplicação de Licença**

1.  **Verificação de Expiração**
    
    -   Se uma licença temporária expirar, os módulos Viewtimon, Viewtify QoS, Viewtilog e outros são desativados, embora ainda seja possível fazer login no Viewtimanager.
    -   O Viewtisight fica totalmente inacessível até que uma licença válida seja carregada.
2.  **Aviso de Expiração Iminente**
    
    -   Quando uma licença temporária estiver dentro de 30 dias de sua data de expiração, ou o período de suporte de uma licença permanente estiver a 30 dias do término, o Viewtimanager exibe um aviso pop-up.
3.  **Habilitação/Desabilitação de Módulos**
    
    -   Se um módulo estiver **desativado** no arquivo de licença, suas tabelas ou recursos serão bloqueados:
        
        -   **Viewtimon**: consultas a `dpi_records` e `voip_records` são negadas.
        -   **Viewtify QoS**: consultas a `qos_records` são negadas.
        -   **Viewtimon Sniffer**: acesso a `pcap_storage_records` é negado.
        -   **Viewtilog**: todas as tabelas, exceto `dpi_records`, `voip_records`, `qos_records` e `self_monitoring*`, são negadas.
            
            <br />
            

## **3\. Cenários de Licenciamento**

### **3.1 Licença em Conformidade (Compliant)**

Todo o uso está abaixo dos limites de aviso e bloqueio. A GUI e todos os módulos funcionam normalmente, com o número de série da licença exibido no topo da seção License.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/wHQ3P0X0g3FDEb1yXaDL.png" align="center"></figure>

<br />
<br />

### **3.2 Licença Temporária Perto de Expirar**

Dentro de 30 dias da expiração, o Viewtimanager exibe um aviso amarelo em pop-up. A funcionalidade permanece ininterrupta.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/OsFnEamRXX1XmJWqJWVn.png" align="center"></figure>

<br />

### **3.3 Suporte de Licença Permanente Perto de Expirar**

Dentro de 30 dias do fim do suporte, um aviso similar é exibido no Viewtimanager. Os módulos continuam funcionando normalmente:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/vbHh9HeVJ5d8OF72bhin.png" align="center"></figure>

<br />

### **3.4 Licença Temporária Expirada**

Após a data de expiração, todos os módulos, exceto o próprio Viewtimanager, são desativados. O Viewtisight fica inacessível e exibe um banner de desativação:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/HU8Y2TkrlbLp5wkUCdMW.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/nNjs5PZGIMh1Tr2XbuFL.png" align="center"></figure>

<br />

### **3.5 Período de Suporte de Licença Permanente Expirado**

Os módulos permanecem operacionais, mas o Viewtimanager exibe uma mensagem de suporte expirado no topo da seção License:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/Uty7zaPj5J2ZW0SfzYth.png" align="center"></figure>

<br />

### **3.6 Módulo(s) Acima dos Limites de Aviso**

Quando o uso (GB/dia, taxa de transferência ou contagem de dispositivos) excede o limite de aviso, o Viewtimanager exibe um alerta não bloqueante na seção License para alertar antes de atingir os limites de bloqueio:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/7tT9sAysLa1YhvJ2eMmA.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/xxbnLMcqQYIipSRsgWE0.png" align="center"></figure>

<br />

### **3.7 Módulo(s) Acima dos Limites de Bloqueio, mas Ainda Conforme**

Se o uso atingiu o limite de negação, mas ainda não por tempo suficiente para declarar não conformidade, o sistema exibe um aviso e registra eventos no histórico da licença. A funcionalidade permanece ativa:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/EWjbMsUh0A39Goc87TrF.png" align="center"></figure>

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/MtTVP0ArwxlFYQn15E3V.png" align="center"></figure>

<br />

### **3.8 Módulo(s) Não Conforme (Non-Compliant)**

Quando o uso exceder os limites de bloqueio por sete dias seguidos (ou regra equivalente para faixas de transferência), o módulo é declarado não conforme:

-   Todas as tabelas relacionadas são bloqueadas (apenas tabelas mínimas de auto-monitoramento permanecem).
-   Uma mensagem de erro aparece no Viewtimanager e o Viewtisight restringe as visualizações afetadas.
-   É necessário aguardar 30 dias a partir da última verificação — ou carregar uma nova licença com limites ampliados — para restaurar o serviço:
    
    <br />
    

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/o16HcrWNNphk1dYg/images/d5PNMk4xuW02QY0Pe2zo.png" align="center"></figure>

---

<br />
