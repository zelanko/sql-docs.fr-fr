---
Title: 'Tutorial: Additional Tips and Tricks for using SSMS'
description: 'Tutoriel qui couvre quelques conseils et astuces supplémentaires sur l’utilisation de SSMS. '
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
ms.openlocfilehash: e358fb73ff4f248b7de368364b8bb758f70018ff
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="tutorial-additional-tips-and-tricks-for-using-ssms"></a>Tutoriel : Conseils et astuces supplémentaires sur l’utilisation de SSMS
Ce tutoriel vous propose des astuces supplémentaires sur l’utilisation de SQL Server Management Studio. Cet article va vous apprendre à : 

> [!div class="checklist"]
> * Ajouter et supprimer des commentaires dans le texte T-SQL (Transact-SQL)
> * Mettre en retrait du texte
> * Filtrer des objets dans l’Explorateur d’objets
> * Accéder à votre journal des erreurs SQL Server
> * Rechercher le nom de votre instance de SQL Server

## <a name="prerequisites"></a>Conditions préalables requises
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio, de l’accès à un serveur SQL Server et d’une base de données AdventureWorks. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Téléchargez un [exemple de base de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Les instructions de restauration des bases de données dans SSMS se trouvent ici : [Restauration d’une base de données](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 

## <a name="comment--uncomment-your-t-sql-code"></a>Ajouter / supprimer des commentaires dans votre code T-SQL
Il est possible d’ajouter et de supprimer des commentaires dans des parties de votre texte à l’aide du bouton Commentaire de la barre d’outils. Le texte qui est commenté ne sera pas exécuté. 

1. Ouvrez SQL Server Management Studio. 
2. Connectez-vous à votre serveur SQL Server.
3. Ouvrez une fenêtre **Nouvelle requête**. 
4. Collez l’extrait de code T-SQL suivant dans la fenêtre du texte : 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 


5. Mettez en surbrillance la partie **ALTER DATABASE** du texte et cliquez sur **Commentaire** dans la barre d’outils : 

    ![Commentaire](media/ssms-tricks/comment.png)
6. Cliquez sur **Exécuter** pour exécuter la partie sans commentaire du texte. 
7. Mettez en surbrillance tous les éléments autres que la commande **ALTER DATABASE** et cliquez sur **Commentaire** dans la barre d’outils :

    ![Tout commenter](media/ssms-tricks/commenteverything.png)

8. Mettez en surbrillance la partie **ALTER DATABASE**, puis cliquez sur **Uncomment** (Annuler le commentaire) pour supprimer les commentaires :

    ![Annuler le commentaire](media/ssms-tricks/uncomment.png)
    
9. Cliquez sur **Exécuter** pour exécuter la partie sans commentaire du texte. 

## <a name="indent-your-text"></a>Mettre en retrait du texte
Les boutons de mise en retrait vous permettent d’augmenter et de réduire le retrait du texte. 

1. Ouvrez une fenêtre **Nouvelle requête**. 
2. Collez l’extrait de code T-SQL suivant dans la fenêtre du texte : 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 
 
3. Mettez en surbrillance la partie **ALTER DATABASE** du texte et appuyez sur **Augmenter le retrait** dans la barre d’outils pour déplacer ce texte vers l’avant :

    ![Augmenter le retrait](media/ssms-tricks/increaseindent.png)

4. Mettez à nouveau en surbrillance la partie **ALTER DATABASE** du texte et, cette fois, cliquez sur **Réduire le retrait** pour déplacer ce texte vers l’arrière. 
    ![Réduire le retrait](media/ssms-tricks/decreaseindent.png)


## <a name="filter-objects-in-object-explorer"></a>Filtrer des objets dans l’Explorateur d’objets
Quand une base de données comprend un grand nombre d’objets, il peut être difficile de trouver un objet spécifique. Pour faciliter cette opération, vous avez la possibilité de filtrer les objets. Cette section explique comment filtrer les tables, mais les mêmes étapes peuvent être appliquées à tout autre nœud dans **l’Explorateur d’objets**

1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données**.
3. Développez le nœud de base de données **AdventureWorks**. 
4. Développez le nœud **Tables**. 
   - Vous remarquerez que vous pouvez voir toutes les tables qui sont présentes dans la base de données.
5. Cliquez avec le bouton droit sur le nœud **Tables** > **Filtre** > **Paramètres du filtre** :

    ![Paramètres du filtre](media/ssms-tricks/filtersettings.png)

6. Dans la fenêtre Paramètres du filtre, vous pouvez modifier les paramètres du filtre. Voici quelques exemples :
    - Filtrer par nom : ![Filtrer par nom](media/ssms-tricks/filterbyname.png)
    - Filtrer par schéma : ![Filtrer par schéma](media/ssms-tricks/filterbyschema.png)

7. Pour effacer le filtre, cliquez avec le bouton droit sur **Tables** > **Supprimer le filtre**

    ![Supprimer le filtre](media/ssms-tricks/removefilter.png)
    


## <a name="access-your-sql-server-error-log"></a>Accéder à votre journal des erreurs SQL Server
Le journal des erreurs est un fichier qui contient des détails sur les éléments qui se produisent sur votre serveur SQL Server. Il peut être parcouru et interrogé dans SSMS. Il peut également figurer sous forme de fichier .log sur le disque.

### <a name="open-error-log-within-ssms"></a>Ouvrir le journal des erreurs dans SSMS
1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Gestion** . 
3. Développez le nœud **Journaux SQL Server**. 
4. Cliquez avec le bouton droit sur le journal des erreurs **actuel** > **Afficher le journal SQL Server** :

    ![Afficher le journal des erreurs dans SSMS](media/ssms-tricks/viewerrorloginssms.png)

### <a name="query-error-log-within-ssms"></a>Interroger le journal des erreurs dans SSMS
1. Connectez-vous à votre serveur SQL Server.
2. Ouvrez une fenêtre **Nouvelle requête**.
3. Collez l’extrait de code T-SQL suivant dans la fenêtre de requête :

 ```sql
   sp_readerrorlog 0,1,'Server process ID' 
  ``` 
4. Remplacez le texte entre guillemets simples par le texte voulu.
5. Exécutez la requête et passez en revue les résultats :
   
    ![Interroger le journal des erreurs](media/ssms-tricks/queryerrorlog.png)


### <a name="find-error-log-location-if-youre-connected-to-sql"></a>Rechercher l’emplacement du journal des erreurs si vous êtes connecté à SQL
1. Connectez-vous à votre serveur SQL Server.
2. Ouvrez une fenêtre **Nouvelle requête**.
3. Collez l’extrait de code T-SQL suivant dans la fenêtre de requête, puis cliquez sur **Exécuter** :

 ```sql
    SELECT SERVERPROPERTY('ErrorLogFileName') AS 'Error log file location'  
  ``` 

4. Les résultats indiquent l’emplacement du journal des erreurs dans le système de fichiers : 

    ![Rechercher le journal des erreurs par requête](media/ssms-tricks/finderrorlogquery.png)

### <a name="find-error-log-location-if-you-cannot-connect-to-sql"></a>Rechercher l’emplacement du journal des erreurs si vous ne pouvez pas vous connecter à SQL
1. Ouvrez le Gestionnaire de configuration SQL Server. 
2. Développez le nœud **Services**.
3. Cliquez avec le bouton droit sur votre instance de SQL Server > **Propriétés** :

    ![Propriétés du Gestionnaire de configuration SQL Server](media/ssms-tricks/serverproperties.PNG)

4. Sélectionnez l’onglet **Paramètres de démarrage**.
5. Dans la zone **Paramètres existants**, le chemin après le « -e » correspond à l’emplacement du journal des erreurs : 
    
    ![Journal des erreurs de SQL Server](media/ssms-tricks/errorlog.png)
    - Vous remarquerez la présence de plusieurs errorlog.* à cet emplacement. Celui se terminant par *.log représente le journal actuel. Ceux se terminant par des numéros sont les journaux précédents, car un journal est créé chaque fois que SQL Server redémarre. 
6. Ouvrez ce fichier dans le Bloc-notes. 

## <a name="determine-sql-server-name"></a>Déterminer le nom du serveur SQL Server...
Il existe différentes façons de déterminer le nom de votre serveur SQL Server avant et après la connexion à votre serveur SQL Server.  

### <a name="when-you-dont-know-it"></a>...quand vous ne le connaissez pas
1. Suivez la procédure pour localiser le [journal des erreurs SQL Server sur le disque](#finding-your-error-log-if-you-cannot-connect-to-sql). 
2. Ouvrez le fichier errorlog.log dans le Bloc-notes. 
3. Parcourez-le jusqu’à ce que vous trouviez le texte « Le nom du serveur est » :
  - Ce qui figure entre guillemets simples est le nom du serveur SQL Server et votre connexion : ![Nom du serveur dans le journal des erreurs](media/ssms-tricks/servernameinlog.png). Le format du nom est 'HOSTNAME\INSTANCENAME'. Si vous ne voyez que le nom d’hôte, cela signifie que vous avez installé l’instance par défaut et que le nom de votre instance est 'MSSQLSERVER'. Lors de la connexion à une instance par défaut, il vous suffit de taper le nom d’hôte pour vous connecter à votre serveur SQL Server.  

### <a name="once-youre-connected-to-sql"></a>...une fois que vous êtes connecté à SQL 
Il existe trois emplacements où rechercher le serveur SQL Server auquel vous êtes connecté. 

1. Le nom du serveur s’affiche dans **l’Explorateur d’objets** :

    ![Nom de l’instance dans l’Explorateur d’objets](media/ssms-tricks/nameinobjectexplorer.png)
2. Le nom du serveur s’affiche dans la fenêtre de requête :

    ![Nom dans la fenêtre de requête](media/ssms-tricks/nameinquerywindow.png)
3. Le nom du serveur s’affiche également dans la **fenêtre Propriétés**.
    - Pour y accéder, ouvrez le menu **Affichage** > **Fenêtre Propriétés** :

    ![Nom dans la fenêtre Propriétés](media/ssms-tricks/nameinproperties.png)

### <a name="if-youre-connected-to-an-alias-or-availability-group-listener"></a>...si vous êtes connecté à un alias ou un écouteur de groupe de disponibilité 
Quand vous êtes connecté à un alias ou un écouteur de groupe de disponibilité, il s’agit de l’élément affiché par **l’Explorateur d’objets** et la fenêtre  **Propriétés**. Dans ce cas, le nom SQL Server n’est peut-être pas visible et doit être interrogé. 

1. Connectez-vous à SQL Server.
2. Ouvrez une fenêtre **Nouvelle requête**.
3. Collez l’extrait de code T-SQL suivant dans la fenêtre : 

  ```sql
   select @@Servername 
 ``` 
4. Affichez les résultats de la requête pour identifier le nom du serveur SQL Server auquel vous êtes connecté : 
    
    ![Nom du serveur de requête](media/ssms-tricks/queryservername.png)


