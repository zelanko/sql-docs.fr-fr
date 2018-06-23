---
title: Créer des index cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- index creation [SQL Server], clustered indexes
- clustered indexes, creating
- clustered indexes, PRIMARY KEY constraint
- clustered indexes, UNIQUE constraint
- indexes [SQL Server], clustered
ms.assetid: 47148383-c2c7-4f08-a9e4-7016bf2d1d13
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6eba78c9d13d3f9de794495c4904f7a1ed43e348
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038345"
---
# <a name="create-clustered-indexes"></a>Créer des index cluster
  Vous pouvez créer des index cluster sur les tables dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. À quelques exceptions près, chaque table doit posséder un index cluster. Outre le fait qu'il améliore les performances des requêtes, un index cluster peut être reconstruit ou réorganisé à la demande pour contrôler la fragmentation de la table. Un index cluster peut également être créé sur une vue. (Les index cluster sont définis dans la rubrique [Description des index cluster et non-cluster](clustered-and-nonclustered-indexes-described.md).)  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Implémentations types](#Implementations)  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer un index cluster sur une table à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Implementations"></a> Implémentations types  
 Les index cluster sont implémentés des manières suivantes :  
  
-   **Contraintes PRIMARY KEY et UNIQUE**  
  
     La création d'une contrainte PRIMARY KEY entraîne la création automatique d'un index cluster unique sur la ou les colonnes pour autant qu'il n'existe pas encore d'index cluster dans la table ou qu'un index non-cluster unique n'ait pas été défini explicitement. La colonne clé primaire ne peut pas contenir de valeurs NULL.  
  
     Lorsque vous créez une contrainte UNIQUE, un index non-cluster unique est créé pour appliquer par défaut une contrainte UNIQUE. Vous pouvez spécifier un index cluster unique si aucun index cluster n'existe déjà sur la table.  
  
     Un index créé dans le cadre de la contrainte reçoit automatiquement le nom de celle-ci. Pour plus d'informations, consultez [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md) et [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
-   **Index indépendant d'une contrainte**  
  
     Vous pouvez créer un index cluster sur une autre colonne que la colonne clé primaire si une contrainte de clé primaire non-cluster a été spécifiée.  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Lorsqu'une structure d'index cluster est créée, l'ancienne structure (source) et la nouvelle structure (cible) requièrent de l'espace disque dans leurs fichiers et groupes de fichiers respectifs. L'ancienne structure n'est désallouée qu'une fois l'ensemble de la transaction validé. Il est également possible qu'une opération de tri nécessite de l'espace disque temporaire supplémentaire. Pour plus d’informations, consultez [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).  
  
-   Si un index cluster est créé sur un segment comprenant plusieurs index non-cluster, ces derniers doivent tous être reconstruits afin qu'ils contiennent la valeur de clé de clustering au lieu de l'identificateur de ligne (RID). De même, si un index cluster est supprimé d'une table comprenant plusieurs index non-cluster, ces derniers sont tous regénérés pendant l'opération de suppression (DROP). Cette opération peut prendre beaucoup de temps sur les tables volumineuses.  
  
     Il est préférable de construire des index sur des tables volumineuses en commençant par l'index cluster, puis de poursuivre avec les index non-cluster. Pensez à attribuer la valeur ON à l'option ONLINE lorsque vous créez des index sur des tables existantes. Lorsque cette option a pour valeur ON, les verrous de table à long terme ne sont pas maintenus. Ce paramétrage permet de poursuivre les interrogations ou les mises à jour de la table sous-jacente. Pour plus d'informations, consultez [Perform Index Operations Online](perform-index-operations-online.md).  
  
-   La clé d'un index cluster ne peut pas contenir de colonnes `varchar` qui possèdent des données dans l'unité d'allocation ROW_OVERFLOW_DATA. Si un index cluster est créé sur une colonne `varchar` et que les données existantes se trouvent dans l'unité d'allocation IN_ROW_DATA, les actions d'insertion ou de mise à jour réalisées ultérieurement sur la colonne et susceptibles d'envoyer les données hors ligne sont vouées à l'échec. Pour obtenir des informations sur les tables pouvant contenir des données de dépassement de ligne, utilisez la fonction de gestion dynamique [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite une autorisation ALTER sur la table ou la vue. L’utilisateur doit être membre du rôle serveur fixe **sysadmin** ou des rôles de base de données fixes **db_ddladmin** et **db_owner** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-clustered-index-by-using-object-explorer"></a>Pour créer un index cluster à l'aide de l'Explorateur d'objets  
  
1.  Dans l'Explorateur d'objets, développez la table sur laquelle vous souhaitez créer un index cluster.  
  
2.  Cliquez avec le bouton droit sur le dossier **Index** , pointez sur **Nouvel index**, puis sélectionnez **Index cluster...**.  
  
3.  Dans la boîte de dialogue **Nouvel index** , sur la page **Général** , entrez le nom du nouvel index dans la zone **Nom de l'index** .  
  
4.  Sous **Colonnes clés d'index**, cliquez sur **Ajouter…**.  
  
5.  Dans la boîte de dialogue **Sélectionnez les colonnes à partir de***nom_table*, cochez la case de la colonne de la table à ajouter à l’index cluster.  
  
6.  Cliquez sur **OK**.  
  
7.  Dans la boîte de dialogue **Nouvel index** , cliquez sur **OK**.  
  
#### <a name="to-create-a-clustered-index-by-using-the-table-designer"></a>Pour créer un index cluster à l'aide du Concepteur de tables  
  
1.  Dans l'Explorateur d'objets, développez la base de données sur laquelle vous souhaitez créer une table avec un index cluster.  
  
2.  Cliquez avec le bouton droit sur le dossier **Tables** et sélectionnez **Nouvelle table...**.  
  
3.  Créez une table comme vous le feriez normalement. Pour plus d’informations, consultez [Créer des tables &#40;moteur de base de données&#41;](../tables/create-tables-database-engine.md).  
  
4.  Cliquez avec le bouton droit sur la nouvelle table créée ci-dessus, puis sélectionnez **Conception**.  
  
5.  Dans le menu **Concepteur de tables** , cliquez sur **Index/Clés**.  
  
6.  Dans la boîte de dialogue **Index/Clés** , cliquez sur **Ajouter**.  
  
7.  Sélectionnez le nouvel index dans la zone de texte **Index ou clé unique/primaire sélectionné(e)** .  
  
8.  Dans la grille, sélectionnez **Créer comme Clustered**et choisissez **Oui** dans la liste déroulante à droite de la propriété.  
  
9. Cliquez sur **Fermer**.  
  
10. Dans le menu **Fichier**, cliquez sur **Enregistrer***nom_table*.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-clustered-index"></a>Pour créer un index cluster  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Create a new table with three columns.  
    CREATE TABLE dbo.TestTable  
        (TestCol1 int NOT NULL,  
         TestCol2 nchar(10) NULL,  
         TestCol3 nvarchar(50) NULL);  
    GO  
    -- Create a clustered index called IX_TestTable_TestCol1  
    -- on the dbo.TestTable table using the TestCol1 column.  
    CREATE CLUSTERED INDEX IX_TestTable_TestCol1   
        ON dbo.TestTable (TestCol1);   
    GO  
    ```  
  
 Pour plus d’informations, consultez [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des clés primaires](../tables/create-primary-keys.md)   
 [Créer des contraintes uniques](../tables/create-unique-constraints.md)  
  
  
