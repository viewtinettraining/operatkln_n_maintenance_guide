---
# snazzyDocs - DO NOT REMOVE OR EDIT BELOW THIS LINE
title: 'Visualizando o Status dos Contêineres'
id: 1GM-1PE0-3E1-IFM
slug: viewing-container-status
isVisible: true
lastUpdated: '2025-10-15 15:59:03'
---
# **<span align="center">Visualizando o Status do Contêiner</span>**

<br />

Para listar todos os contêineres em execução, a Viewtinet fornece um alias conveniente na CLI chamado `dps`, que mapeia para o seguinte comando:

```bash
sudo docker ps
```

Você pode simplesmente executar:

```bash
$ dps
```

Quando você executa o comando `dps` (um alias para `sudo docker ps`), a CLI retorna uma tabela mostrando o estado atual de todos os contêineres Docker ativos no ambiente Viewtinet. Cada linha corresponde a um contêiner e inclui detalhes úteis como:

-   **CONTAINER ID**: O identificador único para o contêiner.
-   **IMAGE**: A imagem Docker usada para criar o contêiner, incluindo a versão (ex., `viewtinet/viewtimanager/backend:6.3.5`).
-   **COMMAND**: O ponto de entrada ou comando usado para iniciar o contêiner.
-   **CREATED**: Quanto tempo atrás o contêiner foi iniciado.
-   **STATUS**: Indica se o contêiner está em execução, há quanto tempo está ativo e se está saudável.
-   **PORTS**: Lista as portas que estão sendo usadas e expostas pelo contêiner (ex., `0.0.0.0:4500-&gt;4000/tcp`).
-   **NAMES**: O nome atribuído ao contêiner, que normalmente inclui o módulo e a função do contêiner (ex., `viewtimanager_viewtinet-viewtimanager-backend_1`).

Esta saída é extremamente útil para diagnosticar problemas, verificar se todos os serviços esperados estão em execução e identificar contêineres que podem estar mal configurados ou falhando. Também ajuda a rastrear qual versão de cada componente (ex., `:6.3.5`) está implantada atualmente.

Abaixo está um exemplo de saída de um sistema Viewtinet totalmente implantado:

```
CONTAINER ID   IMAGE                                     COMMAND                  CREATED        STATUS                  PORTS                                                                                          NAMES
3f1d3d216126   viewtinet/kafka:6.3.5                     "/opt/bitnami/script…"   2 hours ago    Up 2 hours              0.0.0.0:9092->9092/tcp, :::9092->9092/tcp                                                      dhyana_kafka_1
d4ba21773245   viewtinet/viewtinet-dhyana/dhyana:6.3.5   "/app/dhyana -p /con…"   2 hours ago    Up 2 hours                                                                                                             dhyana_viewtinet-dhyana-kafka_1
7b0bf85cebb4   viewtinet/zookeeper:6.3.5                 "/opt/bitnami/script…"   2 hours ago    Up 2 hours              2181/tcp, 2888/tcp, 3888/tcp, 8080/tcp                                                         dhyana_zookeeper_1
b48a20cd0840   viewtinet/viewtinet-dhyana/dhyana:6.3.5   "nice -n -20 /app/dh…"   2 hours ago    Up 2 hours                                                                                                             dhyana_viewtinet-dhyana_1
62bdcff67243   viewtinet/viewtinet-haproxy:6.3.5         "docker-entrypoint.s…"   23 hours ago   Up 23 hours                                                                                                            haproxy_viewtinet-haproxy_1
ae188f58470c   viewtinet/mongodb:6.3.5                   "docker-entrypoint.s…"   23 hours ago   Up 23 hours             27017/tcp                                                                                      license-checker_viewtinet-license-checker-mongodb_1
0f1b8bde4d6b   viewtinet/license-checker:6.3.5           "/app/license-checke…"   23 hours ago   Up 23 hours             0.0.0.0:9974->9974/tcp, :::9974->9974/tcp                                                      viewtinet-license-checker
...
```

> **Nota**: Este é um exemplo real baseado em um sistema Viewtinet em execução. A saída real dependerá dos módulos implantados e de seu estado atual.

<br />