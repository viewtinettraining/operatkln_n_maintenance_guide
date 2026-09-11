---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Saving and Installing the Plugin'
id: CUS-PLG-FIN-001
slug: saving-and-installing
isVisible: true
isSearchable: true
lastUpdated: '2026-05-25 19:00:00'
---
# **<span align="center">Salvando e Instalando o Plugin</span>**

<br />

Depois de terminar de configurar as etapas de **Extract** (Extrair), **Transform** (Transformar), **Load** (Carregar) e **Schema** (Esquema), você deve confirmar, salvar e instalar o plugin adequadamente para que as alterações tenham efeito no sistema.

<br />

---

## **1. Confirmando as Alterações da Etapa**

Toda vez que você modificar uma etapa (como a configuração de Schema), você estará trabalhando dentro de um pop-up ou de uma janela de configuração específica. Para garantir que essas alterações sejam temporariamente mantidas pelo editor, você deve clicar no botão **CONFIRM** (Geralmente localizado no canto inferior direito).

> [!WARNING] **Fechar sem Confirmar**
> Se você fechar a janela de configuração sem clicar em **CONFIRM**, todas as modificações feitas dentro dessa etapa específica serão perdidas.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/plugin-confirm.png" align="center"></figure>

<br />

---

## **2. Salvando as Alterações no Banco de Dados**

Depois de confirmar as alterações dentro das etapas individuais, você retornará para a interface principal do Editor de Plugin, que mostra o fluxograma do ETL. 

Neste ponto, as alterações estão apenas na memória do editor. Para confirmar (commit) essas configurações no banco de dados, você deve rolar até o final da página e clicar no botão **SAVE CHANGES** (Salvar Alterações). 

Você também pode fornecer uma breve descrição do que foi alterado antes de salvar, o que ajuda a manter um histórico de modificações.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/plugin-save.png" align="center"></figure>

<br />

---

## **3. Instalando o Plugin**

Salvar as alterações no banco de dados garante que seu trabalho seja armazenado, mas **não as aplica automaticamente ao sistema em execução**. 

Para gerar e implantar as pipelines reais, modelos, dashboards e alarmes no host, você deve **instalar** (install) o plugin.

Para fazer isso:
1. Volte para a página de Detalhes do Plugin (fora do editor).
2. Clique no botão **INSTALL** (Instalar).

O sistema compilará as suas configurações e as implantará. Se o plugin já existir, os itens serão atualizados perfeitamente.

<br />

<figure align="center"><img src="https://viewtinettraining.github.io/viewtinettraining635.github.io/images/plugin-install.png" align="center"></figure>

<br />
