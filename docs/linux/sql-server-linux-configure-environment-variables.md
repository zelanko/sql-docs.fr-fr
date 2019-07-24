---
title: Configurer des paramètres de SQL Server à l’aide de variables d’environnement
description: Cet article explique comment utiliser des variables d’environnement pour configurer des paramètres SQL Server 2017 spécifiques sur Linux.
author: VanMSFT
ms.author: vanto
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 51589a2183043c5c8ea8d1f9bf5d4af6fcc1eea3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419251"
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Configurer des paramètres de SQL Server avec des variables d’environnement sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Vous pouvez utiliser plusieurs variables d’environnement différentes pour configurer SQL Server 2017 sur Linux. Ces variables sont utilisées dans deux scénarios:

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Vous pouvez utiliser plusieurs variables d’environnement différentes pour configurer SQL Server version préliminaire 2019 sur Linux. Ces variables sont utilisées dans deux scénarios:

::: moniker-end

- Pour configurer l’installation initiale à `mssql-conf setup` l’aide de la commande.
- Pour configurer un nouveau [conteneur de SQL Server dans l’ancrage](quickstart-install-connect-docker.md).

> [!TIP]
> Si vous devez configurer SQL Server après ces scénarios d’installation, consultez [configurer SQL Server sur Linux avec l’outil MSSQL-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="environment-variables"></a>Variables d’environnement

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

| Variable d'environnement | Description |
|-----|-----|
| **ACCEPT_EULA** | Définissez la variable **ACCEPT_EULA** sur n’importe quelle valeur pour confirmer que vous acceptez le [Contrat de licence utilisateur final](https://go.microsoft.com/fwlink/?LinkId=746388). Paramètre obligatoire pour l’image de SQL Server. |
| **MSSQL_SA_PASSWORD** | Configurez le mot de passe de l’utilisateur SA. |
| **MSSQL_PID** | Définissez l’édition SQL Server ou la clé de produit. Les valeurs possibles sont : </br></br>**Evaluation**</br>**Développeur**</br>**Express**</br>**Web**</br>**Standard**</br>**Entreprise**</br>**Une clé de produit**</br></br>Si vous spécifiez une clé de produit, elle doit être au format # # # # #-# # # # #-# # # # #-# # # # #-# # # # #, où «#» est un chiffre ou une lettre.|
| **MSSQL_LCID** | Définit l’ID de langue à utiliser pour SQL Server. Par exemple 1036 est le français. |
| **MSSQL_COLLATION** | Définit le classement par défaut pour SQL Server. Cela remplace le mappage par défaut de l’ID de langue (LCID) par le classement. |
| **MSSQL_MEMORY_LIMIT_MB** | Définit la quantité maximale de mémoire (en Mo) que SQL Server pouvez utiliser. Par défaut, il s’agit de 80% de la mémoire physique totale. |
| **MSSQL_TCP_PORT** | Configurez le port TCP sur lequel SQL Server écoute (par défaut 1433). |
| **MSSQL_IP_ADDRESS** | Définissez l’adresse IP. Actuellement, l’adresse IP doit être de type IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Définissez l’emplacement du répertoire de sauvegarde par défaut. |
| **MSSQL_DATA_DIR** | Modifiez le répertoire dans lequel les nouveaux fichiers de données de la base de données SQL Server (. mdf) sont créés. |
| **MSSQL_LOG_DIR** | Modifiez le répertoire dans lequel les nouveaux fichiers journaux de base de données SQL Server (. ldf) sont créés. |
| **MSSQL_DUMP_DIR** | Modifiez le répertoire dans lequel SQL Server déposera les images mémoire et d’autres fichiers de dépannage par défaut. |
| **MSSQL_ENABLE_HADR** | Activez le groupe de disponibilité. Par exemple, «1» est activé et «0» est désactivé |
| **MSSQL_AGENT_ENABLED** | Activez SQL Server Agent. Par exemple, «true» est activé et «false» est désactivé. Par défaut, l’agent est désactivé.  |
| **MSSQL_MASTER_DATA_FILE** | Définit l’emplacement du fichier de données de la base de données Master. Doit être nommé **Master. mdf** jusqu’à la première exécution de SQL Server. |
| **MSSQL_MASTER_LOG_FILE** | Définit l’emplacement du fichier journal de la base de données Master. Doit être nommé **mastlog. ldf** jusqu’à la première exécution de SQL Server. |
| **MSSQL_ERROR_LOG_FILE** | Définit l’emplacement des fichiers ErrorLog. |

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

| Variable d'environnement | Description |
|-----|-----|
| **ACCEPT_EULA** | Définissez la variable **ACCEPT_EULA** sur n’importe quelle valeur pour confirmer que vous acceptez le [Contrat de licence utilisateur final](https://go.microsoft.com/fwlink/?LinkId=746388). Paramètre obligatoire pour l’image de SQL Server. |
| **MSSQL_SA_PASSWORD** | Configurez le mot de passe de l’utilisateur SA. |
| **MSSQL_PID** | Définissez l’édition SQL Server ou la clé de produit. Les valeurs possibles sont : </br></br>**Evaluation**</br>**Développeur**</br>**Express**</br>**Web**</br>**Standard**</br>**Entreprise**</br>**Une clé de produit**</br></br>Si vous spécifiez une clé de produit, elle doit être au format # # # # #-# # # # #-# # # # #-# # # # #-# # # # #, où «#» est un chiffre ou une lettre.|
| **MSSQL_LCID** | Définit l’ID de langue à utiliser pour SQL Server. Par exemple 1036 est le français. |
| **MSSQL_COLLATION** | Définit le classement par défaut pour SQL Server. Cela remplace le mappage par défaut de l’ID de langue (LCID) par le classement. |
| **MSSQL_MEMORY_LIMIT_MB** | Définit la quantité maximale de mémoire (en Mo) que SQL Server pouvez utiliser. Par défaut, il s’agit de 80% de la mémoire physique totale. |
| **MSSQL_TCP_PORT** | Configurez le port TCP sur lequel SQL Server écoute (par défaut 1433). |
| **MSSQL_IP_ADDRESS** | Définissez l’adresse IP. Actuellement, l’adresse IP doit être de type IPv4 (0.0.0.0). |
| **MSSQL_BACKUP_DIR** | Définissez l’emplacement du répertoire de sauvegarde par défaut. |
| **MSSQL_DATA_DIR** | Modifiez le répertoire dans lequel les nouveaux fichiers de données de la base de données SQL Server (. mdf) sont créés. |
| **MSSQL_LOG_DIR** | Modifiez le répertoire dans lequel les nouveaux fichiers journaux de base de données SQL Server (. ldf) sont créés. |
| **MSSQL_DUMP_DIR** | Modifiez le répertoire dans lequel SQL Server déposera les images mémoire et d’autres fichiers de dépannage par défaut. |
| **MSSQL_ENABLE_HADR** | Activez le groupe de disponibilité. Par exemple, «1» est activé et «0» est désactivé |
| **MSSQL_AGENT_ENABLED** | Activez SQL Server Agent. Par exemple, «true» est activé et «false» est désactivé. Par défaut, l’agent est désactivé.  |
| **MSSQL_MASTER_DATA_FILE** | Définit l’emplacement du fichier de données de la base de données Master. Doit être nommé **Master. mdf** jusqu’à la première exécution de SQL Server. |
| **MSSQL_MASTER_LOG_FILE** | Définit l’emplacement du fichier journal de la base de données Master. Doit être nommé **mastlog. ldf** jusqu’à la première exécution de SQL Server. |
| **MSSQL_ERROR_LOG_FILE** | Définit l’emplacement des fichiers ErrorLog. |

::: moniker-end

## <a name="use-with-initial-setup"></a>Utiliser avec l’installation initiale

Cet exemple s' `mssql-conf setup` exécute avec les variables d’environnement configurées. Les variables d’environnement suivantes sont spécifiées:

- **ACCEPT_EULA** accepte le contrat de licence utilisateur final.
- **MSSSQL_PID** spécifie l’édition de développeur sous licence gratuite de SQL Server pour une utilisation hors production.
- **MSSQL_SA_PASSWORD** définit un mot de passe fort.
- **MSSQL_TCP_PORT** définit le port TCP que SQL Server écoute sur 1234.

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="use-with-docker"></a>Utiliser avec l’ancrage

Cet exemple de commande dockr utilise les variables d’environnement suivantes pour créer un conteneur de SQL Server:

- **ACCEPT_EULA** accepte le contrat de licence utilisateur final.
- **MSSSQL_PID** spécifie l’édition de développeur sous licence gratuite de SQL Server pour une utilisation hors production.
- **MSSQL_SA_PASSWORD** définit un mot de passe fort.
- **MSSQL_TCP_PORT** définit le port TCP que SQL Server écoute sur 1234. Cela signifie qu’au lieu de mapper le port 1433 (par défaut) à un port hôte, le port TCP personnalisé doit être mappé `-p 1234:1234` à la commande dans cet exemple.

<!--SQL Server 2017 on Linux -->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Si vous exécutez Dockr sur Linux/macOS, utilisez la syntaxe suivante avec des guillemets simples:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

Si vous exécutez Dockr sur Windows, utilisez la syntaxe suivante avec des guillemets doubles:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2017-latest
```

> [!NOTE]
> Le processus d’exécution des éditions de production dans des conteneurs est légèrement différent. Pour plus d’informations, consultez [Exécuter des images conteneur de production](sql-server-linux-configure-docker.md#production).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

Si vous exécutez Dockr sur Linux/macOS, utilisez la syntaxe suivante avec des guillemets simples:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

Si vous exécutez Dockr sur Windows, utilisez la syntaxe suivante avec des guillemets doubles:

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour d’autres SQL Server paramètres qui ne sont pas répertoriés ici, consultez [configurer SQL Server sur Linux avec l’outil MSSQL-conf](sql-server-linux-configure-mssql-conf.md).

Pour plus d’informations sur l’installation et l’exécution de SQL Server sur Linux, consultez [installer des SQL Server sur Linux](sql-server-linux-setup.md).
