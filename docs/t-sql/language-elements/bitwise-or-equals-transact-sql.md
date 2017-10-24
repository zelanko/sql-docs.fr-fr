---
title: "| = (Opérateur de bits OR est égal à) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '|='
- '|=_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, |=
- '|= (bitwize OR equals)'
ms.assetid: bd746a4f-6498-4196-bf2e-b6f457a15d44
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 224f1c3e0dff0ad9e6a1816a6a12eea0392791ab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="-bitwise-or-equals-transact-sql"></a>|= (Bitwise OR EQUALS) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Exécute une opération de bits OR logique entre deux valeurs entières spécifiées, traduites en expressions binaires dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)], et affecte une valeur au résultat de l'opération.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression |= expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) de tout des données de type de catégorie numérique, à l’exception du **bits** type de données.  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données de l'argument ayant la priorité la plus élevée. Pour plus d’informations, consultez [Priorités des types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [&#124; &#40; Opérateur de bits OR &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/bitwise-or-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Opérateurs de bits &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  

