---
title: LEN (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 09/03/2015
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
- LEN
- LEN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- LEN function
- characters [SQL Server], number of
- number of characters
ms.assetid: fa20fee4-884d-4301-891a-c03e901345ae
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 532b996c23a8f9746a52434d78783da2a24d1add
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="len-transact-sql"></a>LEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne le nombre de caractères de l'expression de type chaîne spécifiée, à l'exception des espaces de droite.  
  
> [!NOTE]  
>  Pour retourner le nombre d’octets utilisés pour représenter une expression, utilisez la [DATALENGTH](../../t-sql/functions/datalength-transact-sql.md) (fonction).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
LEN ( string_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *string_expression*  
 La chaîne [expression](../../t-sql/language-elements/expressions-transact-sql.md) à évaluer. *string_expression* peut être une constante, une variable ou une colonne de données binaire ou caractère.  
  
## <a name="return-types"></a>Types de retour  
 **bigint** si *expression* est de le **varchar (max)**, **nvarchar (max)** ou **varbinary (max)** des types de données ; sinon, **int**.  
  
 Si vous utilisez des classements SC, la valeur entière retournée compte les paires de substitution UTF-16 comme un caractère unique. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="remarks"></a>Notes  
 LEN exclut les espaces à droite. Si c’est un problème, envisagez d’utiliser le [DATALENGTH &#40; Transact-SQL &#41; ](../../t-sql/functions/datalength-transact-sql.md) fonction qui ne les supprime pas. Si le traitement d’une chaîne unicode, DATALENGTH retourne deux fois le nombre de caractères. L’exemple suivant montre la fonction LEN et DATALENGTH avec un espace de fin.  
  
```  
DECLARE @v1 varchar(40),  
    @v2 nvarchar(40);  
SELECT   
@v1 = 'Test of 22 characters ',   
@v2 = 'Test of 22 characters ';  
SELECT LEN(@v1) AS [varchar LEN] , DATALENGTH(@v1) AS [varchar DATALENGTH];  
SELECT LEN(@v2) AS [nvarchar LEN], DATALENGTH(@v2) AS [nvarchar DATALENGTH];  
  
```  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant sélectionne le nombre de caractères et les données figurant dans `FirstName` pour les personnes résidant en `Australia`. Cet exemple utilise la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT LEN(FirstName) AS Length, FirstName, LastName   
FROM Sales.vIndividualCustomer  
WHERE CountryRegionName = 'Australia';  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant retourne le nombre de caractères dans la colonne `FirstName` et les premier et les noms des employés se trouve dans `Australia`.  
  
```  
-- Uses AdventureWorks  
  
SELECT DISTINCT LEN(FirstName) AS FNameLength, FirstName, LastName   
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.DimGeography AS g   
    ON e.SalesTerritoryKey = g.SalesTerritoryKey   
WHERE EnglishCountryRegionName = 'Australia';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
FNameLength  FirstName  LastName  
-----------  ---------  ---------------  
4            Lynn       Tsoflias
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
 [DATALENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [GAUCHE &#40; Transact-SQL &#41;](../../t-sql/functions/left-transact-sql.md)   
 [DROITE &#40; Transact-SQL &#41;](../../t-sql/functions/right-transact-sql.md)  
  
  



