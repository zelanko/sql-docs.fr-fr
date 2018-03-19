---
title: "Restaurer une base de données SQL Server dans Docker | Documents Microsoft"
description: "Ce didacticiel montre comment restaurer une sauvegarde de base de données SQL Server dans un conteneur Linux Docker."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: ea1aa01f3917c0d6ee4423861a3bf4fb985f53fa
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="restore-a-sql-server-database-in-a-linux-docker-container"></a>Restaurer une base de données SQL Server dans un conteneur Linux Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce didacticiel montre comment déplacer et de restaurer un fichier de sauvegarde de SQL Server dans une image de conteneur de SQL Server 2017 Linux s’exécutant sur Docker.

> [!div class="checklist"]
> * Extraire et exécuter la dernière image conteneur Linux de SQL Server 2017.
> * Restaurer la base de données dans le conteneur. 
> * Restaurez la base de données dans le conteneur.
> * Exécuter les instructions Transact-SQL pour afficher et modifier la base de données.
> * Sauvegardre la base de données modifiée.

## <a name="prerequisites"></a>Configuration requise

* Moteur de docker 1.8+ sur n’importe quelle distribution de Linux ou Docker supporté pour Mac et Windows. Pour plus d’informations, consultez [Installer Docker](https://docs.docker.com/engine/installation/).
* Minimum de 2 Go d’espace disque
* Minimum de 2 Go de RAM
* [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a name="pull-and-run-the-container-image"></a>Extraire et exécuter l’image de conteneur

1. Ouvrez un terminal de l’interpréteur de commandes sur Linux/Mac ou une session PowerShell avec élévation de privilèges sur Windows.

1. Extraire l’image de conteneur de SQL Server 2017 Linux à partir du Hub Docker.

    ```bash
    sudo docker pull microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker pull microsoft/mssql-server-linux:2017-latest
    ```

    > [!TIP]
    > Tout au long de ce didacticiel, les exemples de commandes docker sont indiquées pour l’interpréteur de commandes bash (Linux/Mac) et PowerShell (Windows).

1. Pour exécuter l’image de conteneur avec Docker, vous pouvez utiliser la commande suivante :

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql1' -p 1401:1433 \
       -v sql1data:/var/opt/mssql \
       -d microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql1" -p 1401:1433 `
       -v sql1data:/var/opt/mssql `
       -d microsoft/mssql-server-linux:2017-latest
    ```

    Cette commande crée un conteneur de SQL Server 2017 avec l’édition développeur (par défaut). Port SQL Server **1433** est exposée sur l’ordinateur hôte en tant que port **1401**. Le paramètre facultatif `-v sql1data:/var/opt/mssql` paramètre crée un conteneur de volume de données nommé **sql1ddata**. Cela permet de conserver les données créées par SQL Server.

   > [!NOTE]
   > Le processus d’exécution des éditions de SQL Server de production dans des conteneurs est légèrement différent. Pour plus d’informations, consultez [exécuter des images de conteneur de production](sql-server-linux-configure-docker.md#production). Si vous utilisez les mêmes noms de conteneur et ports, le reste de cette procédure pas à pas fonctionne toujours avec des conteneurs de production.

1. Pour afficher vos conteneurs Docker, utilisez le `docker ps` commande.

    ```bash
    sudo docker ps -a
    ```

    ```PowerShell
    docker ps -a
    ```
 
1. Si la colonne **STATUS** affiche un statut **Up**, alors SQL Server est en cours d’exécution dans le conteneur et à l’écoute sur le port spécifié dans la colonne **PORTS**. Si le colonne **STATUS** pour votre conteneur SQL Server affiche **Exited**, consultez la [résolution des problèmes de la section du guide de configuration](sql-server-linux-configure-docker.md#troubleshooting).

   ```
   $ sudo docker ps -a

   CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                    NAMES
   941e1bdf8e1d        microsoft/mssql-server-linux   "/bin/sh -c /opt/m..."   About an hour ago   Up About an hour    0.0.0.0:1401->1433/tcp   sql1
   ```

## <a name="change-the-sa-password"></a>Modifier le mot de passe SA

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="copy-a-backup-file-into-the-container"></a>Copier un fichier de sauvegarde dans le conteneur

Ce didacticiel utilise la [base de donnéesd'exemple Wide World Importers](../sample/world-wide-importers/wide-world-importers-documentation.md). Utilisez les étapes suivantes pour télécharger et copier le fichier de sauvegarde de base de données de Wide World Importers dans votre conteneur de SQL Server.

1. Tout d’abord, utilisez **exec de docker** pour créer un dossier de sauvegarde. La commande suivante crée un **/var/opt/mssql/** répertoire à l’intérieur du conteneur de SQL Server.

   ```bash
   sudo docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

   ```PowerShell
   docker exec -it sql1 mkdir /var/opt/mssql/backup
   ```

1. Ensuite, téléchargez le [WideWorldImporters-full.bak](https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0) fichier sur votre ordinateur hôte. Les commandes suivantes accédent au répertoire d’accueil/utilisateur et téléchargent le fichier de sauvegarde en tant que **wwi.bak**.

   ```bash
   cd ~
   curl -L -o wwi.bak 'https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak'
   ```

   ```PowerShell
   curl -OutFile "wwi.bak" "https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak"
   ```

1. Utilisez **docker cp** pour copier le fichier de sauvegarde dans le conteneur dans le répertoire **/var/opt/mssql/backup**.

   ```bash
   sudo docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

   ```PowerShell
   docker cp wwi.bak sql1:/var/opt/mssql/backup
   ```

## <a name="restore-the-database"></a>Restaurer la base de données

Le fichier de sauvegarde se trouve désormais dans le conteneur. Avant de restaurer la sauvegarde, il est important de connaître les noms de fichiers logiques et les types de fichiers à l’intérieur de la sauvegarde. Les commandes Transact-SQL suivantes inspectent la sauvegarde et effectuent la restauration à l’aide de **sqlcmd** dans le conteneur.

> [!TIP]
> Ce didacticiel utilise **sqlcmd** à l’intérieur du conteneur, car le conteneur est fourni avec cet outil préinstallé. Toutefois, vous pouvez également exécuter les instructions Transact-SQL avec un autre client outils en dehors du conteneur, tel que [Visual Studio Code](sql-server-linux-develop-use-vscode.md) ou [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md). Pour vous connecter, utilisez le port de l’hôte qui a été mappé au port 1433 dans le conteneur. Dans cet exemple, qui est **localhost, 1401** sur l’ordinateur hôte et **Host_IP_Address, 1401** à distance.

1. Exécutez **sqlcmd** dans le conteneur à la liste des noms de fichiers logiques et les chemins d’accès à l’intérieur de la sauvegarde. Cette opération s’effectue avec l'instruction Transact-SQL **RESTORE FILELISTONLY**.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost \
      -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE FILELISTONLY FROM DISK = "/var/opt/mssql/backup/wwi.bak"' \
      | tr -s ' ' | cut -d ' ' -f 1-2
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd -S localhost `
      -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE FILELISTONLY FROM DISK = '/var/opt/mssql/backup/wwi.bak'"
   ```

   Vous devez voir une sortie similaire à ce qui suit :

   ```
   LogicalName   PhysicalName
   ------------------------------------------
   WWI_Primary   D:\Data\WideWorldImporters.mdf
   WWI_UserData   D:\Data\WideWorldImporters_UserData.ndf
   WWI_Log   E:\Log\WideWorldImporters.ldf
   WWI_InMemory_Data_1   D:\Data\WideWorldImporters_InMemory_Data_1
   ```

1. Appelez le **restaurer la base de données** pour restaurer la base de données à l’intérieur du conteneur. Spécifiez les nouveaux chemins pour chacun des fichiers à l’étape précédente.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'RESTORE DATABASE WideWorldImporters FROM DISK = "/var/opt/mssql/backup/wwi.bak" WITH MOVE "WWI_Primary" TO "/var/opt/mssql/data/WideWorldImporters.mdf", MOVE "WWI_UserData" TO "/var/opt/mssql/data/WideWorldImporters_userdata.ndf", MOVE "WWI_Log" TO "/var/opt/mssql/data/WideWorldImporters.ldf", MOVE "WWI_InMemory_Data_1" TO "/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1"'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "RESTORE DATABASE WideWorldImporters FROM DISK = '/var/opt/mssql/backup/wwi.bak' WITH MOVE 'WWI_Primary' TO '/var/opt/mssql/data/WideWorldImporters.mdf', MOVE 'WWI_UserData' TO '/var/opt/mssql/data/WideWorldImporters_userdata.ndf', MOVE 'WWI_Log' TO '/var/opt/mssql/data/WideWorldImporters.ldf', MOVE 'WWI_InMemory_Data_1' TO '/var/opt/mssql/data/WideWorldImporters_InMemory_Data_1'"
   ```

   Vous devez voir une sortie similaire à ce qui suit :

   ```
   Processed 1464 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   Processed 33 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   Processed 3862 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Converting database 'WideWorldImporters' from version 852 to the current version 869.
   Database 'WideWorldImporters' running the upgrade step from version 852 to version 853.
   Database 'WideWorldImporters' running the upgrade step from version 853 to version 854.
   Database 'WideWorldImporters' running the upgrade step from version 854 to version 855.
   Database 'WideWorldImporters' running the upgrade step from version 855 to version 856.
   Database 'WideWorldImporters' running the upgrade step from version 856 to version 857.
   Database 'WideWorldImporters' running the upgrade step from version 857 to version 858.
   Database 'WideWorldImporters' running the upgrade step from version 858 to version 859.
   Database 'WideWorldImporters' running the upgrade step from version 859 to version 860.
   Database 'WideWorldImporters' running the upgrade step from version 860 to version 861.
   Database 'WideWorldImporters' running the upgrade step from version 861 to version 862.
   Database 'WideWorldImporters' running the upgrade step from version 862 to version 863.
   Database 'WideWorldImporters' running the upgrade step from version 863 to version 864.
   Database 'WideWorldImporters' running the upgrade step from version 864 to version 865.
   Database 'WideWorldImporters' running the upgrade step from version 865 to version 866.
   Database 'WideWorldImporters' running the upgrade step from version 866 to version 867.
   Database 'WideWorldImporters' running the upgrade step from version 867 to version 868.
   Database 'WideWorldImporters' running the upgrade step from version 868 to version 869.
   RESTORE DATABASE successfully processed 58455 pages in 18.069 seconds (25.273 MB/sec).
   ```

## <a name="verify-the-restored-database"></a>Vérifiez que la base de données restaurée

Exécutez la requête suivante pour afficher une liste de noms de base de données dans votre conteneur :

```bash
sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
   -Q 'SELECT Name FROM sys.Databases'
```

```PowerShell
docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
   -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
   -Q "SELECT Name FROM sys.Databases"
```

Vous devez voir **WideWorldImporters** dans la liste des bases de données.

## <a name="make-a-change"></a>Apportez une modification

Les étapes suivantes apporter une modification dans la base de données.

1. Exécuter une requête pour afficher les 10 premiers éléments de la table **Warehouse.StockItems**.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT TOP 10 StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems ORDER BY StockItemID"
   ```

   Vous devez voir une liste de noms et les identificateurs d’éléments :

   ```
   StockItemID StockItemName
   ----------- -----------------
             1 USB missile launcher (Green)
             2 USB rocket launcher (Gray)
             3 Office cube periscope (Black)
             4 USB food flash drive - sushi roll
             5 USB food flash drive - hamburger
             6 USB food flash drive - hot dog
             7 USB food flash drive - pizza slice
             8 USB food flash drive - dim sum 10 drive variety pack
             9 USB food flash drive - banana
            10 USB food flash drive - chocolate bar
   ```

1. Mettre à jour la description du premier élément par le code suivant l'instruction **UPDATE** : 

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName="USB missile launcher (Dark Green)" WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "UPDATE WideWorldImporters.Warehouse.StockItems SET StockItemName='USB missile launcher (Dark Green)' WHERE StockItemID=1; SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   Vous devez voir une sortie similaire au texte suivant :

   ```
   (1 rows affected)
   StockItemID StockItemName
   ----------- ------------------------------------
             1 USB missile launcher (Dark Green)
   ```

## <a name="create-a-new-backup"></a>Créer une sauvegarde

Une fois que vous avez restauré la base de données dans un conteneur, vous souhaiterez également créer régulièrement des sauvegardes de base de données à l’intérieur du conteneur en cours d’exécution. Les étapes suivent un modèle semblable à la procédure précédente, mais en sens inverse.

1. Utilisez la commande Transact-SQL **sauvegarde de base de données** pour créer une sauvegarde de base de données dans le conteneur. Ce didacticiel crée un nouveau fichier de sauvegarde,**wwi_2.bak**, dans le répertoire précédemment créé **/var/opt/mssql/backup**.

   ```bash
   sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   ```PowerShell
   docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "BACKUP DATABASE [WideWorldImporters] TO DISK = N'/var/opt/mssql/backup/wwi_2.bak' WITH NOFORMAT, NOINIT, NAME = 'WideWorldImporters-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
   ```

   Vous devez voir une sortie similaire à ce qui suit :

   ```
   10 percent processed.
   20 percent processed.
   30 percent processed.
   40 percent processed.
   50 percent processed.
   60 percent processed.
   70 percent processed.
   Processed 1200 pages for database 'WideWorldImporters', file 'WWI_Primary' on file 1.
   Processed 53096 pages for database 'WideWorldImporters', file 'WWI_UserData' on file 1.
   80 percent processed.
   Processed 3865 pages for database 'WideWorldImporters', file 'WWI_InMemory_Data_1' on file 1.
   Processed 938 pages for database 'WideWorldImporters', file 'WWI_Log' on file 1.
   100 percent processed.
   BACKUP DATABASE successfully processed 59099 pages in 25.056 seconds (18.427 MB/sec).
   ```

1. Ensuite, copiez le fichier de sauvegarde hors du conteneur et sur votre ordinateur hôte.

   ```bash
   cd ~
   sudo docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

   ```PowerShell
   cd ~
   docker cp sql1:/var/opt/mssql/backup/wwi_2.bak wwi_2.bak
   ls -l wwi*
   ```

## <a name="use-the-persisted-data"></a>Utiliser les données persistantes

En plus des sauvegardes de base de données pour protéger vos données, vous pouvez également utiliser des conteneurs de volumes de données. Au début de ce didacticiel a été créé le **sql1** contenant le paramètre `-v sql1data:/var/opt/mssql`. Le conteneur de volume de données **sql1data** persiste les données **/var/opt/mssql** même après le conteneur est supprimé. Les étapes suivantes suppriment complètement la **sql1** conteneur, puis créent un nouveau conteneur, **sql2**, avec les données persistantes.

1. Arrêter le conteneur **sql1**.

   ```bash
   sudo docker stop sql1
   ```

   ```PowerShell
   docker stop sql1
   ```

1. Supprimer le conteneur. Cette opération ne supprime pas précédemment créé **sql1data** conteneur de volumes de données et les données qu’elle contient.

   ```bash
   sudo docker rm sql1
   ```

   ```PowerShell
   docker rm sql1
   ```

1. Créer un nouveau conteneur, **sql2** et réutiliser le conteneur de volumes de données **sql1data**.

    ```bash
    sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
       --name 'sql2' -e 'MSSQL_PID=Developer' -p 1401:1433 \
       -v sql1data:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
    ```

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
       --name "sql2" -e "MSSQL_PID=Developer" -p 1401:1433 `
       -v sql1data:/var/opt/mssql -d microsoft/mssql-server-linux:2017-latest
    ```

1. La base de données de Wide World Importers est présente dans le nouveau conteneur.  Exécutez une requête pour vérifier la modification précédente que vous avez apportée.

   ```bash
   sudo docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd \
      -S localhost -U SA -P '<YourNewStrong!Passw0rd>' \
      -Q 'SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1'
   ```

   ```PowerShell
   docker exec -it sql2 /opt/mssql-tools/bin/sqlcmd `
      -S localhost -U SA -P "<YourNewStrong!Passw0rd>" `
      -Q "SELECT StockItemID, StockItemName FROM WideWorldImporters.Warehouse.StockItems WHERE StockItemID=1"
   ```

   > [!NOTE]
   > Le mot de passe SA n’est pas le mot de passe que vous avez spécifié pour le conteur **sql2**, `MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>`. Toutes les données de SQL Server ont été restaurées à partir de **sql1**, y compris le mot de passe modifié à partir de précédemment dans le didacticiel. En effet, certaines options sont ainsi ignorées en raison de la restauration des données dans /var/opt/mssql. Pour cette raison, le mot de passe est `<YourNewStrong!Passw0rd>` comme indiqué ici.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment sauvegarder une base de données sur Windows et les déplacer vers un serveur Linux en cours d’exécution SQL Server 2017 RC2. Vous avez appris comment à :
> [!div class="checklist"]
> * Créer des images de conteneur de SQL Server 2017 Linux.
> * Copier les sauvegardes de base de données SQL Server dans un conteneur.
> * Exécuter des instructions Transact-SQL à l’intérieur du conteneur avec **sqlcmd**.
> * Créer et extraire des fichiers de sauvegarde à partir d’un conteneur.
> * Utiliser des conteneurs de volumes de données dans Docker pour conserver les données de SQL Server.

Ensuite, passez en revue les autres configuration Docker et les scénarios de dépannage :

> [!div class="nextstepaction"]
>[Guide de configuration de 2017 du serveur SQL sur Docker](sql-server-linux-configure-docker.md)
