---
title: Afficher la définition d’une procédure stockée | Microsoft Docs
description: Découvrez comment afficher la définition d’une procédure dans l’Explorateur d’objets, et dans l’éditeur de requête à l’aide d’une procédure stockée système, d’une fonction système et d’un affichage catalogue d’objets.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 10b39b46beeb3add46e56065f5671dbfedd9ed2b
ms.sourcegitcommit: 75f767c7b1ead31f33a870fddab6bef52f99906b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87332539"
---
# <a name="view-the-definition-of-a-stored-procedure"></a>Afficher la définition d'une procédure stockée
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
    
##  <a name="view-the-definition-of-a-stored-procedure"></a><a name="Top"></a> Afficher la définition d'une procédure stockée 

Cette rubrique décrit comment afficher la définition de la procédure dans l'Explorateur d'objets et en utilisant une procédure stockée système, une fonction système et un affichage catalogue d'objets dans l'éditeur de requête.  
  
-   **Avant de commencer :**  [Sécurité](#Security)  
  
-   **Pour afficher la définition d'une procédure, à l'aide de :**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Procédure stockée système : **sp_helptext**  
 Nécessite l'appartenance au rôle **public** . Les définitions de l'objet système sont visibles publiquement. La définition des objets utilisateur est visible par le propriétaire de l’objet ou les bénéficiaires de l’une des autorisations suivantes : ALTER, CONTROL, TAKE OWNERSHIP ou VIEW DEFINITION.  
  
 Fonction système :  **OBJECT_DEFINITION**  
 Les définitions de l'objet système sont visibles publiquement. La définition des objets utilisateur est visible par le propriétaire de l’objet ou les bénéficiaires de l’une des autorisations suivantes : ALTER, CONTROL, TAKE OWNERSHIP ou VIEW DEFINITION. Ces autorisations sont implicitement possédées par des membres des rôles de base de données fixes **db_owner**, **db_ddladmin**et **db_securityadmin** .  
  
 Affichage catalogue d’objet : **sys.sql_modules**  
 La visibilité des métadonnées dans les affichages catalogue est limitée aux éléments sécurisables qu'un utilisateur détient ou pour lesquels des autorisations lui ont été accordées. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
##  <a name="how-to-view-the-definition-of-a-stored-procedure"></a><a name="Procedures"></a> Comment afficher la définition d'une procédure stockée  
 Vous pouvez utiliser l'un des éléments suivants :  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour afficher la définition d'une procédure dans l'Explorateur d'objets**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, développez la base de données à laquelle appartient la procédure, puis développez **Programmabilité**.  
  
3.  Développez **Procédures stockées**, cliquez avec le bouton de droite sur la procédure, puis cliquez sur **Script de procédure stockée en tant que**, puis cliquez sur l'une des options suivantes : **Créer dans**, **Modifier dans** ou **Déposer et créer dans**.  
  
4.  Sélectionnez **Nouvelle fenêtre d’éditeur de requête**. Cette action affiche la définition de la procédure.  

###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour afficher la définition d'une procédure dans l'éditeur de requête**  
  
 Procédure stockée système : **sp_helptext**  
 1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, entrez l’instruction suivante qui utilise la procédure stockée système **sp_helptext** . Modifiez le nom de la base de données et celui de la procédure stockée pour faire référence à la base de données et à la procédure stockée de votre choix.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 Fonction système :  **OBJECT_DEFINITION**  
 1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, entrez les instructions suivantes qui utilisent la fonction système **OBJECT_DEFINITION** . Modifiez le nom de la base de données et celui de la procédure stockée pour faire référence à la base de données et à la procédure stockée de votre choix.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 Affichage catalogue d’objet : **sys.sql_modules**  
 1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, entrez les instructions suivantes qui utilisent l’affichage catalogue **sys.sql_modules** . Modifiez le nom de la base de données et celui de la procédure stockée pour faire référence à la base de données et à la procédure stockée de votre choix.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une procédure stockée](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [Modifier une procédure stockée](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [Supprimer une procédure stockée](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)   
 [Renommer une procédure stockée](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)  
  
  
