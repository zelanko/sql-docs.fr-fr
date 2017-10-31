---
title: La fonction TRIM (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 01/20/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TRIM
- TRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
caps.latest.revision: 4
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 64cef84a613d71e65b33bed1c1e740dc59eeed9d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="trim-transact-sql"></a>La fonction TRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

Supprime le caractère espace `char(32)` ou d’autres caractères spécifiés à partir du début ou la fin d’une chaîne.  
 
## <a name="syntax"></a>Syntaxe   
```
TRIM ( [ characters FROM ] string ) 
```
[//]: # "[LES DEUX | DÉBUT | FIN] ne pas encore disponible."

## <a name="arguments"></a>Arguments   

caractères   
Est un littéral, une variable ou un appel de fonction de n’importe quel type de caractère de non LOB (`nvarchar`, `varchar`, `nchar`, ou `char`) contenant des caractères qui doivent être supprimés. `nvarchar(max)`et `varchar(max)` les types ne sont pas autorisés.

chaîne   
Est une expression de n’importe quel type de caractère (`nvarchar`, `varchar`, `nchar`, ou `char`) où les caractères doivent être supprimés.

## <a name="return-types"></a>Types de retour   
Retourne une expression de caractères avec un type d’argument de chaîne dans laquelle le caractère espace `char(32)` ou autres caractères spécifiées sont supprimés des deux côtés. Retourne `NULL` si la chaîne d’entrée est `NULL`.

## <a name="remarks"></a>Notes   
Par défaut `TRIM` fonction supprime le caractère espace `char(32)` des deux côtés. Ceci équivaut à `LTRIM(RTRIM(@string))`. Comportement de `TRIM ` fonction avec des caractères spécifiés est identique au comportement de `REPLACE` fonction où les caractères de début ou de fin sont remplacées par des chaînes vides.


## <a name="examples"></a>Exemples
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Supprime l’espace des deux côtés de la chaîne   
L’exemple suivant supprime les espaces avant et après le mot `test`.   
```tsql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>B.  Supprime caractères spécifiés dans les deux côtés de la chaîne   
L’exemple suivant supprime un point final et les espaces de fin.
```tsql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>Voir aussi
[Fonctions de chaîne (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
[LTRIM (Transact-SQL)](../../t-sql/functions/ltrim-transact-sql.md)   
[RTRIM (Transact-SQL)](../../t-sql/functions/rtrim-transact-sql.md)   
[REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)   

