---
title: COL_NAME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COL_NAME
- COL_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- COL_NAME function
- column names [SQL Server]
- names [SQL Server], columns
ms.assetid: 214144ab-f2bc-4052-83cf-caf0a85c4cc6
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3028e409a8218b35bbf7cd4773e80ca27e8db8be
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="colname-transact-sql"></a>COL_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Renvoie le nom d'une colonne à partir des numéros d'identification de table et de colonne correspondants.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
COL_NAME ( table_id , column_id )  
```  
  
## <a name="arguments"></a>Arguments  
*table_id*  
Numéro d'identification de la table contenant la colonne. *table_id* est de type **int**.
  
*column_id*  
Numéro d'identification de la colonne. *column_id* paramètre est de type **int**.
  
## <a name="return-types"></a>Types de retour
**sysname**
  
## <a name="exceptions"></a>Exceptions  
Retourne la valeur NULL en cas d'erreur ou si un appelant n'est pas autorisé à afficher l'objet.
  
Un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'une autorisation. Cela signifie que les fonctions intégrées générant des métadonnées, telles que COL_NAME, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Notes  
Le *table_id* et *column_id* paramètres produisent une chaîne de nom de colonne.
  
Pour plus d’informations sur l’obtention des numéros d’identification de table et de colonne, consultez [OBJECT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/object-id-transact-sql.md).
  
## <a name="examples"></a>Exemples  
L'exemple suivant renvoie le nom de la première colonne de la table `Employee` de la base de données `AdventureWorks2012`.
  
```sql
USE AdventureWorks2012;  
GO  
SET NOCOUNT OFF;  
GO  
SELECT COL_NAME(OBJECT_ID('HumanResources.Employee'), 1) AS 'Column Name';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`Column Name`
  
-----------------\-
  
`BusinessEntityID`
  
## <a name="examples"></a>Exemples

[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

L’exemple suivant retourne le nom de la première colonne dans un exemple `Employee` table.
  
```sql
-- Uses AdventureWorks  
  
SELECT COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 1) AS FirstColumnName,  
COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 2) AS SecondColumnName;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
ColumnName          
------------   
BusinessEntityID  
```  
  
## <a name="see-also"></a>Voir aussi
[Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)  
[COL_LENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/col-length-transact-sql.md)
  
  


