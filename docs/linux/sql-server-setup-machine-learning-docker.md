---
title: Installer sur Docker
titleSuffix: SQL Server Machine Learning Services
description: Découvrez comment installer SQL Server Machine Learning Services (Python et R) sur Docker.
author: cawrites
ms.author: chadam
ms.reviewer: davidph
manager: cgronlun
ms.date: 02/18/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 767df0ec19f0749eab78a757db5bc92eb66cab49
ms.sourcegitcommit: 39d8d2d504d0ab70bac5ae3e981657e15dfb7bee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2020
ms.locfileid: "78964517"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-docker"></a>Installer SQL Server Machine Learning Services (Python et R) sur Docker

Cet article explique comment installer SQL Server Machine Learning Services sur Docker. Vous pouvez utiliser Machine Learning Services pour exécuter des scripts Python et R en base de données. Nous ne fournissons pas de conteneurs prédéfinis avec Machine Learning Services. Vous pouvez en créer un à partir des conteneurs SQL Server à l’aide d’[un exemple de modèle disponible sur GitHub](https://github.com/Microsoft/mssql-docker/tree/master/linux/preview/examples/mssql-mlservices).

## <a name="prerequisites"></a>Prérequis

- Interface de ligne de commande GIT.
- Moteur Docker 1.8+ sur n’importe quelle distribution Linux prise en charge ou Docker pour Mac/Windows. Pour plus d’informations, consultez [Installer Docker](https://docs.docker.com/engine/install/).
- [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a name="clone-the-mssql-docker-repository"></a>Clonez le référentiel mssql-docker

1. Ouvrez un terminal Bash sur Linux ou Mac, ou ouvrez un terminal Sous-système Windows pour Linux sur Windows.

2. Créez un répertoire local pour contenir une copie locale du référentiel mssql-docker.

3. Exécuter la commande clone git pour cloner le référentiel mssql-docker :

    ```bash
    git clone https://github.com/microsoft/mssql-docker mssql-docker
    ```

## <a name="build-a-sql-server-linux-container-image"></a>Générer une image conteneur Linux de SQL Server

1. Modifier le répertoire par le répertoire mssql-mlservices :

2. Dans le même répertoire, exécutez la commande suivante :

    ```bash
       docker builds -t mssql-server-mlservices
    ```

3. Exécutez la commande suivante :

    ```bash
       docker runs -d -e MSSQL_PID=Developer -e ACCEPT_EULA=Y -e ACCEPT_EULA_ML=Y -e SA_PASSWORD=  -v OS>:/var/opt/mssql -p 1433:1433 mssql-server-mlservices
    ```

    Modifiez pour ajouter SA_PASSWORD et le chemin -v. 

4. Confirmez en exécutant la commande suivante :

    ```bash
       docker ps -a
    ```

   > [!NOTE]
   > Pour générer l’image Docker, vous devez installer des packages d’une taille de plusieurs Go. Le script peut prendre jusqu’à 20 minutes pour terminer de s’exécuter en fonction de la bande passante réseau.

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

4. Si la colonne **ÉTAT** affiche **En cours d’exécution**, SQL Server est en cours d’exécution dans le conteneur et écoute sur le port spécifié dans la colonne **PORTS**. Si la colonne **ÉTAT** pour votre conteneur SQL Server affiche **Quitté**, consultez la [section Résolution des problèmes dans le guide de configuration](sql-server-linux-configure-docker.md#troubleshooting).

   ```bash
   $ sudo docker ps -a
   ```
    Sortie :

    ```
    CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
    941e1bdf8e1d        mcr.microsoft.com/mssql/server/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour     0.0.0.0:1401->1433/tcp   sql1
    ```

## <a name="run-in-a-container"></a>Exécuter dans un conteneur

[Exécuter des images conteneur SQL Server avec Docker](quickstart-install-connect-docker.md).

## <a name="connect-to-linux-sql-server-in-the-container"></a>Se connecter à SQL Server Linux dans le conteneur

```sql
EXEC sp_configure  'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE
```

## <a name="next-steps"></a>Étapes suivantes

Les développeurs Python peuvent apprendre à utiliser Python avec SQL Server en effectuant les didacticiels suivants :

+ [Tutoriel : Exécuter Python dans T-SQL](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs Python](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

Pour consulter des exemples d’apprentissage automatique basés sur des scénarios réels, consultez les [Didacticiels d’apprentissage automatique](../advanced-analytics/tutorials/machine-learning-services-tutorials.md).

Les développeurs peuvent démarrer avec quelques exemples simples et découvrir les principes de base du fonctionnement de R avec SQL Server. Pour l’étape suivante, consultez les liens suivants :

+ [Tutoriel : Exécuter R dans T-SQL](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Tutoriel : Analytique dans la base de données pour les développeurs R](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)
