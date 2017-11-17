---
title: IIF (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IIF_TSQL
- IIF
dev_langs:
- TSQL
helpviewer_keywords:
- IIF function
ms.assetid: e3ccf8ed-1cec-43ac-90b7-d8597c24b050
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 86ff2683e1ee71a3d11baa024753e0f52e5b3ee9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="logical-functions---iif-transact-sql"></a>Fonctions logiques - IIF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne l'une des deux valeurs possibles, selon que l'expression booléenne renvoie true ou false dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IIF ( boolean_expression, true_value, false_value )  
```  
  
## <a name="arguments"></a>Arguments  
 *boolean_expression*  
 Expression booléenne valide.  
  
 Si cet argument n'est pas une expression booléenne, une erreur de syntaxe est générée.  
  
 *true_value*  
 Valeur à retourner si *boolean_expression* a la valeur true.  
  
 *false_value*  
 Valeur à retourner si *boolean_expression* a la valeur false.  
  
## <a name="return-types"></a>Types de retour  
 Retourne le type de données avec la priorité la plus élevée parmi les types dans *true_value* et *false_value*. Pour plus d’informations, consultez [Priorités des types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Notes  
 IIF est un moyen rapide d'écrire une expression CASE. Elle évalue l'expression booléenne passée comme premier argument, puis retourne l'un des deux autres arguments selon le résultat de l'évaluation. Autrement dit, le *true_value* est retourné si l’expression booléenne est true et le *false_value* est retourné si l’expression booléenne est false ou unknown. *true_value* et *false_value* peut être de n’importe quel type. Les règles qui s'appliquent à l'expression CASE pour les expressions booléennes, la gestion de la valeur NULL et les types de retour s'appliquent également à IIF. Pour plus d’informations, consultez [cas &#40; Transact-SQL &#41; ](../../t-sql/language-elements/case-transact-sql.md).  
  
 Le fait que IIF soit convertie en CASE a également un impact sur d'autres aspects du comportement de cette fonction. Étant donné que les expressions CASE peuvent être imbriquées seulement jusqu'à un niveau de 10, les instructions IIF peuvent également être imbriquées uniquement jusqu'à un niveau maximal de 10. En outre, IIF est exécutée à distance sur d'autres serveurs en tant qu'expression CASE sémantiquement équivalente, avec tous les comportements d'une expression CASE exécutée à distance.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-iif-example"></a>A. Exemple IIF simple  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a > @b, 'TRUE', 'FALSE' ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------  
TRUE  
  
(1 row(s) affected)  
```  
  
### <a name="b-iif-with-null-constants"></a>B. IIF avec des constantes NULL  
  
```  
SELECT IIF ( 45 > 30, NULL, NULL ) AS Result;  
```  
  
 Le résultat de cette instruction est une erreur.  
  
### <a name="c-iif-with-null-parameters"></a>C. IIF avec des paramètres NULL  
  
```  
DECLARE @P INT = NULL, @S INT = NULL;  
SELECT IIF ( 45 > 30, @p, @s ) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
--------  
NULL  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAS &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Choisissez &#40; Transact-SQL &#41;](../../t-sql/functions/logical-functions-choose-transact-sql.md)  
  
  

