---
title: "- (Négatif) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: negative
dev_langs: TSQL
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
- negative values
ms.assetid: d6c14d14-d379-403b-82db-c197ad58c896
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c2d561099b6208ad0057489efd27942e48882df9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="unary-operators---negative"></a>Opérateurs unaires - négatif
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie la négation de la valeur d'une expression numérique (un opérateur unaire). Les opérateurs unaires effectuent une opération sur une seule expression de n'importe quel type de données de la catégorie des types numériques.   
  
|Opérateur|Signification|  
|--------------|-------------|  
|[+ (Positif)](../../t-sql/language-elements/unary-operators-positive.md)|La valeur numérique est positive.|  
|[- (Négatif)](../../t-sql/language-elements/unary-operators-negative.md)|La valeur numérique est négative.|  
|[~ (NOT au niveau du bit)](../../t-sql/language-elements/bitwise-not-transact-sql.md)|Renvoie le complément à un du nombre.|  
  
 Les opérateurs + (positif) et - (négatif) peuvent s'utiliser dans toute expression de n'importe quel type de données de la catégorie des types numériques. L'opérateur ~ (NOT au niveau du bit) ne peut s'utiliser que dans des expressions dont le type de données appartient à la catégorie des types entiers. 
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
- numeric_expression  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) de l’un des types de données de la catégorie de type de données numérique, à l’exception de la date et de la catégorie de temps.  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données *numeric_expression*, mais non **tinyint** expression est promue à un **smallint** résultat.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-setting-a-variable-to-a-negative-value"></a>A. Affectation d'une valeur négative à une variable  
 L'exemple suivant affecte une valeur négative à une variable.  
  
```  
USE tempdb;  
GO  
DECLARE @MyNumber decimal(10,2);  
SET @MyNumber = -123.45;  
SELECT @MyNumber AS NegativeValue;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
NegativeValue  
---------------------------------------  
-123.45  
  
(1 row(s) affected)  
  
```  
  
### <a name="b-changing-a-variable-to-a-negative-value"></a>B. Modification d'une variable en une valeur négative  
 L'exemple suivant modifie une variable en une valeur négative.  
  
```  
USE tempdb;  
GO  
DECLARE @Num1 int;  
SET @Num1 = 5;  
SELECT @Num1 AS VariableValue, -@Num1 AS NegativeValue;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
VariableValue NegativeValue  
------------- -------------  
5             -5  
  
(1 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-negative-of-a-positive-constant"></a>C. Retourner la valeur négative d’une constante positive  
 L’exemple suivant retourne la valeur négative d’une constante positive.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) - 17 FROM DimEmployee;  
```  
  
 Valeur renvoyée  
  
```  
-17  
```  
  
### <a name="d-returning-the-positive-of-a-negative-constant"></a>D. Retour de la valeur positive d’une constante négative  
 L’exemple suivant retourne la valeur positive d’une constante négative.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) – ( - 17) FROM DimEmployee;  
```  
  
 Valeur renvoyée  
  
```  
17  
```  
  
### <a name="e-returning-the-negative-of-a-column"></a>E. Retourner la valeur négative d’une colonne  
 L’exemple suivant retourne la valeur négative de la `BaseRate` valeur pour chaque employé dans le `dimEmployee` table.  
  
```  
USE ssawPDW;  
  
SELECT - BaseRate FROM DimEmployee;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

