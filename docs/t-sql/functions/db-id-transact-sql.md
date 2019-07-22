---
title: DB_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DB_ID_TSQL
- DB_ID
dev_langs:
- TSQL
helpviewer_keywords:
- viewing database ID numbers
- IDs [SQL Server], databases
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
- displaying database ID numbers
- DB_ID function
ms.assetid: 7b3aef89-a6fd-4144-b468-bf87ebf381b8
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d2dc84cd224b8ea1863fd67561fdcf20a37c4544
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119022"
---
# <a name="dbid-transact-sql"></a>DB_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Cette fonction retourne le numéro d’identification (ID) de la base de données spécifiée.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DB_ID ( [ 'database_name' ] )   
```  
  
## <a name="arguments"></a>Arguments  
'*database_name*'  
Nom de la base de données dont le numéro d’ID `DB_ID` est retourné. Si l’appel à `DB_ID` omet *database_name*, `DB_ID` retourne l’ID de la base de données active.
  
## <a name="return-types"></a>Types de retour
**Int**

## <a name="remarks"></a>Notes
`DB_ID` ne peut être utilisé que pour retourner l’identificateur de la base de données active dans Azure SQL Database. La valeur NULL est retournée si le nom spécifié n’est pas celui de la base de données active.
  
## <a name="permissions"></a>Autorisations  
Si l’appelant de `DB_ID` ne possède pas une base de données non **MASTER** ou non **tempdb** spécifique, au minimum les autorisations au niveau serveur `ALTER ANY DATABASE` ou `VIEW ANY DATABASE` sont nécessaires pour consulter la ligne `DB_ID` correspondante. Pour la base de données **MASTER**, `DB_ID` a besoin au minimum de l’autorisation `CREATE DATABASE`. La base de données à laquelle l’appelant se connecte apparaît toujours dans **sys.databases**.
  
> [!IMPORTANT]  
>  Par défaut, le rôle public a l’autorisation `VIEW ANY DATABASE`, qui permet à toutes les connexions de consulter les informations de la base de données. Pour empêcher une connexion de détecter une base de données, révoquez (`REVOKE`) l’autorisation publique `VIEW ANY DATABASE`, ou refusez (`DENY`) l’autorisation `VIEW ANY DATABASE` pour les connexions individuelles.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-database-id-of-the-current-database"></a>A. Retour de l'ID de la base de données active  
L’exemple suivant retourne l’ID de la base de données active.
  
```sql
SELECT DB_ID() AS [Database ID];  
GO  
```  
  
### <a name="b-returning-the-database-id-of-a-specified-database"></a>B. Retour de l'ID d'une base de données spécifique  
L’exemple suivant retourne l’ID de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql
SELECT DB_ID(N'AdventureWorks2008R2') AS [Database ID];  
GO  
```  
  
### <a name="c-using-dbid-to-specify-the-value-of-a-system-function-parameter"></a>C. Utilisation de DB_ID pour spécifier la valeur d'un paramètre de fonction système  
L’exemple suivant utilise `DB_ID` pour retourner l’ID de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] dans la fonction système `sys.dm_db_index_operational_stats`. Le premier paramètre de la fonction est un ID de base de données.
  
```sql
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-return-the-id-of-the-current-database"></a>D. Renvoi de l’ID de la base de données active  
L’exemple suivant retourne l’ID de la base de données active.
  
```sql
SELECT DB_ID();  
```  
  
### <a name="e-return-the-id-of-a-named-database"></a>E. Renvoi de l’ID d’une base de données nommée  
L’exemple suivant retourne l’ID de la base de données AdventureWorksDW2012.
  
```sql
SELECT DB_ID('AdventureWorksPDW2012');  
```  
  
## <a name="see-also"></a>Voir aussi
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
[Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)
  
  

