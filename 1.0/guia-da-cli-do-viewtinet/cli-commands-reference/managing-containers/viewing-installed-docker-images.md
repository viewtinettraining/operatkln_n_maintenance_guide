---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Visualizando Imagens Docker Instaladas'
id: R1C-WGZV-8OK-AI9
slug: viewing-installed-docker-images
isVisible: true
lastUpdated: '2025-10-15 16:02:19'
---
# **<span align="center">Visualizando Imagens Docker Instaladas</span>**

<br />

A Viewtinet fornece outro alias útil na CLI: `di`, que é a abreviação de:

```bash
sudo docker image ls
```

Este comando lista todas as imagens Docker atualmente instaladas no sistema. É particularmente útil para:

-   Verificar a **versão exata** de cada componente Viewtinet instalado (ex., `viewtinet/viewtisight:6.3.5`)
-   Verificar a **data de criação** da imagem, o que ajuda a determinar quão recentemente ela foi atualizada ou reconstruída
-   Comparar imagens em diferentes ambientes para consistência
-   **Relatar** as versões da imagem para a equipe de suporte da Viewtinet ao abrir um ticket de suporte

Para usá-lo, simplesmente execute:

```bash
$ di
```

Você verá uma saída semelhante à seguinte:

```
REPOSITORY                        TAG       IMAGE ID       CREATED         SIZE
viewtinet/viewtisight-frontend   6.3.5     a1b2c3d4e5f6   23 hours ago    400MB
viewtinet/viewtiauth-backend     6.3.5     b2c3d4e5f6g7   23 hours ago    350MB
viewtinet/viewticore             6.3.5     c3d4e5f6g7h8   23 hours ago    780MB
```

> **Dica**: Sempre inclua a saída do `di` ao enviar uma solicitação de suporte. Isso permite que a equipe de suporte confirme se você está executando as versões corretas e mais recentes dos componentes envolvidos.

Este comando complementa o `dps` oferecendo uma visão no nível da versão dos módulos implantados, ajudando você a acompanhar a saúde da plataforma e o histórico de atualizações.

<br />

## **Verificando a Versão da Viewtinet Instalada**

Além de monitorar contêineres e imagens, muitas vezes é necessário verificar a versão instalada da própria plataforma Viewtinet. Isso pode ser feito usando o seguinte comando:

```bash
dpkg --list | grep viewtinet
```

Este comando consulta o gerenciador de pacotes Debian para listar quaisquer pacotes instalados que incluam `viewtinet` em seu nome. Uma saída típica se parece com isso:

<br />

```
ii  viewtinet-builder     6.3.3200     all     viewtinet-builder
```

Esta saída indica que o sistema está executando a versão `6.3.3200` do pacote `viewtinet-builder`.

#### Por que isso é útil

-   Permite aos administradores **confirmar a versão exata instalada** da plataforma, independentemente das tags de imagem Docker.
-   É **essencial para fins de suporte**, pois a equipe de suporte da Viewtinet pode solicitar essas informações para solucionar problemas ou verificar a compatibilidade.
-   Ajuda a identificar se o ambiente está executando uma **build estável ou desatualizada**, especialmente antes de realizar atualizações ou correções.

> **Dica**: Inclua o resultado deste comando em qualquer solicitação de suporte para garantir um diagnóstico e resolução mais rápidos.

<br />