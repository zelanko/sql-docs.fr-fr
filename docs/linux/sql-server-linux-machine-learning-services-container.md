---
title: Exécuter SQL Server Machine Learning Services dans un conteneur | Microsoft Docs
description: Ce didacticiel vous montre comment utiliser SQL Server Machine Learning Services dans un conteneur Linux qui s’exécute sur l’ancrage.
author: uc-msft
ms.author: umajay
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f3d3774adf4bee07269b25c3359b031ca24eb99e
ms.sourcegitcommit: ef7834ed0f38c1712f45737018a0bfe892e894ee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300425"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Exécuter SQL Server Machine Learning Services dans un conteneur

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce didacticiel montre comment créer un conteneur d’ancrage avec SQL Server Machine Learning Services et exécuter des scripts de Machine Learning à partir de Transact-SQL.

> [!div class="checklist"]
> * Clonez le référentiel MSSQL-dockr.
> * Créez SQL Server image de conteneur Linux avec Machine Learning Services.
> * Exécutez SQL Server image de conteneur Linux avec Machine Learning Services.
> * Exécutez des scripts R ou python à l’aide d’instructions Transact-SQL.
> * Arrêtez et supprimez le conteneur SQL Server Linux. 

## <a name="prerequisites"></a>Prérequis

* Interface de ligne de commande git.
* Moteur de docker 1.8 + sur n’importe quelle distribution de Linux prise en charge ou Docker pour Mac et Windows. Pour plus d’informations, consultez [Installer Docker](https://docs.docker.com/engine/installation/).
* Au moins 2 Go d’espace disque.
* Minimum de 2 Go de RAM.
* [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Cloner le référentiel MSSQL-dockr

1. Ouvrez un terminal bash sur un terminal Linux/Mac ou WSL sur Windows.

1. Créez un répertoire local pour contenir une copie du référentiel MSSQL-docker localement.
1. Exécutez la commande git clone pour cloner le référentiel MSSQL-docker.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Créer SQL Server image de conteneur Linux avec Machine Learning Services

1. Accédez au répertoire MSSQL-mlservices.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Exécutez le script build.sh.

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > La génération de l’image de l’ancrer nécessite l’installation de packages d’une taille de plusieurs Go. L’exécution du script peut prendre jusqu’à 20 minutes en fonction de la bande passante réseau.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Exécuter SQL Server image de conteneur Linux avec Machine Learning Services

1. Définissez les variables d’environnement avant d’exécuter le conteneur. Définissez la variable d’environnement PATH_TO_MSSQL sur un répertoire hôte.

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

   Cette commande crée un conteneur SQL Server avec Machine Learning Services avec l’édition développeur (par défaut). Le port SQL Server **1433** est exposé sur l’ordinateur hôte en tant que port **1401**.

   > [!NOTE]
   > La procédure pour exécuter des éditions de production de SQL Server dans des conteneurs est légèrement différente. Pour plus d’informations, consultez [configurer des images de conteneur SQL Server sur l’ancrage](sql-server-linux-configure-docker.md). Si vous utilisez les mêmes noms de conteneur et ports, le reste de cette procédure pas à pas fonctionne toujours avec les conteneurs de production.

1. Pour afficher vos conteneurs Docker, utilisez la commande `docker ps`.

   ```bash
   sudo docker ps -a
   ```

1. Si la colonne **STATUS** présente l’état **Up**, SQL Server est en cours d’exécution dans le conteneur et à l’écoute sur le port spécifié dans la colonne **PORTS**. Si la colonne **STATUS** pour votre conteneur SQL Server affiche **Exited**, consultez la [résolution des problèmes de la section du guide de configuration](sql-server-linux-configure-docker.md#troubleshooting).

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

1. Connectez-vous à SQL Server dans le conteneur et activez l’option de configuration script externe en exécutant l’instruction T-SQL suivante.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Vérifiez Machine Learning Services fonctionne en exécutant le sp_execute_external_script R/python simple suivant.

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

Dans ce didacticiel, vous avez appris à effectuer les opérations suivantes:

> [!div class="checklist"]
> * Clonez le référentiel MSSQL-dockr.
> * Créez SQL Server image de conteneur Linux avec Machine Learning Services.
> * Exécutez SQL Server image de conteneur Linux avec Machine Learning Services.
> * Exécutez des scripts R ou python à l’aide d’instructions Transact-SQL.
> * Arrêtez et supprimez le conteneur SQL Server Linux.

Ensuite, passez en revue les autres scénarios de configuration et de dépannage de l’amarrage:

> [!div class="nextstepaction"]
>[Guide de configuration pour SQL Server sur l’arrimeur](sql-server-linux-configure-docker.md)
