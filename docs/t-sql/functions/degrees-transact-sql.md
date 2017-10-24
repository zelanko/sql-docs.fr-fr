---
title: "DEGRÉS (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DEGREES
- DEGREES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DEGREES function
- number of degrees
ms.assetid: 5208de3c-90a3-4f59-a7e3-10b01bf285bb
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: b9c361e304bac38b51b31c65c029d5719aa8f006
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="degrees-transact-sql"></a>DEGREES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie l'angle en degrés correspondant à un angle spécifié en radians.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DEGREES ( numeric_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de la catégorie, de type de données numérique approximatives ou à l’exception de la **bits** type de données.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Retourne le même type que *numeric_expression*.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant renvoie la valeur en degrés d'un angle de PI/2 radians.  
  
```  
SELECT 'The number of degrees in PI/2 radians is: ' +   
CONVERT(varchar, DEGREES((PI()/2)));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The number of degrees in PI/2 radians is 90         
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions mathématiques &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  


