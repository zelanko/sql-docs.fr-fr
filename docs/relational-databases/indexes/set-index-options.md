---
title: "D&#233;finir les options d&#39;index | Microsoft Docs"
ms.custom: ""
ms.date: "02/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-indexes"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ALLOW_ROW_LOCKS (option)"
  - "option SORT_IN_TEMPDB"
  - "DROP_EXISTING, clause"
  - "données volumineuses, index"
  - "PAD_INDEX"
  - "STATISTICS_NORECOMPUTE"
  - "option d’index MAXDOP, paramètre"
  - "options d'index [SQL Server]"
  - "MAXDOP (option d'index)"
  - "IGNORE_DUP_KEY (option)"
  - "ALLOW_PAGE_LOCKS (option)"
  - "ONLINE"
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# D&#233;finir les options d&#39;index
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette rubrique explique comment modifier les propriétés d'un index dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour modifier les propriétés d'un index, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les options suivantes sont immédiatement appliquées à l'index à l'aide de la clause SET de l'instruction ALTER INDEX : ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY et STATISTICS_NORECOMPUTE.  
  
-   Les options suivantes peuvent être définies lorsque vous reconstruisez un index à l'aide de ALTER INDEX REBUILD ou de CREATE INDEX WITH DROP_EXISTING : PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP, and DROP_EXISTING (CREATE INDEX uniquement).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite une autorisation ALTER sur la table ou la vue.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour modifier les propriétés d'un index dans le Concepteur de tables  
  
1.  Dans l'Explorateur d'objets, cliquez sur le signe plus (+) pour développer la base de données qui contient la table pour laquelle vous souhaitez modifier les propriétés d'un index.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Tables** .  
  
3.  Cliquez avec le bouton droit sur la table pour laquelle vous voulez modifier les propriétés d’un index et sélectionnez **Conception**.  
  
4.  Dans le menu **Concepteur de tables**, cliquez sur **Index/Clés**.  
  
5.  Sélectionnez l'index à modifier. Ses propriétés apparaîtront dans la grille principale.  
  
6.  Modifiez les paramètres de l'ensemble de propriétés pour personnaliser l'index.  
  
7.  Cliquez sur **Fermer**.  
  
8.  Dans le menu **Fichier**, sélectionnez **Enregistrer***nom_table*.  
  
#### Pour modifier les propriétés d'un index dans l'Explorateur d'objets  
  
1.  Dans l'Explorateur d'objets, cliquez sur le signe plus (+) pour développer la base de données qui contient la table pour laquelle vous souhaitez modifier les propriétés d'un index.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Tables** .  
  
3.  Cliquez sur le signe plus (+) pour développer la table pour laquelle vous souhaitez modifier les propriétés d'un index.  
  
4.  Cliquez sur le signe plus (+) pour développer le dossier **Index** .  
  
5.  Cliquez avec le bouton droit sur l’index dont vous voulez modifier les propriétés, puis sélectionnez **Propriétés**.  
  
6.  Sous **Sélectionner une page**, sélectionnez **Options**.  
  
7.  Modifiez les paramètres de l'ensemble de propriétés pour personnaliser l'index.  
  
8.  Pour ajouter, supprimer ou déplacer une colonne d’index, sélectionnez la page **Général** dans la boîte de dialogue **Propriétés de l’index -** *nom_index*. Pour plus d'informations, consultez [Index Properties F1 Help](../../relational-databases/indexes/index-properties-f1-help.md)  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour afficher les propriétés de tous les index d'une table  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### Pour définir les propriétés d'un index  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez les exemples suivants dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../relational-databases/indexes/codesnippet/tsql/set-index-options_1.sql)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../relational-databases/indexes/codesnippet/tsql/set-index-options_2.sql)]  
  
 Pour plus d’informations, consultez [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
  