---
title: TRIM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- TRIM
- TRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azure-sqldw-latest||=azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0bc2d3f4564438076f0f488b03368c335326ff02
ms.sourcegitcommit: ccea98fa0768d01076cb6ffef0b4bdb221b2f9d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65560046"
---
# <a name="trim-transact-sql"></a>TRIM (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-asdw-xxx-md.md)]

Supprime le caractère espace `char(32)` ou d’autres caractères spécifiés au début ou à la fin d’une chaîne.  

## <a name="syntax"></a>Syntaxe

```
-- Syntax for SQL Server and Azure SQL Database
TRIM ( [ characters FROM ] string )
```

```
-- Syntax for Azure SQL Data Warehouse
TRIM ( string )
```

## <a name="arguments"></a>Arguments

L’argument characters est un littéral, une variable ou un appel de fonction de n’importe quel type de caractères non LOB (`nvarchar`, `varchar`, `nchar` ou `char`) contenant des caractères à supprimer. Les types `nvarchar(max)` et `varchar(max)` ne sont pas autorisés.

L’argument string est une expression de n’importe quel type de caractères (`nvarchar`, `varchar`, `nchar` ou `char`) dans laquelle des caractères doivent être supprimés.

## <a name="return-types"></a>Types de retour

Renvoie une expression de caractères avec un type d’argument de chaîne dans laquelle le caractère espace `char(32)` ou d’autres caractères spécifiés sont supprimés des deux côtés. Renvoie `NULL` si la chaîne d’entrée est `NULL`.

## <a name="remarks"></a>Notes 

Par défaut, la fonction `TRIM` supprime le caractère espace `char(32)` des deux côtés. Ce comportement est équivalent à `LTRIM(RTRIM(@string))`. Le comportement de la fonction `TRIM` avec des caractères spécifiés est identique au comportement de la fonction `REPLACE` quand les caractères de début ou de fin sont remplacés par des chaînes vides.

## <a name="examples"></a>Exemples

### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  Supprimer le caractère espace des deux côtés de la chaîne

L’exemple suivant supprime les espaces avant et après le mot `test`.

```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

`test`

### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>B.  Supprimer les caractères spécifiés des deux côtés de la chaîne

L’exemple suivant supprime un point final et les espaces à droite.

```sql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
`#     test`

## <a name="see-also"></a> Voir aussi

 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)
