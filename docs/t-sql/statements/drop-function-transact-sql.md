---
title: DROP FUNCTION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_FUNCTION_TSQL
- DROP FUNCTION
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined functions [SQL Server], removing
- removing user-defined functions
- DROP FUNCTION statement
- dropping user-defined functions
- deleting user-defined functions
ms.assetid: ee5ad283-9e44-4109-902f-0ce12669ee11
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b85cb68749cdcf88d62d9d8fbf136a37e845519
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-function-transact-sql"></a>DROP FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Supprime une ou plusieurs fonctions définies par l'utilisateur de la base de données active. Fonctions définies par l’utilisateur sont créées à l’aide de [CREATE FUNCTION](../../t-sql/statements/create-function-transact-sql.md) et modifié à l’aide de [ALTER FUNCTION](../../t-sql/statements/alter-function-transact-sql.md).  
  
 La fonction de liste prend en charge les fonctions définies par l’utilisateur scalaires compilées en mode natif. Pour plus d’informations, consultez [Scalar User-Defined des fonctions pour l’OLTP en mémoire](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 -- SQL Server, Azure SQL Database 

DROP FUNCTION [ IF EXISTS ] { [ schema_name. ] function_name } [ ,...n ]   
[;]
```

```  
 -- Azure SQL Data Warehouse, Parallel Data Warehouse 

DROP FUNCTION [ schema_name. ] function_name
[;] 
```  
   
  
## <a name="arguments"></a>Arguments  
 *S’IL EXISTE*    
 Conditionnellement supprime la fonction uniquement s’il existe déjà. Disponible à compter de [!INCLUDE[ssnoversion_md](../../includes/ssnoversion_md.md)] 2016 et dans [!INCLUDE[sssds_md](../../includes/sssds_md.md)].
  
 *schema_name*  
 Nom du schéma auquel appartient la fonction définie par l'utilisateur.  
  
 *nom de la fonction*  
 Nom de la fonction ou des fonctions définies par l'utilisateur à supprimer. La spécification du nom de schéma est facultative. Il n'est pas possible de spécifier le nom du serveur et de la base de données.  
  
## <a name="remarks"></a>Notes  
 DROP FUNCTION échoue si la base de données contient des fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] ou des vues qui font référence à cette fonction et qui ont été créées au moyen de SCHEMABINDING. Elle échoue également s'il existe des colonnes calculées, des contraintes CHECK ou DEFAULT qui font référence à cette fonction.  
  
 DROP FUNCTION échoue si des colonnes calculées qui ont été indexées font référence à cette fonction.  
  
## <a name="permissions"></a>Permissions  
 Pour exécuter DROP FUNCTION, un utilisateur doit avoir au minimum l'autorisation ALTER sur le schéma auquel appartient la fonction ou l'autorisation CONTROL sur la fonction.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-dropping-a-function"></a>A. Suppression d'une fonction  
 L’exemple suivant supprime le `fn_SalesByStore` fonction définie par l’utilisateur à partir de la `Sales` schéma dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données exemple. Pour créer cette fonction, consultez l’exemple B dans [CREATE FUNCTION &#40; Transact-SQL &#41; ](../../t-sql/statements/create-function-transact-sql.md).  
  
```  
DROP FUNCTION Sales.fn_SalesByStore;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-function-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Sys.Parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  

