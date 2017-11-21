---
title: ISNULL (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- ISNULL
- ISNULL_TSQL
- IFNULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- replacing null values
- null values [SQL Server], ISNULL
- null values [SQL Server], replacement values
- ISNULL function
ms.assetid: 6f3e5802-864b-4e77-9862-657bb5430b68
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8d364548d3303de493343365bd16677ffdfd5641
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="isnull-transact-sql"></a>ISNULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Remplace NULL par la valeur de remplacement spécifiée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ISNULL ( check_expression , replacement_value )  
```  
  
## <a name="arguments"></a>Arguments  
 *check_expression*  
 Est la [expression](../../t-sql/language-elements/expressions-transact-sql.md) à vérifier pour NULL. *check_expression* peut être de n’importe quel type.  
  
 *replacement_value*  
 Est l’expression à retourner si *check_expression* a la valeur NULL. *replacement_value* doit être d’un type qui est implicitement convertible en type de *vérification_expression*.  
  
## <a name="return-types"></a>Types de retour  
 Retourne le même type que *check_expression*. Si un littéral NULL est fourni en tant que *check_expression*, retourne le type de données de la *replacement_value*. Si un littéral NULL est fourni en tant que *check_expression* et aucun *replacement_value* est fourni, retourne un **int**.  
  
## <a name="remarks"></a>Notes  
 La valeur de *check_expression* est retournée si elle n’est pas NULL ; sinon, *replacement_value* est retourné après qu’il est implicitement converti en type de *check_expression*, si les types sont différents. *replacement_value* peut être tronqué si *replacement_value* dépasse *check_expression*.  
  
> [!NOTE]  
>  Utilisez [COALESCE &#40; Transact-SQL &#41; ](../../t-sql/language-elements/coalesce-transact-sql.md) pour retourner la première valeur non null.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-isnull-with-avg"></a>A. Utilisation de ISNULL avec AVG  
 L'exemple suivant recherche la moyenne du poids de tous les produits. La valeur `50` se substitue à toutes les entrées NULL de la colonne `Weight` de la table `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT AVG(ISNULL(Weight, 50))  
FROM Production.Product;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 -------------------------- 
59.79  
  
 (1 row(s) affected)
 ```  
  
### <a name="b-using-isnull"></a>B. Utilisation de ISNULL  
 Dans l'exemple suivant, la description (« Description »), le pourcentage de remise (« DiscountPct »), la quantité minimale (« MinQty ») et la quantité maximale (« Max Quantity ») sont sélectionnés pour toutes les offres spéciales figurant dans `AdventureWorks2012`. Si la quantité maximale associée à une offre spéciale déterminée est NULL, `MaxQty` présente la valeur `0.00` dans l'ensemble de résultats.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Description, DiscountPct, MinQty, ISNULL(MaxQty, 0.00) AS 'Max Quantity'  
FROM Sales.SpecialOffer;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|   Description       |  DiscountPct    |   MinQty    |   Quantité maximale       |
|  ---------------   |  -------------  |   --------  |   ---------------    |
|  No Discount       |  0.00           |   0         |   0                  |
|  Volume Discount   |  0.02           |   11        |   14                 |
|  Volume Discount   |  0.05           |   15        |   4                  |
|  Volume Discount   |  0.10           |   25        |   0                  |
|  Volume Discount   |  (0.15%)           |   41        |   0                  |
|  Volume Discount   |  0.20           |   61        |   0                  |
|  Mountain-100 Cl   |  0.35           |   0         |   0                  |
|  Sport casque Di   |  0.10           |   0         |   0                  |
|  Road-650 Overst   |  0.30           |   0         |   0                  |
|  Mountain Tire S   |  0.50           |   0         |   0                  |
|  Sport casque Di   |  (0.15%)           |   0         |   0                  |
|  LL route Frame S   |  0.35           |   0         |   0                  |
|  Tourisme-3000 Pr   |  (0.15%)           |   0         |   0                  |
|  Requête de tirage Touring-1000   |  0.20           |   0         |   0                  |
|  Moitié prix Peda   |  0.50           |   0         |   0                  |
|  Mountain-500 Si   |  0.40           |   0         |   0                  |

 `(16 row(s) affected)`  
  
### <a name="c-testing-for-null-in-a-where-clause"></a>C. Test de valeur NULL dans une clause WHERE  
 N'utilisez pas ISNULL pour rechercher des valeurs NULL. Utilisez IS NULL à la place. L'exemple suivant recherche tous les produits qui comportent `NULL` dans la colonne weight. Notez l'espace entre `IS` et `NULL`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name, Weight  
FROM Production.Product  
WHERE Weight IS NULL;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-isnull-with-avg"></a>D. Utilisation de ISNULL avec AVG  
 L’exemple suivant recherche la moyenne du poids de tous les produits dans un exemple de table. La valeur `50` se substitue à toutes les entrées NULL de la colonne `Weight` de la table `Product`.  
  
```  
-- Uses AdventureWorks  
  
SELECT AVG(ISNULL(Weight, 50))  
FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------------------------   
52.88   
```  
  
### <a name="e-using-isnull"></a>E. Utilisation de ISNULL  
 L’exemple suivant utilise ISNULL pour tester les valeurs NULL dans la colonne `MinPaymentAmount` et afficher la valeur `0.00` pour les lignes.  
  
```  
-- Uses AdventureWorks  
  
SELECT ResellerName,   
       ISNULL(MinPaymentAmount,0) AS MinimumPayment  
FROM dbo.DimReseller  
ORDER BY ResellerName;  
  
```  
  
 Voici un jeu de résultats partiel.  
  
|  ResellerName                |  MinimumPayment    |
|  -------------------------   |  --------------    |
|  Une Association de bicyclette       |     0.0000         |
|  Un magasin de vélos                |     0.0000         |
|  Un magasin de Cycle                |     0.0000         |
|  Une société de bicyclette Great     |     0.0000         |
|  Un magasin de vélo classique         |   200.0000         |
|  Service & Sales acceptables  |     0.0000         |
  
### <a name="f-using-is-null-to-test-for-null-in-a-where-clause"></a>F. L’utilisation de IS NULL pour rechercher les valeurs NULL dans une clause WHERE  
 L’exemple suivant recherche tous les produits qui ont `NULL` dans les `Weight` colonne. Notez l'espace entre `IS` et `NULL`.  
  
```  
-- Uses AdventureWorks  
  
SELECT EnglishProductName, Weight  
FROM dbo.DimProduct  
WHERE Weight IS NULL;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [EST NULL &#40; Transact-SQL &#41;](../../t-sql/queries/is-null-transact-sql.md)   
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [OÙ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [Fusionner &#40; Transact-SQL &#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  


