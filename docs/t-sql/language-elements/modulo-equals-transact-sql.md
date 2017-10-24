---
title: "Modulo égal à (Transact-SQL) | Documents Microsoft"
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
- '%=_TSQL'
- '%='
dev_langs:
- TSQL
helpviewer_keywords:
- '%= (modulo equals)'
- compound operators, %=
ms.assetid: 45e35516-1f4c-406b-a580-70a14b087847
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5d425882e4d0e6b16334bcd0ec7dc5af0487a5c0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="modulo-equals-transact-sql"></a>Modulo EQUALS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Divise un nombre par un autre et affecte une valeur au résultat de l'opération. Par exemple, si une variable @x égal à 38, puis @x % = 5 prend la valeur d’origine @x, divise par 5 et affecte @x pour le reste de cette division (3).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression %= expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) de tout des données de type de catégorie numérique, à l’exception du **bits** type de données.  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données de l'argument ayant la priorité la plus élevée. Pour plus d’informations, consultez [Priorités des types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [Modulo &#40; Transact-SQL &#41; ](../../t-sql/language-elements/modulo-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

