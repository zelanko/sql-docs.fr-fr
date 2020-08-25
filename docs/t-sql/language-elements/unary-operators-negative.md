---
description: '- (Négatif) (Transact-SQL)'
title: '- (Négatif) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- negative
dev_langs:
- TSQL
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
- negative values
ms.assetid: d6c14d14-d379-403b-82db-c197ad58c896
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 873bff9e761f83f0b15493810d0c684afa189748
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459239"
---
# <a name="unary-operators---negative"></a>Opérateurs unaires - Négatif
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Renvoie la négation de la valeur d'une expression numérique (un opérateur unaire). Les opérateurs unaires effectuent une opération sur une seule expression de n'importe quel type de données de la catégorie des types numériques.   
  
|Opérateur|Signification|  
|--------------|-------------|  
|[+ (Positif)](../../t-sql/language-elements/unary-operators-positive.md)|La valeur numérique est positive.|  
|[- (Négatif)](../../t-sql/language-elements/unary-operators-negative.md)|La valeur numérique est négative.|  
|[~ (Opérateur NOT au niveau du bit)](../../t-sql/language-elements/bitwise-not-transact-sql.md)|Renvoie le complément à un du nombre.|  
  
 Les opérateurs + (positif) et - (négatif) peuvent s'utiliser dans toute expression de n'importe quel type de données de la catégorie des types numériques. L'opérateur ~ (NOT au niveau du bit) ne peut s'utiliser que dans des expressions dont le type de données appartient à la catégorie des types entiers. 
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
- numeric_expression  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *numeric_expression*  
 [expression](../../t-sql/language-elements/expressions-transact-sql.md) valide de tout type de données de la catégorie numérique, sauf la catégorie date et heure.  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données de *numeric_expression*, à l’exception d’une expression non signée de type **tinyint** convertie en résultat **smallint** signé.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-setting-a-variable-to-a-negative-value"></a>R. Affectation d'une valeur négative à une variable  
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
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-negative-of-a-positive-constant"></a>C. Retour de la valeur négative d’une constante positive  
 L’exemple suivant retourne la valeur négative d’une constante positive.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) - 17 FROM DimEmployee;  
```  
  
 Retours  
  
```  
-17  
```  
  
### <a name="d-returning-the-positive-of-a-negative-constant"></a>D. Retour de la valeur positive d’une constante négative  
 L’exemple suivant retourne la valeur positive d’une constante négative.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) - ( - 17) FROM DimEmployee;  
```  
  
 Retours  
  
```  
17  
```  
  
### <a name="e-returning-the-negative-of-a-column"></a>E. Retour de la valeur négative d’une colonne  
 L’exemple suivant retourne la valeur négative de la valeur `BaseRate` de chaque employé figurant dans la table `dimEmployee`.  
  
```  
USE ssawPDW;  
  
SELECT - BaseRate FROM DimEmployee;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Opérateurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

