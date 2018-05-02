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
ms.openlocfilehash: a931ddb3cf3229970de4b301e18002484acbaf53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-script-objects-in-sql-server-management-studio"></a>Tutoriel : Générer des scripts d’objets dans SQL Server Management Studio
Ce tutoriel va vous apprendre à générer des scripts T-SQL (Transact-SQL) pour différents objets qui figurent dans SQL Server Management Studio.  Dans ce tutoriel, vous trouverez des exemples de génération de scripts pour les objets suivants : 

> [!div class="checklist"]
> * Requêtes lors de l’exécution d’actions dans l’interface graphique utilisateur
> * Bases de données de deux manières différentes (« Script comme » et « Générer des scripts »)
> * Tables
> * Procédures stockées
> * Événements étendus

En résumé, ce tutoriel montre que tous les objets de **l’Explorateur d’objets** peuvent être scriptés en cliquant dessus avec le bouton droit et en sélectionnant l’option **Scripter l’objet en tant que**. 


## <a name="prerequisites"></a>Prérequis
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio, de l’accès à un serveur SQL Server et d’une base de données AdventureWorks. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Téléchargez un [exemple de base de données AdventureWorks2016](https://github.com/Microsoft/sql-server-samples/releases). Les instructions de restauration des bases de données dans SSMS se trouvent ici : [Restauration d’une base de données](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


## <a name="script-queries-from-gui"></a>Générer des scripts pour les requêtes à partir de l’interface graphique utilisateur
Chaque fois que vous effectuez une tâche à l’aide de l’interface graphique utilisateur dans SSMS, vous pouvez également générer le code T-SQL associé à cette tâche. Les exemples suivants montrent comment procéder quand vous effectuez une sauvegarde d’une base de données et quand vous réduisez le journal des transactions.  Ces mêmes étapes peuvent être appliquées à une action effectuée via l’interface graphique utilisateur. 

### <a name="script-t-sql-when-backing-up-a-database"></a>Script T-SQL lors de la sauvegarde d’une base de données
1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données** .
3. Cliquez avec le bouton droit sur la base de données **Adventureworks2016** > **Tâches** > **Sauvegarder** :

    ![Sauvegarder la base de données](media/scripting-ssms/backupdb.png)

4. Configurez la sauvegarde comme vous le souhaitez. Dans le cadre de ce tutoriel, tous les éléments conservent les valeurs par défaut. Toutefois, toutes les modifications apportées dans la fenêtre seront également répercutées dans le script. 
5. Sélectionnez l’option **Script** > **Action de script dans une fenêtre de requête** :
 
    ![Script de sauvegarde de base de données](media/scripting-ssms/scriptdbbackup.PNG)
6. Passez en revue le script T-SQL rempli dans la fenêtre de requête : 

    ![Script pour la sauvegarde de base de données](media/scripting-ssms/dbbackupscript.PNG)
7. Sélectionnez **Exécuter** pour exécuter la requête permettant de sauvegarder la base de données via T-SQL. 


### <a name="script-t-sql-when-shrinking-the-transaction-log"></a>Script T-SQL lors de la réduction du journal des transactions
1. Cliquez avec le bouton droit sur la base de données**AdventureWorks2016** > **Tâches** > **Réduire** > **Fichiers** :

     ![Réduire les fichiers](media/scripting-ssms/shrinkfiles.png)

2. Sélectionnez **Journal** dans la liste déroulante **Type de fichier** :

    ![Réduire le journal des transactions](media/scripting-ssms/shrinktlog.png)

3. Sélectionnez l’option **Script** et sur **Action de script dans le Presse-papiers** :

    ![Générer un script sur le Presse-papiers](media/scripting-ssms/scriptactiontoclipboard.png)

4. Ouvrez une fenêtre **Nouvelle requête** et sélectionnez Coller (cliquez avec le bouton droit dans la fenêtre > **Coller**) :

    ![Coller le script](media/scripting-ssms/paste.png)
5. Sélectionnez **Exécuter** pour exécuter la requête et réduire le journal des transactions. 


## <a name="script-databases"></a>Scripter des bases de données
La section suivante vous apprend à générer le script de la base de données à l’aide des options **Script comme** et **Générer des scripts**.  L’option **Script comme** recrée la base de données et les options de configuration associées. L’option **Générer des scripts** vous permet de scripter à la fois le schéma et les données. Dans cette section, vous allez créer deux nouvelles bases de données : *AdventureWorks2016a* à créer avec l’option **Script comme**. *AdventureWorks2016b* à créer avec l’option **Générer des scripts**. 


### <a name="script-database-using-script-option"></a>Générer le script de la base de données à l’aide de l’option Script comme
1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données** .
3. Cliquez avec le bouton droit sur la base de données **AdventureWorks2016** > **Scripter la base de données comme** > **Créer dans** > **Nouvelle fenêtre de requête** :

    ![Scripter une base de données](media/scripting-ssms/scriptdb.png)

4. Passez en revue la requête de création de base de données dans la fenêtre : 

    ![Base de données scriptée](media/scripting-ssms/scriptedoutdb.png)
    - Cette option scripte uniquement les options de configuration de la base de données.
5. Sur votre clavier, sélectionnez **Ctrl + F** pour ouvrir la boîte de dialogue **Rechercher** et sélectionnez la flèche vers le bas pour ouvrir l’option **Remplacer**. Sur la ligne **Rechercher** en haut, tapez *AdventureWorks2016* et sur la ligne **Remplacer** en bas, tapez *AdventureWorks2016a*. 
6. Sélectionnez **Remplacer tout** pour remplacer toutes les instances de *AdventureWorks2016* par *AdventureWorks2016a*. 

    ![Rechercher et remplacer](media/scripting-ssms/findandreplace.png)

1. Sélectionnez **Exécuter** pour exécuter la requête et créer votre nouvelle base de données *AdventureWorks2016a*. 

### <a name="script-database-using-generate-scripts-option"></a>Scripter la base de données à l’aide de l’option Générer des scripts
1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données** .
3. Cliquez avec le bouton droit sur la base de données **AdventureWorks2016** > **Tâches** > **Générer des scripts** :

    ![Générer des scripts pour la base de données](media/scripting-ssms/generatescriptsfordb.png)

4. La page **Introduction** s’ouvre, sélectionnez **Suivant** pour ouvrir la page **Choisir des objets**. Vous pouvez sélectionner la base de données entière ou des objets spécifiques de la base de données. Sélectionner l’option pour **scripter la base de données entière et tous ses objets** 
 
    ![Générer des scripts pour les objets](media/scripting-ssms/scriptobjects.png)
 
5. Sélectionnez **Suivant** pour ouvrir la page **Définir les options de script**, dans laquelle vous pouvez configurer où enregistrer le script ainsi que des options avancées supplémentaires. 

    A. Sélectionnez l’option **Enregistrer dans une nouvelle fenêtre de requête**. 

    B. Sélectionnez **Avancé** et vérifiez que ces options sont définies : 

      - **Générer un script pour les statistiques** défini sur *Générer un script pour les statistiques*
      - **Types de données à scripter** défini sur *Schéma uniquement*
      - **Générer un script pour les index** défini sur *true*

   ![Scripter des objets](media/scripting-ssms/advancedscripts.png)

   > [!NOTE]
   > Vous avez la possibilité de scripter les données de la base de données lorsque vous sélectionnez *Schéma et données* pour l’option **Types de données à scripter**. Toutefois, ce n’est pas idéal avec les grandes bases de données, car l’opération peut prendre plus de mémoire que SSMS ne peut en allouer. Cela fonctionne pour les petites bases de données, mais si vous souhaitez déplacer les données d’une plus grande base de données, vous devez utiliser l’[Assistant Importation et exportation](https://docs.microsoft.com/en-us/sql/integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard).



1. Sélectionnez **OK**, puis **Suivant**. 
2. Sélectionnez **Suivant** dans le **Résumé**, puis sélectionnez **Suivant** pour générer le script dans une fenêtre **Nouvelle requête**.  
3. Sur votre clavier, sélectionnez **Ctrl + F** pour ouvrir la boîte de dialogue **Rechercher** et sélectionnez la flèche vers le bas pour ouvrir l’option **Remplacer**. Sur la ligne **Rechercher** en haut, tapez *AdventureWorks2016* et sur la ligne **Remplacer** en bas, tapez *AdventureWorks2016b*. 
    A. Sélectionnez **Remplacer tout** pour remplacer toutes les instances de *AdventureWorks2016* par *AdventureWorks2016b*. 

    ![AdventureWorks2016b](media/scripting-ssms/adventureworks2016b.png)
7. Sélectionnez **Exécuter** pour exécuter la requête et créer votre nouvelle base de données *AdventureWorks2016b*. 
 
## <a name="script-tables"></a>Scripter des tables
Cette section explique comment scripter les tables de votre base de données. À l’aide de cette option, vous pouvez créer la table, ou supprimer et créer la table. Vous pouvez aussi utiliser cette option pour générer un script du code T-SQL associé à la modification de la table, par exemple pour des opération d’insertion ou de mise à jour. Dans cette section, vous allez supprimer une table, puis la recréer. 

1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données**.
3. Développez le nœud de base de données **AdventureWorks**. 
4. Développez le nœud **Tables**.
5. Cliquez avec le bouton droit sur **dbo.ErrorLog** >  **Scripter la table comme** > **Supprimer et créer dans** > **Nouvelle fenêtre d'éditeur de requête** :
    
    ![Scripter la table](media/scripting-ssms/scripttable.png)

6. Sélectionnez **Exécuter** pour exécuter la requête, ce qui supprime la table *Errorlog* et la recrée. 

    >[!NOTE]
    > La table *Errorlog* est vide par défaut dans la base de données AdventureWorks2016, donc vous ne perdez aucune donnée en supprimant la table. Toutefois, la réalisation de ces étapes sur une table avec des données entraîne une perte de données. 
 
## <a name="script-stored-procedures"></a>Scripter des procédures stockées
Dans cette section, vous allez apprendre à supprimer et à créer une procédure stockée.  

1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Bases de données**.
3. Développez le nœud **Programmabilité**. 
4. Développez le nœud **Procédure stockée**.
5. Cliquez avec le bouton droit sur la procédure stockée **dbo.uspGetBillOfMaterials**> **Scripter la procédure stockée comme** > **Supprimer et créer dans** > **Nouvelle fenêtre de requête** :
    
    ![Scripter des procédures stockées](media/scripting-ssms/scriptstoredprocedure.PNG)

## <a name="script-extended-events"></a>Scripter des événements étendus
Cette section explique comment scripter des [événements étendus](https://docs.microsoft.com/en-us/sql/relational-databases/extended-events/extended-events). 

1. Connectez-vous à votre serveur SQL Server.
2. Développez le nœud **Gestion**.
3. Développez le nœud **Événements étendus**.
4. Développez le nœud **Sessions**.
5. Cliquez avec le bouton droit sur la session étendue qui vous intéresse > **Scripter une session comme** > **Nouvelle fenêtre d'éditeur de requête** :

    ![Scripter des événements XEvent](media/scripting-ssms/scriptxevents.png) 
6. Dans la **nouvelle fenêtre de requête**, remplacez le nouveau nom de la session *system_health* par *system_health2* et sélectionnez **Exécuter** pour exécuter la requête. 

    A. Cliquez avec le bouton droit sur **Sessions** dans **l’Explorateur d’objets** et sélectionnez **Actualiser** pour voir votre nouvelle session d’événements étendus. L’icône verte à côté de la session indique que la session est en cours d’exécution tandis que l’icône rouge indique que la session est arrêtée. 

    ![Nouveau événement xEvent](media/scripting-ssms/newxevent.png)

    >[!NOTE]
    > Vous pouvez démarrer la session en cliquant avec le bouton droit et en sélectionnant **Démarrer**. Toutefois, puisqu’il s’agit d’une copie de la session *system_health* déjà en cours, cette étape peut être ignorée. Vous pouvez supprimer la copie de la session d’événements étendus en cliquant avec le bouton droit et en sélectionnant **Supprimer**. 

## <a name="next-steps"></a>Étapes suivantes
L’article suivant vous présente les modèles T-SQL prédéfinis qui figurent dans SSMS. 

Passez à l’article suivant pour en savoir plus :
> [!div class="nextstepaction"]
> [Étapes suivantes](templates-ssms.md)


