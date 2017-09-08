---
title: Db_name (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DB_NAME
- DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database names [SQL Server], DB_NAME
- names [SQL Server], databases
- viewing database names
- displaying database names
- DB_NAME function
ms.assetid: e21fb33a-a3ea-49b0-bb6b-8f789a675a0e
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5743ccb1374640078a77d84a140e9e5d0fdaef0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbname-transact-sql"></a>DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne le nom de la base de données.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
DB_NAME ( [ database_id ] )  
```  
  
## <a name="arguments"></a>Arguments  
*database_id*  
Numéro d'identification de la base de données à retourner. *database_id* est **int**, sans valeur par défaut. Si l'ID n'est pas spécifié, la fonction renvoie le nom de la base de données active.
  
## <a name="return-types"></a>Types de retour
**nvarchar (128)**
  
## <a name="permissions"></a>Permissions  
Si l’appelant de **DB_NAME** n’est pas le propriétaire de la base de données et la base de données n’est pas **master** ou **tempdb**, les autorisations minimales requises pour consulter la ligne correspondante sont ALTER ANY DATABASE ou VIEW ANY DATABASE au niveau du serveur, ou l’autorisation CREATE DATABASE dans le **master** base de données. La base de données à laquelle l'appelant est connecté peut toujours être vue dans **sys.databases**.
  
> [!IMPORTANT]  
>  Par défaut, le rôle public a l’autorisation VIEW ANY DATABASE, ce qui permet des connexions d’accès aux informations de base de données. Pour bloquer une connexion à partir de la capacité de détecter une base de données, RÉVOQUER l’autorisation VIEW ANY DATABASE public, ou refuser l’autorisation VIEW ANY DATABASE pour des connexions individuelles.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-current-database-name"></a>A. Renvoi du nom de la base de données active  
L'exemple suivant renvoie le nom de la base de données active.
  
```sql
SELECT DB_NAME() AS [Current Database];  
GO  
```  
  
### <a name="b-returning-the-database-name-of-a-specified-database-id"></a>B. Renvoi du nom de la base de données correspondant à un ID de base de données spécifié.  
L'exemple suivant renvoie le nom de la base de données ayant l'ID `3`.
  
```sql
USE master;  
GO  
SELECT DB_NAME(3)AS [Database Name];  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-return-the-current-database-name"></a>C. Retourner le nom actuel de la base de données  
  
```sql
SELECT DB_NAME() AS [Current Database];  
```  
  
### <a name="d-return-the-name-of-a-database-by-using-the-database-id"></a>D. Retourner le nom d’une base de données à l’aide de l’ID de base de données  
L’exemple suivant retourne le nom de la base de données et le database_id pour chaque base de données.
  
```sql
SELECT DB_NAME(database_id) AS [Database], database_id  
FROM sys.databases;  
```  
  
## <a name="see-also"></a>Voir aussi
[DB_ID &#40; Transact-SQL &#41;](../../t-sql/functions/db-id-transact-sql.md)  
[Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
  
  


