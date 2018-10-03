---
title: Afficher les dépendances d’une procédure stockée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 14f380f510070da1b8fa77f7f5440640ce37452b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224419"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a>Afficher les dépendances d'une procédure stockée
    
##  <a name="Top"></a> Cette rubrique explique comment afficher les dépendances des procédures stockées dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour afficher les dépendances d’une procédure, avec :**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Fonction système : `sys.dm_sql_referencing_entities`  
 Requiert l'autorisation CONTROL sur l'entité référencée et l'autorisation SELECT sur sys.dm_sql_referencing_entities. Lorsque l'entité référencée est une fonction de partition, l'autorisation CONTROL sur la base de données est requise. Par défaut, l'autorisation SELECT est accordée à public.  
  
 Fonction système : `sys.dm_sql_referenced_entities`  
 Requiert l'autorisation SELECT sur sys.dm_sql_referenced_entities et l'autorisation VIEW DEFINITION sur l'entité de référence. Par défaut, l'autorisation SELECT est accordée à public. Requiert l'autorisation VIEW DEFINITION sur la base de données ou l'autorisation ALTER DATABASE DDL TRIGGER sur la base de données lorsque l'entité de référence est un déclencheur DDL au niveau de la base de données. Requiert l'autorisation VIEW ANY DEFINITION sur le serveur lorsque l'entité de référence est un déclencheur DDL au niveau du serveur.  
  
 Affichage catalogue d'objets : `sys.sql_expression_dependencies`  
 Requiert l'autorisation VIEW DEFINITION sur la base de données et l'autorisation SELECT sur sys.sql_expression_dependencies pour la base de données. Par défaut, l'autorisation SELECT est accordée uniquement aux membres du rôle de base de données fixe db_owner. Lorsque les autorisations SELECT et VIEW DEFINITION sont accordées à un autre utilisateur, le bénéficiaire peut consulter toutes les dépendances dans la base de données.  
  
##  <a name="Procedures"></a> Pour afficher les dépendances d'une procédure stockée  
 Vous pouvez utiliser l'un des éléments suivants :  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher les dépendances d'une procédure dans l'Explorateur d'objets**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure, puis développez **Programmabilité**.  
  
3.  Développez **Procédures stockées**, cliquez avec le bouton droit sur la procédure, puis cliquez sur **Afficher les dépendances**.  
  
4.  Examinez la liste des objets qui dépendent de la procédure.  
  
5.  Examinez la liste des objets dont dépend la procédure.  
  
6.  Cliquez sur **OK**.  
  
###  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher les dépendances d'une procédure dans l'Éditeur de requête**  
  
 Fonction système : `sys.dm_sql_referencing_entities`  
 Cette fonction est utilisée pour afficher les objets qui dépendent d'une procédure.  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure.  
  
3.  Dans le menu **Fichier** , cliquez sur **Nouvelle requête** .  
  
4.  Copiez et collez les exemples suivants dans l'éditeur de requête. Le premier exemple crée la procédure `uspVendorAllInfo` qui retourne le nom de tous les fournisseurs dans la base de données [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] , les produits qu'ils vendent, leurs conditions de crédit et leur disponibilité.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  Une fois la procédure créée, le deuxième exemple utilise la fonction sys.dm_sql_referencing_entities pour afficher les objets qui dépendent de la procédure.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 Fonction système : `sys.dm_sql_referenced_entities`  
 Cette fonction est utilisée pour afficher les objets dont la procédure dépend.  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure.  
  
3.  Dans le menu **Fichier** , cliquez sur **Nouvelle requête** .  
  
4.  Copiez et collez les exemples suivants dans l'éditeur de requête. Le premier exemple crée la procédure `uspVendorAllInfo` qui retourne le nom de tous les fournisseurs dans la base de données [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] , les produits qu'ils vendent, leurs conditions de crédit et leur disponibilité.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  Une fois la procédure créée, le deuxième exemple utilise la fonction sys.dm_sql_referenced_entities pour afficher les objets dont dépend la procédure.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 Affichage catalogue d'objets : `sys.sql_expression_dependencies`  
 Cette vue peut être utilisée pour afficher des objets dont une procédure dépend ou qui dépendent d'une procédure.  
  
 Affichage des objets qui dépendent d'une procédure.  
 1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure.  
  
3.  Dans le menu **Fichier** , cliquez sur **Nouvelle requête** .  
  
4.  Copiez et collez les exemples suivants dans l'éditeur de requête. Le premier exemple crée la procédure `uspVendorAllInfo` qui retourne le nom de tous les fournisseurs dans la base de données [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] , les produits qu'ils vendent, leurs conditions de crédit et leur disponibilité.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  Une fois la procédure créée, le deuxième exemple utilise la fonction sys.sql_expression_dependencies pour afficher les objets qui dépendent de la procédure.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 Affichage des objets dont une procédure dépend.  
 1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure.  
  
3.  Dans le menu **Fichier** , cliquez sur **Nouvelle requête** .  
  
4.  Copiez et collez les exemples suivants dans l'éditeur de requête. Le premier exemple crée la procédure `uspVendorAllInfo` qui retourne le nom de tous les fournisseurs dans la base de données [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] , les produits qu'ils vendent, leurs conditions de crédit et leur disponibilité.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  Une fois la procédure créée, le deuxième exemple utilise la fonction sys.sql_expression_dependencies pour afficher les objets dont dépend la procédure.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Renommer une procédure stockée](rename-a-stored-procedure.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
