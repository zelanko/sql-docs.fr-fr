---
title: ET (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AND_TSQL
- AND
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], TRUE
- TRUE
- AND, about AND operators
- AND
- combining expressions
ms.assetid: b61d7f8d-5a51-49b7-91dd-f6190a5a0fb9
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f21efc0360c992c3a88706a13f84f35d7026b101
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="and-transact-sql"></a>AND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combine deux expressions booléennes et retourne **TRUE** lorsque les deux expressions sont **TRUE**. Lorsque plusieurs opérateurs logiques est utilisé dans une instruction, le **AND** opérateurs sont évalués en premier. Vous pouvez modifier l'ordre de traitement en utilisant des parenthèses.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
boolean_expression AND boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 *boolean_expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) qui retourne une valeur booléenne : **TRUE**, **FALSE**, ou **inconnu**.  
  
## <a name="result-types"></a>Types des résultats  
 **Booléen**  
  
## <a name="result-value"></a>Valeur des résultats  
 Retourne la valeur TRUE lorsque les deux expressions sont vraies.  
  
## <a name="remarks"></a>Notes  
 Le graphique suivant illustre les valeurs retournées lorsque vous comparez des valeurs TRUE et FALSE à l'aide de l'opérateur AND.  
  
||TRUE|FALSE|UNKNOWN|  
|------|----------|-----------|-------------|  
|**TRUE**|TRUE|FALSE|UNKNOWN|  
|**FALSE**|FALSE|FALSE|FALSE|  
|**INCONNU**|UNKNOWN|FALSE|UNKNOWN|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-the-and-operator"></a>A. Utilisation de l'opérateur AND  
 L'exemple suivant sélectionne des informations sur les employés qui ont à la fois le titre de `Marketing Assistant` et plus de `41` heures de congés disponibles.  
  
```  
-- Uses AdventureWorks  
  
SELECT  BusinessEntityID, LoginID, JobTitle, VacationHours   
FROM HumanResources.Employee  
WHERE JobTitle = 'Marketing Assistant'  
AND VacationHours > 41 ;  
```  
  
### <a name="b-using-the-and-operator-in-an-if-statement"></a>B. Utilisation de l'opérateur AND dans une instruction IF  
 Les exemples suivants indiquent comment utiliser AND dans une instruction IF. Dans la première instruction, `1 = 1` et `2 = 2` sont vrais ; par conséquent, le résultat est vrai. Dans le deuxième exemple, l'argument `2 = 17` est faux ; par conséquent, le résultat est faux.  
  
```  
IF 1 = 1 AND 2 = 2  
BEGIN  
   PRINT 'First Example is TRUE'  
END  
ELSE PRINT 'First Example is FALSE';  
GO  
  
IF 1 = 1 AND 2 = 17  
BEGIN  
   PRINT 'Second Example is TRUE'  
END  
ELSE PRINT 'Second Example is FALSE' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [OÙ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

