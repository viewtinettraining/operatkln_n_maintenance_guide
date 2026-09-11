---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'IPMI IP Address Configuration'
id: GTF-VP32-JNO-C00
slug: ipmi-ip-address-configuration
isVisible: true
lastUpdated: '2025-10-15 10:36:15'
---
# **<span align="center">Configuração do Endereço IP da IPMI</span>**

<span align="justify">O Intelligent Platform Management Interface (IPMI) fornece acesso remoto a vários usuários em diferentes locais para rede. Ele também permite que um administrador do sistema monitore a integridade do sistema e gerencie eventos do computador remotamente. A IPMI opera de forma independente do sistema operacional. Fornece acesso remoto a vários usuários de diferentes locais para manutenção e gerenciamento do sistema.</span>

Esta seção descreve as etapas para configurar o endereço IP da interface IPMI. Para concluir essas etapas, você precisará conectar um teclado e um monitor ao seu appliance (lista de portas no capítulo anterior, link), ligar o appliance e, quando a mensagem da SuperMicro aparecer, conforme mostrado na imagem abaixo, você deve pressionar a tecla DEL

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/dBYEmjKmvVdmmBMRcFD6.png"></figure>

Na próxima tela, você precisará pressionar a tecla &lt;DEL&gt; novamente.

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/zXcW0E7FveIE23iUXAr5.png"></figure>

O procedimento acima permitirá que você entre no Utilitário de Configuração do appliance (Setup Utility). Para acessar a configuração da IPMI, use a tecla de seta para a direita '-&gt;' para navegar até o menu IPMI, conforme mostrado nas imagens

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/eMrsZet3rgH8KXhUqSEI.png"></figure>

<br />

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/a8YHwpY94NBJwUmyRqpv.png"></figure>

Usando a tecla de seta para baixo no teclado, selecione o menu 'Update IPMI LAN Configuration' (Atualizar Configuração de LAN da IPMI) e pressione a tecla &lt;Enter&gt; para alterar a configuração.

No menu pop-up, selecione 'Yes' (Sim)

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/xgnecpAv56dTAspkzmT6.png"></figure>

Use a tecla de seta para baixo para selecionar cada parâmetro de configuração (Station IP Address, Subnet Mask, Gateway IP Address) para configurá-lo de acordo com as configurações da sua rede

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/ZHCKdxWiIQjNd7lVFkkO.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/gAUHg17U5pzXvR52BJPN.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/FIqKuIBzsQj6bLgXpZs1.png"></figure>

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/AGCp1sU4oGJbaxNYKF7o.png"></figure>

Depois de configurar os parâmetros de rede, para confirmar as alterações, você precisará pressionar a tecla &lt;F4&gt;

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/Rk34fGvJ6LICCghb7wT6.png"></figure>

Para finalizar, selecione a opção 'Yes' (Sim) no menu pop-up

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/xyi36NMuEVSEcTWd/images/6HHddNJPpu8amwjAb2Ev.png"></figure>

Agora o appliance passará por um processo de reinicialização e você poderá acessar a ferramenta IPMI via web. Lembre-se de conectar fisicamente a porta IPMI à sua rede para acessar a ferramenta de IP baseada na web (consulte o seguinte [link](http:#?target=2PL-6EPV-GGQ-5D7#standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) #standard-chassis-installation) )

<br />

<br />