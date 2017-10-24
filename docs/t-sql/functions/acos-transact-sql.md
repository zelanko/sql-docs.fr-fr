---
title: ACOS (Transact-SQL) | Documents Microsoft
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
- ACOS
- ACOS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cosine
- ACOS function
- arccosine
ms.assetid: 4ec6b46e-9438-4f0f-8b96-461edd84280a
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aad94e57120771babeb734c7410fdcac94c28c21
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="acos-transact-sql"></a>ACOS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Fonction mathématique qui renvoie l’angle, en radians, dont le cosinus est spécifié **float** expression ; également appelé arc cosinus.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
ACOS ( float_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*expression*  
Est une expression de type **float** ou d’un type qui peut être implicitement converti en **float**, avec une valeur comprise entre -1 et 1. Les valeurs non comprises dans cette plage renvoient la valeur NULL et rapportent une erreur de domaine.
  
## <a name="return-types"></a>Types de retour  
**float**
  
## <a name="examples"></a>Exemples  
L'exemple suivant renvoie l'ACOS du nombre spécifié.
  
```sql
SET NOCOUNT OFF;  
DECLARE @cos float;  
SET @cos = -1.0;  
SELECT 'The ACOS of the number is: ' + CONVERT(varchar, ACOS(@cos));  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---------------------------------   
The ACOS of the number is: 3.14159   
  
(1 row(s) affected)  
```  
  
### <a name="includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 

L'exemple suivant renvoie l'ACOS du nombre spécifié.
  
```sql
DECLARE @cos float;  
SET @cos = -1.0;  
SELECT 'The ACOS of the number is: ' + CONVERT(varchar, ACOS(@cos));  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---------------------------------   
The ACOS of the number is: 3.14159   
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions mathématiques &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
[Fonctions](../../t-sql/functions/functions.md)
  
  


