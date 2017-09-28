---
title: CEILING (Transact-SQL) | Documents Microsoft
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
- CEILING_TSQL
- CEILING
dev_langs:
- TSQL
helpviewer_keywords:
- smallest integer great than or equal to expression
- integers [SQL Server]
- CEILING function [Transact-SQL]
ms.assetid: e736b43a-9457-4781-95a4-4bcf9d4fc46a
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c8b61f59733fa0696e8176f6c380139330c575e9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="ceiling-transact-sql"></a>CEILING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Renvoie le plus petit entier supérieur ou égal à l'expression numérique spécifiée.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CEILING ( numeric_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*numeric_expression*  
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de la catégorie, de type de données numérique approximatives ou à l’exception de la **bits** type de données.
  
## <a name="return-types"></a>Types de retour
Retourne le même type que *numeric_expression*.
  
## <a name="examples"></a>Exemples  
L'exemple suivant illustre l'utilisation de valeurs numériques positives, négatives et nulles avec la fonction CEILING.
  
```sql
SELECT CEILING($123.45), CEILING($-123.45), CEILING($0.0);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
--------- --------- -------------------------   
124.00    -123.00    0.00                       
  
(1 row(s) affected)  
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

L’exemple suivant montre l’utilisation de numériques positives, négatives et les valeurs zéro avec la fonction CEILING.
  
```sql
SELECT CEILING(123.45), CEILING(-123.45), CEILING(0.0);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`------- --------- --------`
  
`124.00  -123.00   0.00`
  
## <a name="see-also"></a>Voir aussi
[Fonctions système &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  

