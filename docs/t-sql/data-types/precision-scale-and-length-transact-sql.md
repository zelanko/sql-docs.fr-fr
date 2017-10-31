---
title: "Précision, échelle et longueur (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], length
- data types [SQL Server], scale
- precision [SQL Server], data types
- lengths [SQL Server], data types
- number of digits
- scale [SQL Server]
- scale [SQL Server], data types
- data types [SQL Server], precision
ms.assetid: fbc9ad2c-0d3b-4e98-8fdd-4d912328e40a
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 557d7a5c45e9cc5a0839dfb4a1fdb0d08c2bf83f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="precision-scale-and-length-transact-sql"></a>Précision, échelle et longueur (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

La précision est le nombre de chiffres qui composent un nombre. L'échelle est le nombre de chiffres à droite du séparateur décimal dans un nombre. Par exemple, le nombre 123,45 a une précision de 5 et une échelle de 2.
  
Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la précision maximale par défaut **numérique** et **décimal** des types de données est 38. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], elle est de 28.
  
La longueur d'un type de données numérique est le nombre d'octets utilisés pour stocker le nombre. La longueur d'un type de données chaîne de caractères ou Unicode est le nombre de caractères. La longueur de **binaire**, **varbinary**, et **image** des types de données est le nombre d’octets. Par exemple, un **int** type de données peut contenir 10 chiffres, est stocké sur 4 octets et n’accepte pas de décimales. Le **int** type de données a une précision de 10, une longueur de 4 et une échelle de 0.
  
Lorsque deux **char**, **varchar**, **binaire**, ou **varbinary** expressions sont concaténées, la longueur de l’expression obtenue est la somme des longueurs des deux expressions sources ou 8 000 caractères, plus petite étant retenue.
  
Lorsque deux **nchar** ou **nvarchar** expressions sont concaténées, la longueur de l’expression obtenue est la somme des longueurs des deux expressions sources, soit 4 000 caractères, plus petite étant retenue.
  
Lorsque deux expressions de même type mais de longueur différente sont comparées à l'aide des fonctions UNION, EXCEPT ou INTERSECT, la longueur du résultat est la longueur maximale des deux expressions.
  
La précision et l’échelle des types de données numériques en plus de **décimal** sont fixes. Si un opérateur arithmétique agit sur deux expressions du même type, le résultat est du même type de données, avec la précision et l'échelle définies pour ce type. Si un opérateur agit sur deux expressions de types de données numériques différents, les règles de priorité des types de données déterminent le type du résultat. Le résultat a la précision et l'échelle définies pour son type de données.
  
Le tableau suivant définit la façon dont la précision et l’échelle du résultat sont calculées lorsque le résultat d’une opération est de type **décimal**. Le résultat est **décimal** lorsque une des opérations suivantes est vraie :
-   Les deux expressions sont **décimal**.  
-   Une expression est **décimal** et l’autre est un type de données avec une priorité inférieure à celle **décimal**.  
  
Les expressions des opérandes sont notées e1 et e2, avec respectivement les précisions p1 et p2 et les échelles s1 et s2. La précision et l’échelle d’une expression qui n’est pas **décimal** est la précision et l’échelle définies pour le type de données de l’expression.
  
|Opération|Précision du résultat|Échelle du résultat *|  
|---|---|---|
|e1 + e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 - e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 * e2|p1 + p2 + 1|s1 + s2|  
|e1 / e2|p1 - s1 + s2 + max(6, s1 + p2 + 1)|max(6, s1 + p2 + 1)|  
|E1 {UNION &#124; À l’exception de &#124; INTERSECT} e2|max(s1, s2) + max(p1-s1, p2-s2)|max(s1, s2)|  
|e1 % e2|min(p1-s1, p2 -s2) + max( s1,s2 )|max(s1, s2)|  
  
\*La précision du résultat et l’échelle ont une valeur absolue maximale de 38. Lors de la précision du résultat est supérieure à 38, elle est réduite à 38, et l’échelle correspondante est réduite pour empêcher la troncature de la partie entière d’un résultat. Dans certains cas, tels que la multiplication ou une division, facteur d’échelle n’est pas réduite pour maintenir la précision décimale, bien que l’erreur de dépassement de capacité peut être déclenché.

Dans les opérations d’addition et soustraction, nous devons `max(p1 – s1, p2 – s2)` emplacements de stockage partie intégrante du nombre décimal. Si il espace est insuffisant pour stocker les c'est-à-dire `max(p1 – s1, p2 – s2) < min(38, precision) – scale`, l’échelle est réduite afin de fournir suffisamment d’espace pour la partie entière. L’échelle qui en résulte est `MIN(precision, 38) - max(p1 – s1, p2 – s2)`, de sorte que la partie fractionnaire peut être arrondie pour tenir dans l’échelle qui en résulte.

Dans les opérations de multiplication et division, nous devons `precision - scale` emplacements de stockage de la partie entière du résultat. L’échelle risque d’être réduite à l’aide des règles suivantes :
1.  L’échelle qui en résulte est réduit à `min(scale, 38 – (precision-scale))` si la partie entière est inférieure à 32, car il ne peut pas être supérieur à `38 – (precision-scale)`. Résultat peut être arrondi dans ce cas.
1. L’échelle ne changera pas si elle est inférieure à 6, et si la partie entière est supérieure à 32. Dans ce cas, les erreurs de dépassement de capacité peut être levée si elle ne peut pas tenir dans décimal (38, échelle) 
1. L’échelle est fixée à 6 si elle est supérieure à 6, et si la partie entière est supérieure à 32. Dans ce cas, fait partie intégrante et l’échelle sont ramenés et type résultant est decimal(38,6). Résultat peut être arrondi à 6 décimales ou erreur de dépassement de capacité sera levée si la partie intégrante ne peut contenir 32 chiffres.

## <a name="examples"></a>Exemples
L’expression suivante retourne le résultat `0.00000090000000000` sans arrondi, étant donné que le résultat s’adaptent à `decimal(38,17)`:
```sql
select cast(0.0000009000 as decimal(30,20)) * cast(1.0000000000 as decimal(30,20)) [decimal 38,17]
```
Dans ce cas la précision est 61, et l’échelle est 40.
Partie intégrante (à l’échelle de précision = 21) est inférieure à 32, c’est le cas (1) dans les règles de multiplication et de mise à l’échelle est calculé comme étant `min(scale, 38 – (precision-scale)) = min(40, 38 – (61-40)) = 17`. Type de résultat est `decimal(38,17)`.

L’expression suivante retourne le résultat `0.000001` pour tenir dans `decimal(38,6)`:
```sql
select cast(0.0000009000 as decimal(30,10)) * cast(1.0000000000 as decimal(30,10)) [decimal(38, 6)]
```
Dans ce cas la précision est 61, et l’échelle est 20.
L’échelle est supérieure à 6 fait partie intégrante (`precision-scale = 41`) est supérieur à 32. C’est le cas (3) dans les règles de multiplication et le résultat est de type `decimal(38,6)`.

## <a name="see-also"></a>Voir aussi
[Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

