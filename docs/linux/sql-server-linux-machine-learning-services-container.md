---
title: Exécuter Machine Learning Services SQL Server dans un conteneur | Microsoft Docs
description: Ce didacticiel vous montre comment utiliser Machine Learning Services SQL Server dans un conteneur Linux qui s’exécute sur Docker.
author: uc-msft
ms.author: umajay
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f3d3774adf4bee07269b25c3359b031ca24eb99e
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68300425"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Exécuter Machine Learning Services SQL Server dans un conteneur

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce didacticiel montre comment générer un conteneur Docker avec Machine Learning Services SQL Server et exécuter des scripts de Machine Learning à partir de Transact-SQL.

> [!div class="checklist"]
> * Clonez le référentiel mssql-docker.
> * Générez SQL une image conteneur Linux SQL Server avec Machine Learning Services.
> * Exécutez SQL une image conteneur Linux SQL Server avec Machine Learning Services.
> * Exécutez des scripts R ou Python à l’aide d’instructions Transact-SQL.
> * Arrêtez et supprimez le conteneur Linux SQL Server. 

## <a name="prerequisites"></a>Conditions préalables requises

* Interface de ligne de commande GIT.
* Docker Engine 1.8+ sur n’importe quelle distribution Linux prise en charge ou Docker pour Mac/Windows. Pour plus d’informations, consultez [Installer Docker](https://docs.docker.com/engine/installation/).
* Au moins 2 Go d’espace disque.
* Au moins 2 Go de RAM.
* [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Clonez le référentiel mssql-docker

1. Ouvrez un terminal Bash sur un terminal Linux/Mac ou WSL sur Windows.

1. Créez un répertoire local pour contenir une copie du référentiel mssql-docker localement.
1. Exécutez la commande clone GIT pour cloner le référentiel mssql-docker.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Générez SQL une image conteneur Linux SQL Server avec Machine Learning Services

1. Modifiez le répertoire par le répertoire mssql-mlservices.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Exécutez le script build.sh.

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > La génération de l’image Docker nécessite l’installation de packages d’une taille de plusieurs Go. L’exécution du script peut prendre jusqu’à 20 minutes en fonction de la bande passante réseau.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Exécutez une image conteneur Linux SQL Server avec Machine Learning Services

1. Définissez des variables d’environnement avant d’exécuter le conteneur. Définissez la variable d’environnement PATH_TO_MSSQL sur un répertoire hôte.

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Exécutez le script run.sh.

   ```bash
   ./run.sh
   ```

   Cette commande crée un conteneur SQL Server avec Machine Learning Services et l’édition Développeur (par défaut). Le port SQL Server **1433** est exposé sur l’hôte en tant que port **1401**.

   > [!NOTE]
   > Le processus d’exécution des éditions SQL Server de production dans des conteneurs est légèrement différent. Pour plus d’informations, consultez [Configurer des images de conteneur SQL Server sur Docker](sql-server-linux-configure-docker.md). Si vous utilisez les mêmes noms et ports de conteneurs, le reste de cette procédure pas à pas fonctionne toujours avec les conteneurs de production.

1. Pour afficher vos conteneurs Docker, utilisez la commande `docker ps`.

   ```bash
   sudo docker ps -a
   ```

1. Si la colonne **ÉTAT** affiche **En cours d’exécution**, SQL Server est en cours d’exécution dans le conteneur et écoute sur le port spécifié dans la colonne **PORTS**. Si la colonne **ÉTAT** pour votre conteneur SQL Server affiche **Quitté**, consultez la [section Résolution des problèmes dans le guide de configuration](sql-server-linux-configure-docker.md#troubleshooting).

   ```bash
   $ sudo docker ps -a
   ```

    Sortie : 
    
    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="change-the-sa-password"></a>Changer le mot de passe AS

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="execute-r--python-scripts-from-transact-sql"></a>Exécuter des scripts R/Python à partir de Transact-SQL

1. Connectez-vous à SQL Server dans le conteneur et activez l’option de configuration de script externe en exécutant l’instruction T-SQL suivante.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Vérifiez que Machine Learning Services fonctionne en exécutant le sp_execute_external_script R/Python simple suivant.

    ```sql
    execute sp_execute_external_script 
    @language = N'R',
    @script = N'
    print("Hello World!")
    print(R.version)
    print(Revo.version)
    OutputDataSet <- InputDataSet', 
    @input_data_1 = N'select 1'
    with result sets((i int));
    go
    ```

    ```sql
    execute sp_execute_external_script 
    @language = N'Python',
    @script = N'
    import sys
    print(sys.version)
    print("Hello World!")
    OutputDataSet = InputDataSet',
    @input_data_1 = N'select 1'
    with result sets((i int));
    go 
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous allez apprendre les actions suivantes :

> [!div class="checklist"]
> * Clonez le référentiel mssql-docker.
> * Générez SQL une image conteneur Linux SQL Server avec Machine Learning Services.
> * Exécutez SQL une image conteneur Linux SQL Server avec Machine Learning Services.
> * Exécutez des scripts R ou Python à l’aide d’instructions Transact-SQL.
> * Arrêtez et supprimez le conteneur Linux SQL Server.

Ensuite, consultez les autres scénarios de configuration et de résolution des problèmes Docker :

> [!div class="nextstepaction"]
>[Guide de configuration pour SQL Server sur Docker](sql-server-linux-configure-docker.md)
