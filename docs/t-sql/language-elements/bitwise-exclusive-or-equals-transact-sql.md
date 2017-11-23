---
title: ^ = (Exclusive au niveau du bit ou assignation) (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ^=
- ^=_TSQL
dev_langs: TSQL
helpviewer_keywords:
- ^= (bitwise exclusive OR equals)
- compound operators, ^=
- assignment operators, ^=
- augmented operators, ^=
ms.assetid: ce524b0f-a24d-44e7-bd5b-b6943793cd48
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ea63dff67d76e51b04e5ed6f994820a3797b91d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="-bitwise-exclusive-or-assignment-transact-sql"></a>^ = (Exclusive au niveau du bit ou assignation) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Effectue une opération de bits OR exclusive entre deux valeurs entières, et affecte une valeur au résultat de l'opération.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression ^= expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) de tout des données de type de catégorie numérique, à l’exception du **bits** type de données.  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données de l'argument ayant la priorité la plus élevée. Pour plus d’informations, consultez [Priorités des types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [^ &#40; Opérateur de bits OR exclusif &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Opérateurs de bits &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  
