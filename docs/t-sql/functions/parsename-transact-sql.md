---
title: PARSENAME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 63065dcee0d1f7784e7be396273785f741ef44c7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="parsename-transact-sql"></a>PARSENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Retourne la partie spécifiée d'un nom d'objet. Les parties d'un objet pouvant être récupérées sont le nom de l'objet, le nom du propriétaire, le nom de la base de données et le nom du serveur.  
  
> [!NOTE]  
>  La fonction PARSENAME n'indique pas s'il existe déjà un objet portant le nom spécifié. Elle se limite à retourner la partie indiquée du nom d'objet spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PARSENAME ( 'object_name' , object_piece )   
```  
  
## <a name="arguments"></a>Arguments  
 '*nom_objet*'  
 Nom de l'objet contenant la partie d'objet spécifiée à extraire. *nom_objet* est **sysname**. Ce paramètre représente un nom d'objet éventuellement qualifié. Si toutes les parties du nom de l'objet sont qualifiées, ce nom peut se composer de quatre parties : le nom du serveur, le nom de la base de données, le nom du propriétaire et le nom de l'objet.  
  
 *object_piece*  
 Partie de l'objet à retourner. *object_piece* est de type **int**et peut prendre les valeurs suivantes :  
  
 1 = Nom de l'objet  
  
 2 = Nom du schéma  
  
 3 = Nom de la base de données  
  
 4 = Nom du serveur  
  
## <a name="return-types"></a>Types de retour  
 **nchar**  
  
## <a name="remarks"></a>Notes  
 La fonction PARSENAME retourne NULL si l'une des conditions suivantes est vraie :  
  
-   Soit *nom_objet* ou *object_piece* a la valeur NULL.  
  
-   une erreur de syntaxe s'est produite.  
  
 La partie d’objet recherchée a une longueur de 0 et n’est pas valide [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificateur. Un nom d'objet d'une longueur égale à 0 invalide la totalité du nom qualifié.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `PARSENAME` pour retourner des informations sur la table `Person` de la base de données `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
SELECT PARSENAME('AdventureWorks2012..Person', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorks2012..Person', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorks2012..Person', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorks2012..Person', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Object Name`  
  
 `------------------------------`  
  
 `Person`  
  
 `(1 row(s) affected)`  
  
 `Schema Name`  
  
 `------------------------------`  
  
 `(null)`  
  
 `(1 row(s) affected)`  
  
 `Database Name`  
  
 `------------------------------`  
  
 `AdventureWorks2012`  
  
 `(1 row(s) affected)`  
  
 `Server Name`  
  
 `------------------------------`  
  
 `(null)`  
  
 `(1 row(s) affected)`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'exemple suivant utilise `PARSENAME` pour retourner des informations sur la table `Person` de la base de données `AdventureWorks2012`.  
  
```  
-- Uses AdventureWorks  
  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 1) AS 'Object Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 2) AS 'Schema Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 3) AS 'Database Name';  
SELECT PARSENAME('AdventureWorksPDW2012.dbo.DimCustomer', 4) AS 'Server Name';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Object Name`  
  
 `------------------------------`  
  
 `DimCustomer`  
  
 `(1 row(s) affected)`  
  
 `Schema Name`  
  
 `------------------------------`  
  
 `dbo`  
  
 `(1 row(s) affected)`  
  
 `Database Name`  
  
 `------------------------------`  
  
 `AdventureWorksPDW2012`  
  
 `(1 row(s) affected)`  
  
 `Server Name`  
  
 `------------------------------`  
  
 `(null)`  
  
 `(1 row(s) affected)`  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Fonctions système &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


