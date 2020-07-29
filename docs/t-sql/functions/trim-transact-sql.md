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
author: julieMSFT
ms.author: jrasnick
monikerRange: = azure-sqldw-latest||=azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3d17b3012e68e08af24ea1fe2b93cb02f206a69a
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87113289"
---
# <a name="trim-transact-sql"></a>TRIM (Transact-SQL)

[!INCLUDE [sqlserver2017-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2017-asdb-asdbmi-asa.md)]

Supprime le caractère espace `char(32)` ou d’autres caractères spécifiés au début et à la fin d’une chaîne.  

## <a name="syntax"></a>Syntaxe

```
-- Syntax for SQL Server and Azure SQL Database
TRIM ( [ characters FROM ] string )
```

```
-- Syntax for Azure SQL Data Warehouse
TRIM ( string )
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments

L’argument characters est un littéral, une variable ou un appel de fonction de n’importe quel type de caractères non LOB (`nvarchar`, `varchar`, `nchar` ou `char`) contenant des caractères à supprimer. Les types `nvarchar(max)` et `varchar(max)` ne sont pas autorisés.

L’argument string est une expression de n’importe quel type de caractères (`nvarchar`, `varchar`, `nchar` ou `char`) dans laquelle des caractères doivent être supprimés.

## <a name="return-types"></a>Types de retour

Renvoie une expression de caractères avec un type d’argument de chaîne dans laquelle le caractère espace `char(32)` ou d’autres caractères spécifiés sont supprimés des deux côtés. Renvoie `NULL` si la chaîne d’entrée est `NULL`.

## <a name="remarks"></a>Notes

Par défaut, la fonction `TRIM` supprime le caractère d’espacement aux deux extrémités de la chaîne. Ce comportement est équivalent à `LTRIM(RTRIM(@string))`.

## <a name="examples"></a>Exemples

### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>R.  Supprimer le caractère espace des deux côtés de la chaîne

L’exemple suivant supprime les espaces avant et après le mot `test`.

```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

```
test
```

### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>B.  Supprimer les caractères spécifiés des deux côtés de la chaîne

L’exemple suivant supprime les espaces et le point avant `#` et après le mot `test`.

```sql
SELECT TRIM( '.,! ' FROM  '     #     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
#     test
```

## <a name="see-also"></a>Voir aussi

- [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
- [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
- [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
- [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
- [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
- [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
- [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)
