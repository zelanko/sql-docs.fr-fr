---
title: Modulo (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- modulo
- '% (Modulo)'
- MOD_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: f93c662e-f405-486e-bf23-a2d03907b5bd
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b417bbca6135db2f4ca6279bb9aac75d9d6f328
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="modulo-transact-sql"></a>Modulo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie le reste d'un nombre divisé par un autre.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 *dividend*  
 Expression numérique à diviser. *dividende* doit être un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de l’un des types de données dans les catégories de types de données monétaires, entier ou **numérique** type de données.  
  
 *divisor*  
 Est l’expression numérique par laquelle diviser le dividende. *diviseur* doit être toute expression valide de l’un des types de données dans les catégories de types de données monétaires, entier ou **numérique** type de données.  
  
## <a name="result-types"></a>Types des résultats  
 Déterminés par les types de données des deux arguments.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser l’opérateur arithmétique modulo dans la liste de sélection de l’instruction SELECT avec n’importe quelle combinaison de noms de colonnes, de constantes numériques ou toute expression valide de l’entier et les données monétaires type catégories ou **numérique** type de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-example"></a>A. Exemple simple  
 L'exemple suivant divise le nombre 38 par 5. Ce résultat est la partie entière du résultat de 7 et montre comment modulo retourne le reste de 3.  
  
```  
SELECT 38 / 5 AS Integer, 38 % 5 AS Remainder ;  
  
```  
  
### <a name="b-example-using-columns-in-a-table"></a>B. Exemple utilisant des colonnes dans une table  
 L'exemple suivant renvoie le numéro d'identification et le prix unitaire du produit, ainsi que le reste (modulo) de la division du prix de chaque produit, converti en valeur entière, par le nombre de produits commandés.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(100)ProductID, UnitPrice, OrderQty,  
   CAST((UnitPrice) AS int) % OrderQty AS Modulo  
FROM Sales.SalesOrderDetail;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-example"></a>C: exemple simple  
 L’exemple suivant montre les résultats de la `%` opérateur de division de 3 par 2.  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) 3%2 FROM dimEmployee;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
1         
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [COMME &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Modulo égal &#40; Transact-SQL &#41;](../../t-sql/language-elements/modulo-equals-transact-sql.md)   
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  



