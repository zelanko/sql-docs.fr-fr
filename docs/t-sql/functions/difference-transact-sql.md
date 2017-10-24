---
title: "DIFFÉRENCE (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DIFFERENCE
- DIFFERENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DIFFERENCE function
- comparing SOUNDEX values
- SOUNDEX values
ms.assetid: c58ca25d-d6ea-48fa-93bb-c9374b0b2a2b
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 1868f902cf41eba9637138d7333ac908c72cb76e
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="difference-transact-sql"></a>DIFFERENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie sous la forme d'un entier la différence entre les valeurs SOUNDEX de deux expressions de caractères.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DIFFERENCE ( character_expression , character_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Est un caractère alphanumérique [expression](../../t-sql/language-elements/expressions-transact-sql.md) des données de caractères. *character_expression* peut être une constante, une variable ou une colonne.  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 L'entier renvoyé est le nombre de caractères identiques dans les valeurs SOUNDEX. La valeur renvoyée est comprise entre 0 et 4 : 0 indique une similarité nulle ou faible, et 4 indique une forte similarité ou des valeurs identiques.  
  
 DIFFERENCE et SOUNDEX respectent le classement.  
  
## <a name="examples"></a>Exemples  
 Dans la première partie de l'exemple qui suit, les valeurs `SOUNDEX` de deux chaînes très similaires sont comparées. Pour un classement Latin1_General `DIFFERENCE` retourne une valeur de `4`. Dans la deuxième partie de l’exemple suivant, la `SOUNDEX` les valeurs de deux chaînes très différentes sont comparées et pour un classement Latin1_General `DIFFERENCE` retourne une valeur de `0`.  
  
```  
-- Returns a DIFFERENCE value of 4, the least possible difference.  
SELECT SOUNDEX('Green'), SOUNDEX('Greene'), DIFFERENCE('Green','Greene');  
GO  
-- Returns a DIFFERENCE value of 0, the highest possible difference.  
SELECT SOUNDEX('Blotchet-Halls'), SOUNDEX('Greene'), DIFFERENCE('Blotchet-Halls', 'Greene');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----- ----- -----------   
G650  G650  4             
  
(1 row(s) affected)  
  
----- ----- -----------   
B432  G650  0             
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SOUNDEX &#40; Transact-SQL &#41;](../../t-sql/functions/soundex-transact-sql.md)   
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


