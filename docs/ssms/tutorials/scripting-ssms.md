---
Title: 'Tutorial: Script Objects in SQL Server Management Studio'
description: Tutoriel pour la génération de scripts d’objets dans SSMS.
keywords: SQL Server, SSMS, SQL Server Management Studio, scripts, génération de scripts
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.openlocfilehash: bc20cc573c6b0890e5b16f4876636534f9fbb916
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-script-objects-in-sql-server-management-studio"></a>Tutoriel : Scripter des objets dans SQL Server Management Studio
Ce tutoriel va vous apprendre à générer des scripts T-SQL (Transact-SQL) pour différents objets qui figurent dans SQL Server Management Studio.  Dans ce tutoriel, vous trouverez des exemples de génération de scripts pour les objets suivants : 

> [!div class="checklist"]
> * Requêtes lors de l’exécution d’actions dans l’interface graphique utilisateur
> * Bases de données de deux manières différentes (« Scripter en tant que » et « Générer des scripts »)
> * Tables
> * Procédures stockées
> * Événements étendus

Le résumé de ce tutoriel est que tout objet dans **l’Explorateur d’objets** peut être scripté en cliquant dessus avec le bouton droit et en sélectionnant l’option **Scripter l’objet en tant que**. 


## <a name="prerequisites"></a>Prérequis
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio, de l’accès à un serveur SQL Server et d’une base de données AdventureWorks. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Téléchargez un [exemple de base de données AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Les instructions de restauration des bases de données dans SSMS se trouvent ici : [Restauration d’une base de données](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


## <a name="script-queries-from-gui"></a>Scripter des requêtes à partir de l’interface graphique utilisateur
Chaque fois que vous effectuez une tâche à l’aide de l’interface graphique utilisateur dans SSMS, vous pouvez également générer le code T-SQL associé à cette tâche. Les exemples suivants montrent comment procéder quand vous effectuez une sauvegarde d’une base de données et quand vous réduisez le journal des transactions.  Ces mêmes étapes peuvent être appliquées à une action effectuée via l’interface graphique utilisateur. 

### <a name="script-t-sql-when-backing-up-a-database"></a>Script T-SQL lors de la sauvegarde d’une base de données
1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données** .
3. Cliquez avec le bouton droit sur la base de données > **Tâches** > **Sauvegarder** :

    ![Sauvegarder la base de données](media/scripting-ssms/backupdb.png)

4. Configurez la sauvegarde comme vous le souhaitez. Dans le cadre de ce tutoriel, tous les éléments conservent les valeurs par défaut. Toutefois, toutes les modifications apportées dans la fenêtre seront également répercutées dans le script. 
5. Cliquez sur l’option **Script** > **Action de script dans une nouvelle fenêtre de requête** :
 
    ![Script de sauvegarde de base de données](media/scripting-ssms/scriptdbbackup.PNG)
6. Passez en revue le script T-SQL rempli dans la fenêtre de requête : 

    ![Script pour la sauvegarde de base de données](media/scripting-ssms/dbbackupscript.PNG)


### <a name="script-t-sql-when-shrinking-the-transaction-log"></a>Script T-SQL lors de la réduction du journal des transactions
1. Cliquez avec le bouton droit sur la base de données > **Tâches** > **Réduire** > **les fichiers** :

     ![Réduire les fichiers](media/scripting-ssms/shrinkfiles.png)

2. Sélectionnez **Journal** dans la liste déroulante **Type de fichier** :

    ![Réduire le journal des transactions](media/scripting-ssms/shrinktlog.png)

3. Cliquez sur l’option **Script** et sur **Action de script dans le Presse-papiers** :

    ![Scripter sur le Presse-papiers](media/scripting-ssms/scriptactiontoclipboard.png)

4. Ouvrez une fenêtre **Nouvelle requête** et sélectionnez Coller (cliquez avec le bouton droit dans la fenêtre > **Coller**) :

    ![Coller le script](media/scripting-ssms/paste.png)


## <a name="script-databases"></a>Scripter des bases de données
La section suivante vous apprend à scripter la base de données à l’aide des options **Scripter en tant que** et **Générer des scripts**.  L’option **Script comme** recrée la base de données et les options de configuration associées. L’option **Générer des scripts** génère le script de tous les objets dans la base de données, mais pas des données. Pour générer également le script des données, vous devez utiliser [l’Assistant Importation et Exportation](https://docs.microsoft.com/en-us/sql/integration-services/import-export-data/start-the-sql-server-import-and-export-wizard).  


### <a name="script-database-using-script-option"></a>Scripter la base de données à l’aide de l’option Scripter en tant que
1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données** .
3. Cliquez avec le bouton droit sur la base de données > **Scripter la base de données en tant que** :

    ![Scripter une base de données](media/scripting-ssms/scriptdb.png)

4. Passez en revue la requête de création de base de données dans la fenêtre : 

    ![Base de données scriptée](media/scripting-ssms/scriptedoutdb.png)
    - Cette option scripte uniquement les options de configuration de la base de données.  

### <a name="script-database-using-generate-scripts-option"></a>Scripter la base de données à l’aide de l’option Générer des scripts
1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données** .
3. Cliquez avec le bouton droit sur la base de données > **Tâches** > **Générer des scripts** :

    ![Générer des scripts pour la base de données](media/scripting-ssms/generatescriptsfordb.png)

4. Sélectionnez **Suivant** et vous verrez que vous pouvez choisir de scripter la base de données entière ou des objets spécifiques au sein de la base de données : 
 
    ![Générer des scripts pour les objets](media/scripting-ssms/scriptobjects.png)
 
5. Sélectionnez **Suivant**. Cet écran vous permet de configurer l’emplacement dans lequel le script doit être enregistré. 
    - Vous pouvez également configurer des options avancées en sélectionnant **Options avancées** :

    ![Options de script avancées](media/scripting-ssms/advancedscripts.png)

6. Une fois que vous êtes prêt à poursuivre, continuez à cliquer sur **Suivant** jusqu’à ce que les scripts soient générés et que vous accédiez à **Terminer**. Votre script de base de données se trouve à l’emplacement où il a été enregistré à l’étape 5. 
    - Le schéma et différents objets de la base de données sont ainsi scriptés, mais pas les données. 
 
## <a name="script-tables"></a>Scripter des tables
Cette section explique comment scripter les tables de votre base de données.

1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données**.
3. Développez le nœud de base de données **AdventureWorks**. 
4. Développez le nœud **Tables**.
5. Cliquez avec le bouton droit sur la table que vous voulez scripter > **Scripter une table en tant que** :
    - À ce stade, il existe différentes options telles que la création de la table ou l’ajout de données à la table : 
    
    ![Scripter la table](media/scripting-ssms/scripttable.png)
 
## <a name="script-stored-procedures"></a>Scripter des procédures stockées
Cette section explique comment scripter des procédures stockées. 

1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données**.
3. Développez le nœud **Programmabilité**. 
4. Développez le nœud **Procédure stockée**.
5. Cliquez avec le bouton droit sur la procédure stockée qui vous intéresse > **Scripter une procédure stockée en tant que** :
    
    ![Scripter des procédures stockées](media/scripting-ssms/scriptstoredprocedure.PNG)

## <a name="script-extended-events"></a>Scripter des événements étendus
Cette section explique comment scripter des [événements étendus](https://docs.microsoft.com/en-us/sql/relational-databases/extended-events/extended-events). 

1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Gestion**.
3. Développez le nœud **Événements étendus**.
4. Développez le nœud **Sessions**.
5. Cliquez avec le bouton droit sur la session étendue qui vous intéresse > **Scripter une session en tant que** :

    ![Scripter des événements XEvent](media/scripting-ssms/scriptxevents.png) 

## <a name="next-steps"></a>Étapes suivantes
L’article suivant vous présente les modèles prédéfinis qui figurent dans SSMS. 

Passez à l’article suivant pour en savoir plus
> [!div class="nextstepaction"]
> [Bouton Étapes suivantes](templates-ssms.md)


