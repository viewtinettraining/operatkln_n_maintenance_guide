---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'GUI Logging for AD Users'
id: 9CB-AQAQ-DQS-CXU
slug: gui-logging-for-ad-users
isVisible: true
lastUpdated: '2025-10-15 15:40:05'
---
# **<span align="center">Acesso à GUI para Usuários do AD</span>**

<br />

Uma vez que a integração com o Active Directory esteja concluída, juntamente com a criação e o mapeamento de funções, você poderá realizar o respectivo teste de acesso. Os usuários devem ser criados no Active Directory e pertencer ao seu grupo correspondente. Os passos são os seguintes:

<br />

1.  <span align="justify">Por favor, acesse o endereço IP de gerenciamento do Viewtinet no seu navegador, usando a porta 4200 (insegura) ou 4201 (segura).</span>
2.  Insira o nome de usuário e a senha
3.  <span align="justify">Se a configuração estiver correta, o Viewtinet autenticará o usuário e exibirá as opções de acordo com a função do usuário</span>

<br />

<span align="justify">Para os propósitos deste guia, três usuários foram criados e atribuídos a cada um dos grupos</span>

<br />

<table><tbody><tr><td><p><strong><span align="center">Usuário</span></strong></p></td><td><p><strong><span align="center">Grupo do Active Directory</span></strong></p></td><td><p><strong><span align="center">Função do Viewtinet</span></strong></p></td><td><p><strong><span align="center">Comportamento</span></strong></p></td></tr><tr><td><p><span align="center">user_admin_viewtinet</span></p></td><td><p><span align="center">Admins_Viewtinet</span></p></td><td><p><span align="center">Admin_Viewtinet</span></p></td><td><p><span align="center">Acesso Total ao Viewtimanager e Viewtisight</span></p></td></tr><tr><td><p><span align="center">user_vs_viewtinet</span></p></td><td><p><span align="center">Viewtisight_Viewtinet</span></p></td><td><p><span align="center">Viewtisight_Viewtinet</span></p></td><td><p>Acesso Total ao Viewtisight e Acesso Negado ao Viewtimanager</p></td></tr><tr><td><p><span align="center">user_ro_viewtinet</span></p></td><td><p>ReadOnly_Viewtinet</p></td><td><p>ReadOnly_Viewtinet</p></td><td><p>Acesso Restrito ao Viewtisight (Sem Compositor de Painéis) e Acesso Negado ao Viewtimanager</p></td></tr></tbody></table>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/I17r1lREoUQtRawS8SHK.png" align="center"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/jcK2QHiZKSXbgj9UVl66.png" align="center"></figure>

A partir da opção 'Profile' no botão 'Help' no Viewtisight, você poderá ver o usuário

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/KShGBk8obnYJohe30mOW.png" align="center"></figure>

<br />

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/67xdZpSTXnATYX4X4b8L.png" align="center"></figure>

Acesso Total ao Viewtisight e Viewtimanager

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/0h3kPAa5wjIMY584gWQ3.png"></figure>

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/paqDUPSynt2tfKwzAR31.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/fmvXkOo9YHfidivgnuit.png" align="center"></figure>

<br />

Acesso Total ao Viewtisight:

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/Hzq276bMwR9CXZWaTN7l.png" align="center"></figure>

Acesso Negado ao Viewtimanager:

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/an7TolCCCey15voheahi.png"></figure>

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/lpRmvZfdbKBvOz6MqnOJ.png" align="center"></figure>

<br />

Acesso restrito ao Viewtisight sem opções para criação de painéis (dashboards), métricas, etc.

<br />

<figure align="center"><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/knXaRhkhYqh66S4j5vz3.png" align="center"></figure>

Acesso Negado ao Viewtimanager:

<br />

<figure><img src="https://app.snazzydocs.com/storage/users/ucsRFoMgaUeUU6iR/docs/5f3sro2CXnrmntow/images/tkdKpHUg05hny8QACXsg.png"></figure>

<br />