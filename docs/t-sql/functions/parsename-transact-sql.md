---
title: PARSENAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PARSENAME_TSQL
- PARSENAME
dev_langs:
- TSQL
helpviewer_keywords:
- PARSENAME function
- parsing [SQL Server], PARSENAME function
- names [SQL Server], objects
- objects [SQL Server], names
- part of object names [SQL Server]
ms.assetid: abf34f99-9ee9-460b-85b2-930ca5c4b5ae
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8b85845eea5e2bfcb1c3074b155d442b30ae499d
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394797"
---
# <a name="parsename-transact-sql"></a>PARSENAME (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Retourne la partie spécifiée d'un nom d'objet. Les parties d'un objet pouvant être récupérées sont le nom de l’objet, le nom du schéma, le nom de la base de données et le nom du serveur. 
  
> [!NOTE]  
>  La fonction PARSENAME n'indique pas s'il existe déjà un objet portant le nom spécifié. Elle se limite à retourner la partie indiquée du nom d'objet spécifié.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql 
PARSENAME ('object_name' , object_piece )
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments

*'object_name'* est le paramètre qui contient le nom de l’objet pour lequel récupérer la partie d’objet spécifiée. Ce paramètre représente un nom d'objet éventuellement qualifié. Si toutes les parties du nom de l’objet sont qualifiées, ce nom peut se composer de quatre parties : le nom du serveur, le nom de la base de données, le nom du schéma et le nom de l'objet.  Chaque partie de la chaîne 'object_name' est de type *sysname* qui est équivalente à nvarchar(128) ou 256 octets. Si une partie de la chaîne dépasse 256 octets, PARSENAME retourne la valeur NULL pour cette partie, car il ne s’agit pas d’un sysname valide.
  
*object_piece*  
Partie de l'objet à retourner. *object_piece* est de type **int** et peut prendre les valeurs suivantes :  
    1 = Nom de l'objet  
    2 = Nom du schéma  
    3 = Nom de la base de données  
    4 = Nom du serveur  
  
## <a name="return-type"></a>Type de retour

 **sysname**
  
## <a name="remarks"></a>Notes

 La fonction PARSENAME retourne NULL si l'une des conditions suivantes est vraie :  
  
-   *object_name* ou *object_piece* a la valeur NULL.  
  
-   une erreur de syntaxe s'est produite.  
  
 La partie d’objet recherchée a une longueur égale à 0 et n’est pas un identificateur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide. Un nom d'objet d'une longueur égale à 0 invalide la totalité du nom qualifié.  
  
## <a name="examples"></a>Exemples

 L'exemple suivant utilise `PARSENAME` pour retourner des informations sur la table `Person` de la base de données `AdventureWorks2012`.  
  
```sql  
-- Uses AdventureWorks  
  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```
Object Name
------------------------------
DimCustomer

(1 row(s) affected)

Schema Name
------------------------------
dbo

(1 row(s) affected)

Database Name
------------------------------
AdventureWorksPDW2012

(1 row(s) affected)

Server Name
------------------------------
(null)

(1 row(s) affected)
```
  
## <a name="see-also"></a>Voir aussi

- [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
- [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
- [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
- [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  

