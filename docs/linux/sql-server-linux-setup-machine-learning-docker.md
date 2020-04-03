---
title: Installer sur Docker
titleSuffix: SQL Server Machine Learning Services
description: Découvrez comment installer SQL Server Machine Learning Services (Python et R) sur Docker.
author: cawrites
ms.author: chadam
ms.reviewer: davidph
manager: cgronlun
ms.date: 03/23/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e5a53419aba5515a9a60817ec0cc2a9de5a648d2
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80228340"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-docker"></a>Installer SQL Server Machine Learning Services (Python et R) sur Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment installer SQL Server Machine Learning Services sur Docker. Vous pouvez utiliser Machine Learning Services pour exécuter des scripts Python et R en base de données. Nous ne fournissons pas de conteneurs prédéfinis avec Machine Learning Services. Vous pouvez en créer un à partir des conteneurs SQL Server à l’aide d’[un exemple de modèle disponible sur GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="prerequisites"></a>Prérequis

- Interface de ligne de commande GIT.

- Moteur Docker 1.8+ sur n’importe quelle distribution Linux prise en charge ou Docker pour Mac/Windows. Pour plus d’informations, consultez [Obtenir Docker](https://docs.docker.com/get-docker/).

- Consultez également la [configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Clonez le référentiel mssql-docker

La commande suivante clone le dépôt Git `mssql-docker` vers un répertoire local.

1. Ouvrez un terminal Bash sur Linux ou Mac, ou ouvrez un terminal Sous-système Windows pour Linux sur Windows.

2. Créez un répertoire pour y stocker une copie locale du dépôt mssql-docker.

3. Exécuter la commande clone git pour cloner le référentiel mssql-docker :

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-a-sql-server-linux-container-image"></a>Générer une image conteneur Linux de SQL Server

Pour générer l’image Docker, effectuez les étapes suivantes :

1. Modifier le répertoire par le répertoire mssql-mlservices :

2. Dans le même répertoire, exécutez la commande suivante :

    ```bash
    docker builds -t mssql-server-mlservices
    ```

3. Exécutez la commande suivante :

    ```bash
    docker runs -d -e MSSQL_PID=Developer -e ACCEPT_EULA=Y -e ACCEPT_EULA_ML=Y -e SA_PASSWORD=<your_sa_password> -v OS>:/var/opt/mssql -p 1433:1433 mssql-server-mlservices
    ```

    Changez `<your_sa_password>` par `SA_PASSWORD=<your_sa_password>` et modifiez le chemin `-v`. 

4. Confirmez en exécutant la commande suivante :

    ```bash
    docker ps -a
    ```

   > [!NOTE]
   > Pour générer l’image Docker, vous devez installer des packages d’une taille de plusieurs Go. Le script peut prendre plus ou moins de temps pour s’exécuter entièrement en fonction de la bande passante réseau disponible.

## <a name="run-the-sql-server-linux-container-image"></a>Exécuter l’image conteneur Linux de SQL Server

1. Définissez des variables d’environnement avant d’exécuter le conteneur. Définir la variable d’environnement PATH_TO_MSSQL sur un répertoire hôte :

   ```bash
   export MSSQL_PID='Developer'
   export ACCEPT_EULA='Y'
   export ACCEPT_EULA_ML='Y'
   export PATH_TO_MSSQL='/home/mssql/'
   ```

2. Exécuter le script run.sh :

   ```bash
   ./run.sh
   ```

   Cette commande crée un conteneur SQL Server avec Machine Learning Services à l’aide de l’édition Développeur (par défaut). Le port SQL Server **1433** est exposé sur l’hôte en tant que port **1401**.

   > [!NOTE]
   > Le processus d’exécution des éditions SQL Server de production dans des conteneurs est légèrement différent. Pour plus d’informations, consultez [Configurer des images de conteneur SQL Server sur Docker](sql-server-linux-configure-docker.md). Si vous utilisez les mêmes noms de conteneur et ports, le reste de cette procédure pas à pas fonctionne toujours avec les conteneurs de production.

3. Pour afficher vos conteneurs Docker, exécutez la commande `docker ps` :

   ```bash
   sudo docker ps -a
   ```

4. Si la colonne **ÉTAT** affiche **En cours d’exécution**, SQL Server est en cours d’exécution dans le conteneur et il écoute sur le port spécifié dans la colonne **PORTS**. Si la colonne **ÉTAT** pour votre conteneur SQL Server affiche **Quitté**, consultez la [section Résolution des problèmes dans le guide de configuration](sql-server-linux-configure-docker.md#troubleshooting).

   ```bash
   $ sudo docker ps -a
   ```

    Sortie :

    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="enable-machine-learning-services"></a>Activer Machine Learning Services

Pour activer Machine Learning Services, connectez-vous à votre instance SQL Server et exécutez l’instruction T-SQL suivante :

```sql
EXEC sp_configure  'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE
```

## <a name="next-steps"></a>Étapes suivantes

Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en effectuant les didacticiels suivants :

+ [Tutoriel Python : Prédire la location de ski avec régression linéaire dans SQL Server Machine Learning Services](../advanced-analytics/tutorials/python-ski-rental-linear-regression.md)
+ [Tutoriel : Catégoriser des clients à l’aide de k-moyennes avec SQL Server Machine Learning Services](../advanced-analytics/tutorials/python-clustering-model.md)

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)
