---
title: Prise en main 2017 du serveur SQL sur Docker | Documents Microsoft
description: "Ce didacticiel de démarrage rapide montre comment utiliser Docker pour exécuter l’image de conteneur de SQL Server 2017. Vous créez et interrogez une base de données avec sqlcmd."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 09/20/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 82737f18-f5d6-4dce-a255-688889fdde69
ms.translationtype: MT
ms.sourcegitcommit: f684f0168e57c5cd727af6488b2460eeaead100c
ms.openlocfilehash: 7fe6626cf8c5b9b348e95b956cee9ac67db16f97
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="run-the-sql-server-2017-container-image-with-docker"></a>Exécuter l’image de SQL Server 2017 conteneur avec Docker

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Dans ce didacticiel de démarrage rapide, vous utilisez Docker pour extraire et exécuter l’image de conteneur SQL Server 2017 RC2, [mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/). Se connecter avec **sqlcmd** à créer votre première base de données et exécuter des requêtes.

Cette image se compose de SQL Server est en cours d’exécution sur Linux basé sur Ubuntu 16.04. Il peut être utilisé avec le moteur Docker 1.8 + sur Linux ou sur Docker pour Mac et Windows.

> [!NOTE]
> Ce guide de démarrage rapide se concentre spécifiquement sur l’utilisation de l’image mssql-server-linux. L’image Windows n’est pas couverte, mais vous pouvez en savoir plus sur elle sur le [page du Hub Docker mssql-server-windows](https://hub.docker.com/r/microsoft/mssql-server-windows/).

## <a id="requirements"></a> Conditions préalables

- Moteur de docker 1.8 + sur n’importe quel pris en charge la distribution de Linux ou Docker pour Mac et Windows.
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

1. Extraire l’image de conteneur à partir du Hub d’ancrage.

    ```bash
    docker pull microsoft/mssql-server-linux
    ```

    > [!TIP]
    > Pour Linux, selon votre configuration système et utilisateur, vous devrez peut-être faire précéder chaque `docker` avec `sudo`.

    > [!NOTE]
    > La commande ci-dessus extrait de la dernière image de conteneur de SQL Server. Si vous souhaitez extraire une image spécifique, vous ajoutez un signe deux-points et le nom de balise (par exemple, `microsoft/mssql-server-linux:rc1`). Pour voir toutes les images disponibles, consultez [la page du hub Docker mssql-server-linux](https://hub.docker.com/r/microsoft/mssql-server-linux/tags/).

1. Pour exécuter l’image de conteneur avec Docker, vous pouvez utiliser la commande suivante à partir d’un interpréteur de commandes bash (Linux/macOS) :

    ```bash
    docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' -e 'MSSQL_PID=Developer' -p 1401:1433 --name sqlcontainer1 -d microsoft/mssql-server-linux
    ```

    Si vous utilisez Docker pour Windows, utilisez la commande suivante à partir d’une invite PowerShell de commandes avec élévation de privilèges :

    ```PowerShell
    docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" -e "MSSQL_PID=Developer" -p 1401:1433 --name sqlcontainer1 -d microsoft/mssql-server-linux
    ```

    > [!NOTE]
    > La seule différence entre l’exemple de l’interpréteur de commandes (Linux/macOS) et l’exemple PowerShell (Windows) est de guillemets simples ou des guillemets doubles autour de variables d’environnement. La commande docker run échoue si vous utilisez une autre. Dans le reste de cette rubrique, un interpréteur de commandes et des blocs de code PowerShell sont fournis pour des raisons pratiques. S’il n'existe qu’un exemple, il fonctionne sur toutes les plateformes, y compris Windows.

    Le tableau suivant fournit une description des paramètres dans la précédente `docker run` exemple :

    | Paramètre |  Description |
    |-----|-----|
    | **-e ' ACCEPT_EULA = Y'** |  Définir le **ACCEPT_EULA** variable à n’importe quelle valeur pour confirmer votre acceptation de la [contrat de licence utilisateur final](http://go.microsoft.com/fwlink/?LinkId=746388). Paramètre de l’image de SQL Server est requis. |
    | **-e ' MSSQL_SA_PASSWORD =\<YourStrong ! Passw0rd\>'** | Spécifiez votre propre mot de passe fort est d’au moins 8 caractères et répondant à [exigences de mot de passe SQL Server](../relational-databases/security/password-policy.md). Paramètre de l’image de SQL Server est requis. |
    | **-e ' MSSQL_PID = Developer'** | Spécifie la clé de produit ou d’édition. Dans cet exemple, l’Édition Developer librement sous licence est utilisée pour le test de hors production. Pour les autres valeurs, consultez [des paramètres de configuration de SQL Server avec les variables d’environnement sur Linux](sql-server-linux-configure-environment-variables.md). |
    | **p - 1401:1433** | Mapper un port TCP sur l’environnement d’hôte (la première valeur) avec un port TCP dans le conteneur (seconde valeur). Dans cet exemple, SQL Server écoute sur TCP 1433 dans le conteneur, et ces informations sont exposées au port, 1401, sur l’ordinateur hôte. |
    | **--nom sqlcontainer1** | Spécifiez un nom personnalisé pour le conteneur au lieu d’un généré de manière aléatoire. Si vous exécutez plusieurs conteneurs, vous ne pouvez pas réutiliser ce même nom. |
    | **Microsoft/mssql-server-linux** | L’image de conteneur SQL serveur Linux. Sauf indication contraire, l’emplacement par défaut pour le **dernière** image. |


1. Pour afficher vos conteneurs Docker, utilisez le `docker ps` commande.

    ```bash
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

Le compte SA est un administrateur système sur l’instance de SQL Server qui est créé lors de l’installation. Après avoir créé votre conteneur de SQL Server, le `MSSQL_SA_PASSWORD` variable d’environnement spécifiée est détectable en exécutant `echo $MSSQL_SA_PASSWORD` dans le conteneur. Pour des raisons de sécurité, modifier votre mot de passe SA.

1. Choisissez un mot de passe fort à utiliser pour l’utilisateur SA.

1. Utilisez `docker exec` pour exécuter **sqlcmd** pour modifier le mot de passe à l’aide de Transact-SQL. Remplacez `<YourStrong!Passw0rd>` et `<YourNewStrong!Passw0rd>` avec vos propres valeurs de mot de passe.

   ```bash
   docker exec -it sqlcontainer1 /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourStrong!Passw0rd>' -Q 'ALTER LOGIN SA WITH PASSWORD="<YourNewStrong!Passw0rd>"'
   ```

   ```PowerShell
   docker exec -it sqlcontainer1 /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "<YourStrong!Passw0rd>" -Q "ALTER LOGIN SA WITH PASSWORD='<YourNewStrong!Passw0rd>'"
   ```

## <a name="connect-to-sql-server"></a>Se connecter à SQL Server

La procédure suivante utilise l’outil de ligne de commande de SQL Server, **sqlcmd**, à l’intérieur du conteneur pour se connecter à SQL Server.

1. Utilisez la `docker exec -it` commande pour démarrer un shell bash interactive à l’intérieur de votre conteneur en cours d’exécution. Dans l’exemple suivant `sqlcontainer1` est le nom spécifié par le `--name` paramètre lorsque vous avez créé le conteneur.

    ```bash
    docker exec -it sqlcontainer1 "bash"
    ```

1. Une fois à l’intérieur du conteneur, se connecter localement avec sqlcmd. SQLCMD n’est pas dans le chemin d’accès par défaut, donc vous devez spécifier le chemin d’accès complet.

    ```bash
    /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '<YourPassword>'
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

## <a name="connect-from-outside-the-container"></a>Se connecter à partir de l’extérieur du conteneur

Vous pouvez également vous connecter à l’instance de SQL Server sur votre ordinateur Docker à partir de n’importe quel outil externe macOS, Windows ou Linux qui prend en charge les connexions SQL.

Les étapes suivantes utilisent **sqlcmd** en dehors de votre conteneur pour se connecter à SQL Server s’exécutant dans le conteneur. Ces étapes supposent que vous avez déjà les outils de ligne de commande SQL Server installés en dehors de votre conteneur. Les mêmes principaux s’appliquent lors de l’utilisation d’autres outils, mais le processus de connexion est unique à chaque outil.

1. Rechercher l’adresse IP de l’ordinateur qui héberge votre conteneur. Sur Linux, utilisez **ifconfig** ou **adresse ip**. Sous Windows, utilisez **ipconfig**.

1. Exécutez sqlcmd en spécifiant l’adresse IP et le port mappé vers le port 1433 dans votre conteneur. Dans cet exemple, qui est le port 1401 sur l’ordinateur hôte.

   ```bash
   sqlcmd -S 10.3.2.4,1401 -U SA -P '<YourPassword>'
   ```

   ```PowerShell
   sqlcmd -S 10.3.2.4,1401 -U SA -P "<YourPassword>"
   ```

1. Exécutez les commandes Transact-SQL. Lorsque vous avez terminé, tapez `QUIT`.

Autres outils courants pour vous connecter à SQL Server :

- [Code Visual Studio](sql-server-linux-develop-use-vscode.md)
- [SQL Server Management Studio (SSMS) sur Windows](sql-server-linux-develop-use-ssms.md)

## <a name="next-steps"></a>Étapes suivantes

Pour Explorer d’autres scénarios, telles que l’exécution de plusieurs conteneurs, la persistance des données et le dépannage, consultez [images de conteneur de configuration de SQL Server 2017 sur Docker](sql-server-linux-configure-docker.md).

Consultez également le [référentiel GitHub de docker de mssql](https://github.com/Microsoft/mssql-docker) des ressources, des commentaires et problèmes connus.

