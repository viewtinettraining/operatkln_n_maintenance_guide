---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Regras de Classificação'
id: FG0-TVA-0IC-BQJ
slug: classification-rules
isVisible: true
isSearchable: true
lastUpdated: '2026-05-26 15:00:33'
---
# **<span align="center">Regras de Classificação</span>**

<br />

A seção de **Regras de Classificação** é onde você define _quais_ fluxos de tráfego específicos deseja gerenciar. Essas regras são a base de qualquer política de QoS do Viewtify. Você pode criar regras baseadas na classificação de inspeção profunda de pacotes (DPI) ou em parâmetros de rede padrão.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_4_img_1.png" align="center"></figure>

<br />

---

## **Tipos de Regras**

Você pode classificar o tráfego usando uma ampla variedade de parâmetros. Versões modernas da engine do Viewtify suportam o reconhecimento de mais de **8.100 aplicativos diferentes** nativamente via DPI. Os tipos de classificação disponíveis incluem:

-   **Application:** Aplicativos específicos reconhecidos pelo DPI (ex., YouTube, Netflix, Office365).
-   **Protocol:** Protocolos da camada de transporte (TCP, UDP, ICMP).
-   **Port & Port Range:** Portas ou intervalos de origem/destino específicos.
-   **IP, IP Range & Subnet:** Endereços IP e sub-redes de origem ou destino.
-   **VLAN:** Tags de LAN virtual.
-   **Time:** Regras baseadas em tempo (úteis quando combinadas com outros parâmetros).

<br />

### **Filtrando Regras**

À medida que sua lista de regras de classificação cresce, você pode encontrar entradas específicas facilmente usando o menu suspenso **Filter by type** no topo da tela. Isso permite que você filtre a visualização para mostrar apenas IPs, sub-redes, portas, protocolos ou VLANs.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_5_img_1.png" align="center"></figure>

<br />

---

## **Criando uma Regra de Classificação**

Para criar uma nova regra de classificação, siga este guia passo a passo:

1.  Clique no botão **+ ADD NEW** na parte inferior da lista.
2.  Insira um **Name** descritivo e único para a regra na primeira coluna.
3.  Selecione o **Type** de parâmetro que você deseja usar no menu suspenso (ex., Portas, Sub-rede, Aplicativo).
4.  Insira o **Value** correspondente na terceira coluna (ex., `443` para uma porta, `192.168.1.0/24` para uma sub-rede). A informação solicitada se adaptará com base no tipo que você selecionou.
5.  Clique no botão **SAVE CHANGES** (com um ícone de marca de seleção) para salvar a nova regra.

Para retornar ao menu de configuração principal, simplesmente clique no botão **Back**.

<br />

---

## **Validações e Avisos**

Para evitar erros de configuração que possam impactar o fluxo de tráfego, o QoS do Viewtify inclui validações integradas.

### **Erros de Validação**

Toda regra é validada antes de poder ser salva. **Os erros devem ser corrigidos** antes de salvar uma política. Por exemplo, se você deixar um campo obrigatório em branco ou tentar criar uma regra com um nome duplicado, o sistema destacará os campos em vermelho.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_7_img_1.png" align="center"></figure>

<br />

### **Avisos**

Os avisos notificam você sobre problemas potenciais, como inserir um valor que já existe. Ao contrário de erros estritos, os avisos servem como um alerta para você verificar duplamente sua configuração.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_8_img_1.png" align="center"></figure>

<br />

---

## **Pesquisando e Excluindo Regras**

-   **Excluindo Regras:** As regras de classificação podem ser excluídas **apenas se não estiverem em uso** em nenhuma política ativa ou salva. Essa proteção evita a quebra de configurações de QoS existentes.
-   **Ferramenta de Pesquisa:** Se você precisar excluir uma regra, mas o sistema impedir, use a opção de **Search (ícone de lupa)** ao lado da regra. Esse recurso ajuda a encontrar a política exata (Caso de Uso) onde a regra de classificação está sendo usada atualmente, permitindo que você a remova primeiro da política.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/pdf_extract/page_9_img_1.png" align="center"></figure>

<br />