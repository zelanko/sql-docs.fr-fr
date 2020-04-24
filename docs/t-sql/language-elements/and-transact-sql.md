---
title: AND (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AND_TSQL
- AND
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], TRUE
- "TRUE"
- AND, about AND operators
- AND
- combining expressions
ms.assetid: b61d7f8d-5a51-49b7-91dd-f6190a5a0fb9
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 05d0a69e2dfa2551522fe7d0d8f067376526e19c
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632682"
---
# <a name="and-transact-sql"></a>AND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combine deux expressions booléennes et retourne la valeur **TRUE** lorsque les deux expressions ont la valeur **TRUE**. Lorsque plusieurs opérateurs logiques sont utilisés dans une instruction, les opérateurs **AND** sont évalués en premier. Vous pouvez modifier l'ordre de traitement en utilisant des parenthèses.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
boolean_expression AND boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 *boolean_expression*  
 Toute [expression](../../t-sql/language-elements/expressions-transact-sql.md) valide retournant une valeur booléenne : **TRUE**, **FALSE** ou **UNKNOWN**.  
  
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
|**UNKNOWN**|UNKNOWN|FALSE|UNKNOWN|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-the-and-operator"></a>R. Utilisation de l'opérateur AND  
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
 [Opérateurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
