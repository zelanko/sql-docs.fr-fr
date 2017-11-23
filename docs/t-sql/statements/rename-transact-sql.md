---
title: Changement de nom (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 11/20/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 0907cfd9-33a6-4fa6-91da-7d6679fee878
caps.latest.revision: "15"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ee5395145b72108b63256a7e3742eca6a9289e06
ms.sourcegitcommit: ef1fa818beea435f58986af3379853dc28f5efd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="rename-transact-sql"></a>Changement de nom (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Renomme une table créée par l’utilisateur dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Renomme un créés par l’utilisateur de table ou de la base de données dans [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
> [!NOTE]  
>  Pour renommer une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez la procédure stockée [sp_renamedb &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-renamedb-transact-sql.md). Pour renommer une base de données dans la base de données SQL Azure, utilisez le [ALTER DATABASE (base de données de SQL Azure)](/statements/alter-database-azure-sql-database.md) instruction. 
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for Azure SQL Data Warehouse  
  
-- Rename a table.  
RENAME OBJECT [ :: ]  [ [ database_name .  [schema_name ] ] . ] | [schema_name . ] ] table_name TO new_table_name  
[;]  
  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
-- Rename a table  
RENAME OBJECT [::] [ [ database_name . [ schema_name ] . ] | [ schema_name . ] ] table_name TO new_table_name  
[;]  
  
-- Rename a database  
RENAME DATABASE [::] database_name TO new_database_name  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 RENOMMER L’OBJET [ :]   
          [[*nom_base_de_données* . [ *schema_name* ]. ] | [ *nom_schéma* . []]*table_name* à *nom_nouvelle_table*  
 **S’APPLIQUE À :**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Modifier le nom d’une table définie par l’utilisateur. Spécifier la table à renommer avec-, deux ou nom en trois parties.    Spécifiez la nouvelle table *new_table_name* comme un nom en une partie.  
  
 RENOMMEZ LA BASE DE DONNÉES [ :]   
          [ *nom_base_de_données* à *nouveau_nom_base_de_données*  
 **S’APPLIQUE À :**  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Modifier le nom d’une base de données défini par l’utilisateur à partir de *nom_base_de_données* à *nouveau_nom_base_de_données*.  Vous ne pouvez pas renommer une base de données à un de ces [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]les noms de base de données :  
  
-   master  
  
-   model  
  
-   msdb  
  
-   tempdb  
  
-   pdwtempdb1  
  
-   pdwtempdb2  
  
-   DWConfiguration  
  
-   DWDiagnostics  
  
-   DWQueue  
  
## <a name="permissions"></a>Permissions  
 Ces autorisations sont nécessaires pour exécuter cette commande :  
  
-   **ALTER** autorisation sur la table  
   
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
  
### <a name="cannot-rename-an-external-table-indexes-or-views"></a>Impossible de renommer une table externe, les index ou les vues
Vous ne pouvez pas renommer une table externe, les index ou les vues. Au lieu de renommer, vous pouvez supprimer la table externe, l’index ou la vue et puis la recréer avec le nouveau nom.

### <a name="cannot-rename-a-table-in-use"></a>Impossible de renommer une table en cours d’utilisation  
 Vous ne pouvez pas renommer une table ou une base de données alors qu’il est en cours d’utilisation. Renommer une table requiert un verrou exclusif sur la table. Si la table est en cours d’utilisation, vous devrez peut-être arrêter les sessions qui sont à l’aide de la table. Pour mettre fin à une session, vous pouvez utiliser la commande KILL. Utilisez KILL avec précaution, car lors d’une session est arrêtée tout travail non validée est restaurée. Sessions dans l’entrepôt de données SQL sont précédées de « SID ». Vous devez inclure cette et le numéro de session lors de l’appel de la commande KILL. Cet exemple affiche une liste des sessions actives ou inactives, puis termine la session 'SID1234'.  
  
### <a name="views-are-not-updated"></a>Les vues ne sont pas mis à jour.  
 Lorsque vous renommez une base de données, toutes les vues qui utilisent le nom de l’ancienne base de données ne seront plus valides. Cela s’applique aux affichages à l’intérieur et à l’extérieur de la base de données. Par exemple, si la base de données de ventes est renommé, une vue qui contient `SELECT * FROM Sales.dbo.table1` deviendront non valides. Pour résoudre ce problème, vous pouvez éviter d’utiliser des noms en trois parties dans les vues, ou mettre à jour les vues pour référencer le nouveau nom de base de données.  
  
 Lorsque vous renommez une table, les vues ne sont pas mises à jour pour référencer le nouveau nom de table. Chaque vue, à l’intérieur ou en dehors de la base de données, ce qui fait référence au nom de l’ancienne table deviendront non valide. Pour résoudre ce problème, vous pouvez mettre à jour chaque vue pour référencer le nouveau nom de table.  
  
## <a name="locking"></a>Verrouillage  
 Renommer une table a un verrou partagé sur l’objet de base de données, un verrou partagé sur l’objet de schéma et un verrou exclusif sur la table.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-rename-a-database"></a>A. Renommer une base de données  
 **S’applique à :** [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] uniquement  
  
 Cet exemple renomme la base de données défini par l’utilisateur AdWorks AdWorks2.  
  
```  
-- Rename the user defined database AdWorks  
RENAME DATABASE AdWorks to AdWorks2;  
  
```  
  
 Lorsque vous renommez une table, tous les objets et les propriétés associées à la table sont mises à jour pour référencer le nouveau nom de table. Par exemple, table des définitions, des index, des contraintes et autorisations sont mises à jour. Les vues ne sont pas mis à jour.  
  
### <a name="b-rename-a-table"></a>B. Renommer une table  
 **S’APPLIQUE À :**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Cet exemple renomme la table Customer Customer1.  
  
```  
-- Rename the customer table  
RENAME OBJECT Customer TO Customer1;  
  
RENAME OBJECT mydb.dbo.Customer TO Customer1;  
```  
  
 Lorsque vous renommez une table, tous les objets et les propriétés associées à la table sont mises à jour pour référencer le nouveau nom de table. Par exemple, table des définitions, des index, des contraintes et autorisations sont mises à jour. Les vues ne sont pas mis à jour.  
   
  
### <a name="c-move-a-table-to-a-different-schema"></a>C. Déplacer une table à un schéma différent  
 **S’APPLIQUE À :**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Si votre objectif est de déplacer l’objet vers un autre schéma, utilisez [ALTER SCHEMA &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-schema-transact-sql.md). Par exemple, cette opération déplace l’élément de tableau à partir du schéma de produit pour le schéma dbo.  
  
```  
ALTER SCHEMA dbo TRANSFER OBJECT::product.item;  
```  
  
### <a name="d-terminate-sessions-before-renaming-a-table"></a>D. Arrêter les sessions avant de renommer une table  
 **S’APPLIQUE À :**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)],  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
 Il est important de se rappeler que vous ne pouvez pas renommer une table alors qu’il est en cours d’utilisation. Un changement de nom d’une table requiert un verrou exclusif sur la table. Si la table est en cours d’utilisation, vous devrez peut-être mettre fin à la session à l’aide de la table. Pour mettre fin à une session, vous pouvez utiliser la commande KILL. Utilisez KILL avec précaution, car lors d’une session est arrêtée tout travail non validée est restaurée. Sessions dans l’entrepôt de données SQL sont précédées de « SID ». Vous devez inclure cette et le numéro de session lors de l’appel de la commande KILL. Cet exemple affiche une liste des sessions actives ou inactives, puis termine la session 'SID1234'.  
  
```  
-- View a list of the current sessions  
SELECT session_id, login_name, status   
FROM sys.dm_pdw_exec_sessions   
WHERE status='Active' OR status='Idle';  
  
-- Terminate a session using the session_id.  
KILL 'SID1234';  
```  
  
  
