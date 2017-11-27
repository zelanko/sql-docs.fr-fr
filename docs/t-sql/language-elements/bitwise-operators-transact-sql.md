---
title: "Opérateurs au niveau du bit (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 09/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- operators [Transact-SQL], bitwise
- bitwise operators
- bit manipulations
ms.assetid: 2b994cf5-2daa-438a-b8c7-4bd8d451ac8d
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: f9441cf26142e70340e23212991665f67fb7bf62
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="bitwise-operators-transact-sql"></a>Opérateurs au niveau du bit (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Les opérateurs au niveau du bit exécutent des manipulations de bits entre deux expressions de tout type de données de la catégorie entier.  
  Opérateurs de bits convertir bits binaires des deux valeurs entières, effectuez l’opération AND, OR, ou pas d’opération sur chaque bit, un résultat. Convertit ensuite le résultat en un entier.  
  
  Par exemple, l’entier 170 convertit en binaire 1010 1010.
Convertit l’entier 75 0100 1011 binaire.

|operator|mathématiques au niveau du bit|
|---- |---- |
|AND <br> Si bits à n’importe quel emplacement 1, le résultat est 1. |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 0000 1010 =  10 |
|ou <br> Si des bits à n’importe quel emplacement sont 1, le résultat est 1. |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 1110 1011 = 235|
|NOT  <br> Inverse la valeur du bit à chaque emplacement de bit. |1010 1010 = 170 <br>----------------- <br>  0101 0101 =   85 |
  
Consultez les rubriques suivantes :   
* [& &#40; Opération de bits AND &#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md)  
* [& = &#40; Assignation de bits AND &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
* [&#124; &#40; Opérateur de bits OR &#41;](../../t-sql/language-elements/bitwise-or-transact-sql.md)  
* [&#124; = &#40; Opérateur de bits OR affectation &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
* [^ &#40; Opérateur de bits OR exclusif &#41;](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md)  
* [^ = &#40; Opérateur de bits OR exclusif affectation &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)  
* [~ &#40; Opération de bits NOT &#41;](../../t-sql/language-elements/bitwise-not-transact-sql.md)  
  
 Les opérandes des opérateurs au niveau du bit peuvent être l’un des types de données de l’entier ou les catégories de types de données de chaîne binaire (à l’exception de la **image** type de données), sauf que les deux opérandes ne peut pas être l’un des types de données de la catégorie de type de données de chaîne binaire. Ce tableau indique les types de données d'opérandes pris en charge.  
  
|Opérande de gauche|Opérande de droite|  
|------------------|-------------------|  
|[binaire](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint**, ou **tinyint**|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|**int**, **smallint**, **tinyint**, ou **bits**|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binaire**, ou **varbinary**|  
|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binaire**, ou **varbinary**|  
|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**, **smallint**, **tinyint**, **binaire**, ou **varbinary**|  
|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**, **smallint**, ou **tinyint**|  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Compound, opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
  
