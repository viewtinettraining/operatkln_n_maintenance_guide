---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Alterando o Endereço IP de Gerenciamento'
id: 99S-98I2-CCR-W37
slug: changing-the-management-ip-address
isVisible: true
lastUpdated: '2025-10-15 14:14:33'
---
# **<span align="center">Alterando o Endereço IP de Gerenciamento</span>**

<br />

Há vários cenários em que pode ser necessário alterar o **endereço IP de gerenciamento** de um appliance Viewtinet ou de qualquer sistema que execute a solução Viewtinet.<br />
Por exemplo, quando um appliance é adquirido pela primeira vez, ele é entregue com um **endereço IP de gerenciamento padrão** que deve ser atualizado para corresponder ao segmento de rede onde o appliance será instalado.<br />
Além disso, devido a **requisitos operacionais** ou mudanças na topologia de rede, os administradores também podem precisar modificar o IP de gerenciamento existente para garantir a comunicação e integração adequadas com outros componentes.

No entanto, devido à **arquitetura de software implementada pelo Viewtinet**, alterar o endereço IP apenas no **nível do sistema operacional** não é suficiente.<br />
Vários serviços internos, arquivos de configuração e containers dependem do IP de gerenciamento para comunicação e sincronização.<br />
Portanto, é necessário executar o script dedicado descrito abaixo, que atualiza automaticamente todas as referências internas e reinicia os serviços afetados.

Este procedimento pode ser realizado:

-   Por meio de uma **sessão SSH** usando o usuário `viewtinet`, ou
-   Diretamente no appliance usando um **teclado e monitor** conectados ao console.

<br />

<div class="sd-callout" data-callout-type="warning">Observe que o endereço IP mencionado nesta seção é o IP de gerenciamento do Viewtinet e é diferente do IP do IPMI</div>

## **Execução do Comando**

Execute o seguinte comando a partir do console do appliance ou por SSH como usuário `viewtinet`:

```
/opt/vn/viewtinet-builder/scripts/change-management-ip.sh
```

Para modificar o **endereço IP de gerenciamento** de um appliance Viewtinet ou de qualquer implantação baseada em Viewtinet, um script dedicado é fornecido.<br />
Este script atualiza a configuração de rede, as variáveis de ambiente de todos os componentes e reinicia os serviços necessários.

Após a execução, o sistema exibirá uma mensagem de aviso semelhante a:

```
You are about to change management ip address. If process fails, access to this server could be lost. 
To continue, it is necessary to have IPMI access, please confirm IPMI access is enabled (yes/no):


```

<div class="sd-callout" data-callout-type="warning">É importante confirmar que o <strong>acesso IPMI está habilitado</strong> para garantir a recuperação remota em caso de configuração incorreta de rede.</div>

Digite:

```
yes
```

e pressione **Enter** para continuar.

---

## **Prompts de Configuração**

O script solicitará os detalhes do IP de gerenciamento atual e do novo:

```
Please insert the current management address: 10.30.23.205
Please insert the current mask in CIDR format (e.g., 24 for 255.255.255.0): 24
Please insert the new management address: 10.30.23.5
Please insert the mask in CIDR format (e.g., 24 for 255.255.255.0): 24
Please insert the current gateway: 10.30.23.1
```

O script usa essas informações para atualizar automaticamente o arquivo de configuração **Netplan** correspondente e todos os arquivos `.env` internos dos diferentes módulos Viewtinet:

```
Netplan configuration updated.
...
/opt/vn/viewtinet-builder/scripts/viewtimanager/.env file updated.
...
MongoDB configuration updated.
Restarting the Viewtimanager service...
```

---

## **Reinicialização Automática**

O script realiza uma reinicialização controlada dos principais serviços:

```
Stopping viewtimanager_viewtinet-viewtimanager-dhyana_1 ... done
Stopping viewtimanager_viewtinet-viewtimanager-mongo_1 ... done
Stopping viewtimanager_viewtinet-viewtimanager-webssh2_1 ... done
Stopping viewtimanager_viewtinet-viewtimanager-backend_1 ... done
Stopping viewtimanager_viewtinet-viewtimanager-frontend_1 ... done
Removing containers ... done
Creating containers ... done
```

Quando o processo for concluído com sucesso, você verá uma mensagem de confirmação:

```
Network configuration, .env update, MongoDB changes, and service restart completed successfully.
Please execute 'sudo netplan apply' to apply the Netplan changes.
Note: You will now need to use the new management address for SSH and GUI connections.
```

---

## **Etapa Final**

Para finalizar o processo, aplique a nova configuração de rede:

```
sudo netplan apply
```

Após esta etapa, o acesso ao sistema deve ser feito usando o **novo endereço IP de gerenciamento** tanto para:

-   Conexões SSH
-   Interface web (GUI do Viewtimanager)

<br />

Se você estiver configurando seu appliance pela primeira vez, precisará prosseguir para a etapa de ativação do usuário administrador (consulte o seguinte [link](http:#?target=757-J2LF-2VB-34B#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation)#standard-chassis-installation))

<br />

<br />
