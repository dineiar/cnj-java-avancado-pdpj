# Curso Java Avançado no escopo da PDPJ

Este repositório guarda códigos desenvolvidos no curso "Java Avançado" promovido pelo CNJ dentre [as capacitações "Java para a PDPJ-Br"](https://www.cnj.jus.br/formacao-e-capacitacao/pdpj/).

O repositório possui configurações para rodar em [Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers) no VSCode.
Ao abrir a pasta do repositório no VSCode, ele oferecerá no canto inferior direito uma sugestão para reabrir a pasta no container. Aceite-a e o VSCode invocará a construção do container e reabrirá o editor no container.

## FAQ

### Encontrei o erro "INTERNET NOT REACHABLE" na hora de criar o container

Ao tentar criar o container estando atrás de um proxy ou em uma rede com inspeção SSL habilitada (em que se usa um certificado injetado na conexão), o processo de criação do Dev Container pode se encerrar com uma mensagem de erro similar à seguinte:

```
================================================================================
==== INTERNET NOT REACHABLE! ===================================================

 Some functionality is disabled or only partially available.
 If this persists, please enable the offline mode:

   $ sdk offline

================================================================================

This command is not available while offline.
ERROR: Feature "Java (via SDKMAN!)" (ghcr.io/devcontainers/features/java) failed to install! Look at the documentation at https://github.com/devcontainers/features/tree/main/src/java for help troubleshooting this error.
------
```

Para solucionar, basta abrir o arquivo [`sdkman_config`](.devcontainer/sdkman_config) que está na pasta `.devcontainer` e substituir a linha `sdkman_insecure_ssl=false` por `sdkman_insecure_ssl=true`. Feito isso, basta salvar o arquivo e recriar o container que o problema deve estar resolvido.
