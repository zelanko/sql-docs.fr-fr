---
title: Exécutez SQL Server Machine Learning Services dans un conteneur | Microsoft Docs
description: Ce didacticiel vous montre comment utiliser SQL Server Machine Learning Services dans un conteneur Linux en cours d’exécution sur Docker.
author: uc-msft
ms.author: umajay
manager: craigg
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.collection: linux-container
moniker: '>= sql-server-linux-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 3e654e29d6c49d3bf68cdfe7c4e3b479b47a973c
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67840468"
---
# <a name="run-sql-server-machine-learning-services-in-a-container"></a>Exécutez SQL Server Machine Learning Services dans un conteneur

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce didacticiel montre comment créer un conteneur Docker avec SQL Server Machine Learning Services et exécuter des Scripts d’apprentissage automatique à partir de Transact-SQL.

> [!div class="checklist"]
> * Clonez le référentiel mssql-docker.
> * Générer l’image de conteneur de SQL Server Linux avec Services Machine Learning.
> * Exécuter l’image conteneur Linux de SQL Server avec Machine Learning Services.
> * Exécuter des scripts R ou Python à l’aide d’instructions Transact-SQL.
> * Arrêter et supprimer le conteneur de SQL Server Linux. 

## <a name="prerequisites"></a>Prérequis

* Interface de ligne de commande de GIT.
* Moteur de docker 1.8 + sur n’importe quelle distribution de Linux prise en charge ou Docker pour Mac et Windows. Pour plus d’informations, consultez [Installer Docker](https://docs.docker.com/engine/installation/).
* Minimum de 2 Go d’espace disque.
* Minimum de 2 Go de RAM.
* [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Clonez le référentiel mssql-docker

1. Ouvrez un terminal bash sur Linux/Mac ou WSL terminal sur Windows.

1. Créez un répertoire local pour stocker une copie du référentiel mssql-docker localement.
1. Exécutez la commande de clone git pour cloner le référentiel mssql-docker.

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-sql-server-linux-container-image-with-machine-learning-services"></a>Générer l’image de conteneur SQL Server Linux avec Services Machine Learning

1. Accédez au répertoire dans le répertoire mssql-mlservices.

    ```bash
    cd mssql-docker/linux/preview/examples/mssql-mlservices
    ```

1. Exécutez le script build.sh.

   ```bash
   ./build.sh
   ```

   > [!NOTE]
   > Création de l’image docker nécessite l’installation des packages de plusieurs gigaoctets. Le script peut prendre jusqu'à 20 minutes en fonction de la bande passante réseau.

## <a name="run-sql-server-linux-container-image-with-machine-learning-services"></a>Exécuter l’image conteneur Linux de SQL Server avec Machine Learning Services

1. Définir des variables d’environnement avant d’exécuter le conteneur. Définir la variable d’environnement PATH_TO_MSSQL dans un répertoire de l’hôte.

   ```bash
    export MSSQL_PID='Developer'
    export ACCEPT_EULA='Y'
    export ACCEPT_EULA_ML='Y'
    export PATH_TO_MSSQL='/home/mssql/'
   ```

1. Exécuter le script de run.sh.

   ```bash
   ./run.sh
   ```

   Cette commande crée un conteneur de SQL Server avec les Services Machine Learning avec l’édition développeur (valeur par défaut). Le port SQL Server **1433** est exposé sur l’ordinateur hôte en tant que port **1401**.

   > [!NOTE]
   > La procédure pour exécuter des éditions de production de SQL Server dans des conteneurs est légèrement différente. Pour plus d’informations, consultez [Exécuter des images conteneur de production](sql-server-linux-configure-docker.md#production). Si vous utilisez les mêmes noms de conteneur et ports, le reste de cette procédure pas à pas fonctionne toujours avec des conteneurs de production.

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

## <a name="execute-r--python-scripts-from-transact-sql"></a>Exécuter R / Python de scripts à partir de Transact-SQL

1. Se connecter à SQL Server dans le conteneur et activez l’option de configuration de script externe en exécutant l’instruction T-SQL suivante.

    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    go
    ```

1. Vérifier la que machine Learning Services fonctionne en exécutant la sp_execute_external_script R/Python simple suivant.

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

Dans ce didacticiel, vous avez appris à effectuer les opérations suivantes :

> [!div class="checklist"]
> * Clonez le référentiel mssql-docker.
> * Générer l’image de conteneur de SQL Server Linux avec Services Machine Learning.
> * Exécuter l’image conteneur Linux de SQL Server avec Machine Learning Services.
> * Exécuter des scripts R ou Python à l’aide d’instructions Transact-SQL.
> * Arrêter et supprimer le conteneur de SQL Server Linux.

Ensuite, passez en revue les autres configuration Docker et les scénarios de dépannage :

> [!div class="nextstepaction"]
>[Guide de configuration de SQL Server sur Docker](sql-server-linux-configure-docker.md)
