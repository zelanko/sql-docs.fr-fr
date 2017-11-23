---
title: Prise en main 2017 du serveur SQL sur Docker | Documents Microsoft
description: "Ce didacticiel de démarrage rapide montre comment utiliser Docker pour exécuter l’image de conteneur de SQL Server 2017. Vous créez et interrogez une base de données avec sqlcmd."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/31/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.workload: Active
ms.openlocfilehash: acd47bd1e2104027610f7ee38c9b135a785429e5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Exécuter l’image de SQL Server 2017 conteneur avec Docker

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Dans ce didacticiel de démarrage rapide, vous utilisez Docker pour extraire et exécuter l’image de conteneur de SQL Server 2017 [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Se connecter avec **sqlcmd** à créer votre première base de données et exécuter des requêtes.

Cette image se compose de SQL Server est en cours d’exécution sur Linux basé sur Ubuntu 16.04. Il peut être utilisé avec le moteur Docker 1.8 + sur Linux ou sur Docker pour Mac et Windows.

> [!NOTE]
> Ce guide de démarrage rapide se concentre spécifiquement sur l’utilisation de mssql-server -**linux** image. L’image Windows n’est pas couverte, mais vous pouvez en savoir plus sur elle sur le [page du Hub Docker mssql-server-windows-developer](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/).

## <a id="requirements"></a> Conditions préalables

- Moteur de docker 1.8 + sur n’importe quel pris en charge la distribution de Linux ou Docker pour Mac et Windows. Pour plus d’informations, consultez [Docker d’installer](https://docs.docker.com/engine/installation/).
- Minimum de 4 Go d’espace disque
- Minimum de 4 Go de RAM
- [Configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

> [!IMPORTANT]
> La valeur par défaut sur Docker pour Mac et Docker pour Windows est de 2 Go pour la VM Moby, donc vous devez le modifier à 4 Go. Si vous exécutez sur Mac ou Windows, utilisez les procédures suivantes pour augmenter la mémoire.

### <a name="increase-docker-memory-to-4-gb-mac"></a>Augmentez la mémoire de Docker à 4 Go (Mac)

Les étapes suivantes augmentent la mémoire pour Docker pour Mac à 4 Go.

1. Cliquez sur le logo de Docker sur la barre d’état supérieur.
1. Sélectionnez **préférences**.
1. Déplacer l’indicateur de mémoire à 4 Go ou plus.
1. Cliquez sur le **redémarrer** bouton sur le bouton de l’écran.

### <a name="increase-docker-memory-to-4-gb-windows"></a>Augmentez la mémoire de Docker à 4 Go (Windows)

Les étapes suivantes augmentent la mémoire pour Docker pour Windows à 4 Go.

1. Avec le bouton droit sur l’icône de Docker à partir de la barre des tâches.
1. Cliquez sur **paramètres** sous ce menu.
1. Cliquez sur le **avancé** onglet.
1. Déplacer l’indicateur de mémoire à 4 Go ou plus.
1. Cliquez sur le **appliquer** bouton.

## <a name="pull-and-run-the-container-image"></a>Extraire et exécuter l’image de conteneur

1. Extraire l’image de conteneur de SQL Server 2017 Linux à partir du Hub d’ancrage.

   ```bash
   sudo docker pull microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker pull microsoft/mssql-server-linux:2017-latest
   ```

   La commande précédente extrait de la dernière image de conteneur de SQL Server 2017. Si vous souhaitez extraire une image spécifique, vous ajoutez un signe deux-points et le nom de balise (par exemple, `microsoft/mssql-server-linux:2017-GA`). Pour voir toutes les images disponibles, consultez [la page du hub Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. Pour exécuter l’image de conteneur avec Docker, vous pouvez utiliser la commande suivante à partir d’un interpréteur de commandes bash (Linux/macOS) ou d’une invite de commandes PowerShell avec élévation de privilèges.

   ```bash
   sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
      -p 1401:1433 --name sql1 \
      -d microsoft/mssql-server-linux:2017-latest
   ```

   ```PowerShell
   docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
      -p 1401:1433 --name sql1 `
      -d microsoft/mssql-server-linux:2017-latest
   ```

   > [!NOTE]
   > Par défaut, il crée un conteneur avec l’édition développeur de SQL Server 2017. Le processus d’exécution des éditions de production dans des conteneurs est légèrement différent. Pour plus d’informations, consultez [exécuter des images de conteneur de production](sql-server-linux-configure-docker.md#production).

   Le tableau suivant fournit une description des paramètres dans la précédente `docker run` exemple :

   | Paramètre |  Description |
   |-----|-----|
   | **-e ' ACCEPT_EULA = Y'** |  Définir le **ACCEPT_EULA** variable à n’importe quelle valeur pour confirmer votre acceptation de la [contrat de licence utilisateur final](http://go.microsoft.com/fwlink/?LinkId=746388). Paramètre de l’image de SQL Server est requis. |
   | **-e ' MSSQL_SA_PASSWORD =\<YourStrong ! Passw0rd\>'** | Spécifiez votre propre mot de passe fort est d’au moins 8 caractères et respecte le [exigences de mot de passe SQL Server](../relational-databases/security/password-policy.md). Paramètre de l’image de SQL Server est requis. |
   | **p - 1401:1433** | Mapper un port TCP sur l’environnement d’hôte (la première valeur) avec un port TCP dans le conteneur (seconde valeur). Dans cet exemple, SQL Server écoute sur TCP 1433 dans le conteneur, et ces informations sont exposées au port, 1401, sur l’ordinateur hôte. |
   | **--nom sql1** | Spécifiez un nom personnalisé pour le conteneur au lieu d’un généré de manière aléatoire. Si vous exécutez plusieurs conteneurs, vous ne pouvez pas réutiliser ce même nom. |
   | **mssql/Microsoft-server-linux:2017-dernière** | L’image de conteneur SQL Server 2017 Linux. |

1. Pour afficher vos conteneurs Docker, utilisez le `docker ps` commande.

   ```bash
   sudo docker ps -a
   ```

   ```PowerShell
   docker ps -a
   ```

   Vous devez voir une sortie similaire à la capture d’écran suivante :

   ![Sortie de la commande docker ps](./media/sql-server-linux-setup-docker/docker-ps-command.png)

1. Si le **état** colonne présente l’état de **des**, puis SQL Server est en cours d’exécution dans le conteneur et à l’écoute sur le port spécifié dans le **PORTS** colonne. Si le **état** colonne pour votre conteneur SQL Server s’affiche **Exited**, consultez la [résolution des problèmes de la section du guide de configuration](sql-server-linux-configure-docker.md#troubleshooting).

Le `-h` (nom d’hôte) paramètre est également utile, mais il n’est pas utilisé dans ce didacticiel pour plus de simplicité. Cela modifie le nom interne du conteneur à une valeur personnalisée. C’est le nom vous verrez retourné dans la requête Transact-SQL suivante :

```sql
SELECT @@SERVERNAME,
    SERVERPROPERTY('ComputerNamePhysicalNetBIOS'),
    SERVERPROPERTY('MachineName'),
    SERVERPROPERTY('ServerName')
```

Paramètre `-h` et `--name` sur la même valeur est un bon moyen d’identifier facilement le conteneur cible.

## <a name="change-the-sa-password"></a>Modifier le mot de passe SA

[!INCLUDE [Change docker password](../includes/sql-server-linux-change-docker-password.md)]

## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

La procédure suivante utilise l’outil de ligne de commande de SQL Server, **sqlcmd**, à l’intérieur du conteneur pour se connecter à SQL Server.

1. Utilisez la `docker exec -it` commande pour démarrer un shell bash interactive à l’intérieur de votre conteneur en cours d’exécution. Dans l’exemple suivant `sql1` est le nom spécifié par le `--name` paramètre lorsque vous avez créé le conteneur.

   ```bash
   sudo docker exec -it sql1 "bash"
   ```

   ```PowerShell
   docker exec -it sql1 "bash"
   ```

1. Une fois à l’intérieur du conteneur, se connecter localement avec sqlcmd. SQLCMD n’est pas dans le chemin d’accès par défaut, donc vous devez spécifier le chemin d’accès complet.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   > [!TIP]
   > Vous pouvez omettre le mot de passe sur la ligne de commande pour être invité à l’entrer.

1. Si l’opération réussit, vous devez accéder à une invite de commandes **sqlcmd** : `1>`.

## <a name="create-and-query-data"></a>Créer et interroger des données

Les sections suivantes vous guident lors de l’utilisation de **sqlcmd** et Transact-SQL pour créer une base de données, ajouter des données et exécuter une requête simple.

### <a name="create-a-new-database"></a>Créer une base de données

La procédure suivante crée une base de données nommée `TestDB`.

1. À partir de l’invite de commandes **sqlcmd**, collez la commande Transact-SQL suivante pour créer une base de données de test :

   ```sql
   CREATE DATABASE TestDB
   ```

1. Sur la ligne suivante, écrivez une requête pour retourner le nom de toutes les bases de données sur votre serveur :

   ```sql
   SELECT Name from sys.Databases
   ```

1. Les deux commandes précédentes n’ont pas été exécutées immédiatement. Vous devez taper `GO` sur une nouvelle ligne pour exécuter les commandes précédentes :

   ```sql
   GO
   ```

### <a name="insert-data"></a>Insérer des données

Créez ensuite une table, `Inventory`, et insérez deux nouvelles lignes.

1. À partir de l’invite de commandes **sqlcmd**, basculez le contexte vers la nouvelle base de données `TestDB` :

   ```sql
   USE TestDB
   ```

1. Créez une table nommée `Inventory` :

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Insérez des données dans la nouvelle table :

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Tapez `GO` pour exécuter les commandes précédentes :

   ```sql
   GO
   ```

### <a name="select-data"></a>Sélectionner les données

Exécutez maintenant une requête pour retourner des données de la table `Inventory`.

1. Dans l’invite de commandes **sqlcmd**, entrez une requête qui retourne les lignes de la table `Inventory` dont la quantité est supérieure à 152 :

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Exécutez la commande :

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Quitter l’invite de commandes sqlcmd

1. Pour mettre fin à votre session **sqlcmd**, tapez `QUIT` :

   ```sql
   QUIT
   ```

1. Pour quitter l’invite de commandes interactive dans votre conteneur, tapez `exit`. Le conteneur se poursuit après avoir quitté l’interpréteur de commandes bash interactif.

## <a id="connectexternal"></a>Se connecter à partir de l’extérieur du conteneur

Vous pouvez également vous connecter à l’instance de SQL Server sur votre ordinateur Docker à partir de n’importe quel outil externe macOS, Windows ou Linux qui prend en charge les connexions SQL.

Les étapes suivantes utilisent **sqlcmd** en dehors de votre conteneur pour se connecter à SQL Server s’exécutant dans le conteneur. Ces étapes supposent que vous avez déjà les outils de ligne de commande SQL Server installés en dehors de votre conteneur. Les mêmes principaux s’appliquent lors de l’utilisation d’autres outils, mais le processus de connexion est unique à chaque outil.

1. Rechercher l’adresse IP de l’ordinateur qui héberge votre conteneur. Sur Linux, utilisez **ifconfig** ou **adresse ip**. Sous Windows, utilisez **ipconfig**.

1. Exécutez sqlcmd en spécifiant l’adresse IP et le port mappé vers le port 1433 dans votre conteneur. Dans cet exemple, qui est le port 1401 sur l’ordinateur hôte.

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourNewStrong!Passw0rd>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourNewStrong!Passw0rd>"
   ```

1. Exécutez les commandes Transact-SQL. Lorsque vous avez terminé, tapez `QUIT`.

Autres outils courants pour vous connecter à SQL Server :

- [Code Visual Studio](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) sur Windows](sql-server-linux-develop-use-ssms.md)

## <a name="remove-your-container"></a>Supprimer le conteneur de votre

Si vous souhaitez supprimer le conteneur de SQL Server utilisé dans ce didacticiel, exécutez les commandes suivantes :

```bash
sudo docker stop sql1
sudo docker rm sql1
```

```PowerShell
docker stop sql1
docker rm sql1
```

> [!WARNING]
> L’arrêt et la suppression d’un conteneur définitivement supprime toutes les données de SQL Server dans le conteneur. Si vous avez besoin de conserver vos données, [créer et copier un fichier de sauvegarde hors du conteneur](tutorial-restore-backup-in-sql-server-container.md) ou utilisez un [technique de persistance de données de conteneur](sql-server-linux-configure-docker.md#persist).

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir un didacticiel sur la façon de restaurer des fichiers de sauvegarde de base de données dans un conteneur, consultez [restaurer une base de données SQL Server dans un conteneur Linux Docker](tutorial-restore-backup-in-sql-server-container.md). Pour Explorer d’autres scénarios, telles que l’exécution de plusieurs conteneurs, la persistance des données et le dépannage, consultez [images de conteneur de configuration de SQL Server 2017 sur Docker](sql-server-linux-configure-docker.md).

Consultez également le [référentiel GitHub de docker de mssql](https://github.com/Microsoft/mssql-docker) des ressources, des commentaires et problèmes connus.
