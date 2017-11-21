---
title: TYPE_NAME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TYPE_NAME_TSQL
- TYPE_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- names [SQL Server], data types
- unqualified type names
- type names [SQL Server]
- data types [SQL Server], names
- TYPE_NAME function
ms.assetid: e4075a2e-5f70-440f-986b-9ec8434e07c1
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d3d60bec3a21bb5b1127b0f18977d3485979f20b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="typename-transact-sql"></a>TYPE_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie le nom du type non qualifié correspondant à un ID de type spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TYPE_NAME ( type_id )   
```  
  
## <a name="arguments"></a>Arguments  
 *type_id*  
 ID du type qui sera utilisé. *type_id* est un **int**, il peut faire référence à un type de n’importe quel schéma de l’appelant est autorisé à accéder.  
  
## <a name="return-types"></a>Types de retour  
 **sysname**  
  
## <a name="exceptions"></a>Exceptions  
 Retourne la valeur NULL en cas d'erreur ou si un appelant n'est pas autorisé à afficher l'objet.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'un droit d'accès. Cela signifie que les fonctions intégrées générant des métadonnées, telles que TYPE_NAME, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Notes  
 TYPE_NAME renvoie NULL lorsque *type_id* n’est pas valide ou lorsque l’appelant ne dispose pas des autorisations suffisantes pour référencer le type.  
  
 TYPE_NAME fonctionne pour les types de données système ainsi que pour les types de données définis par l'utilisateur. Le type peut être contenu dans n'importe quel schéma, mais un nom de type non qualifié est toujours renvoyé. Cela signifie que le nom n’a pas la *schéma***.** préfixe.  
  
 Les fonctions système peuvent être utilisées dans la liste de sélection, dans une clause WHERE, et partout où une expression est autorisée. Pour plus d’informations, consultez [Expressions &#40; Transact-SQL &#41; ](../../t-sql/language-elements/expressions-transact-sql.md) et [où &#40; Transact-SQL &#41; ](../../t-sql/queries/where-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie le nom d'objet, le nom de colonne et le nom du type de chaque colonne de la table `Vendor` de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT o.name AS obj_name, c.name AS col_name,  
       TYPE_NAME(c.user_type_id) AS type_name  
FROM sys.objects AS o   
JOIN sys.columns AS c  ON o.object_id = c.object_id  
WHERE o.name = 'Vendor'  
ORDER BY col_name;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
obj_name        col_name                  type_name
--------------- ------------------------ --------------
Vendor          AccountNumber            AccountNumber
Vendor          ActiveFlag               Flag
Vendor          BusinessEntityID         int
Vendor          CreditRating             tinyint
Vendor          ModifiedDate             datetime
Vendor          Name                     Name
Vendor          PreferredVendorStatus    Flag
Vendor          PurchasingWebServiceURL  nvarchar

(8 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant retourne le `TYPE ID` pour le type de données avec l’id `1`.  
  
```  
SELECT TYPE_NAME(36) AS Type36, TYPE_NAME(239) AS Type239;  
GO  
```  
  
 Pour obtenir la liste des types de requête sys.types.  
  
```  
SELECT * FROM sys.types;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [TYPE_ID &#40; Transact-SQL &#41;](../../t-sql/functions/type-id-transact-sql.md)   
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
  
  


