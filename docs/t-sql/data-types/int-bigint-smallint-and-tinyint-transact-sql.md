---
title: int, bigint, smallint et tinyint (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 9/8/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bigint_TSQL
- smallint
- bigint
- smallint_TSQL
- tinyint_TSQL
- int_TSQL
- int
- tinyint
dev_langs: TSQL
helpviewer_keywords:
- exact numeric data [SQL Server]
- numeric data
- tinyint data type
- int data type
- smallint data type
ms.assetid: 9bda5b0b-2380-4931-a1c8-f362fdefa99b
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 2e99ccb97dc5c36f8b7870a042963d6302b3f1eb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="int-bigint-smallint-and-tinyint-transact-sql"></a>int, bigint, smallint et tinyint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Types de données représentant des valeurs numériques exactes qui utilisent des entiers. Pour économiser de l’espace dans la base de données, utilisez le plus petit type de données qui peut contenir fiable de toutes les valeurs possibles. Par exemple, tinyint peut suffire pour la durée de vie d’une personne, car aucun habite à plus de 255 ans. Mais tinyint ne serait pas suffisant pour la durée de vie d’une génération, car une génération peut être plus de 255 ans.
  
|Type de données|Plage|Stockage|  
|---|---|---|
|**bigint**|-2^63 (-9,223,372,036,854,775,808) à 2^63-1 (9,223,372,036,854,775,807)|Huit octets|  
|**int**|-2^31 (-2 147 483 648) à 2^31-1 (2 147 483 647)|Quatre octets|  
|**smallint**|-2^15 (-32 768) à 2^15-1 (32 767)|Deux octets|  
|**tinyint**|0 à 255|Un octet|  
  
## <a name="remarks"></a>Notes  
Le **int** type de données est le type de données integer principal dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le **bigint** type de données est destiné à utiliser lorsque les valeurs entières peuvent dépasser la plage prise en charge par le **int** type de données.
  
**bigint** s’insère entre **smallmoney** et **int** dans le graphique de priorité de type de données.
  
Fonctions retournent **bigint** uniquement si l’expression de paramètre est un **bigint** type de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ne promeut pas automatiquement les autres types de données integer (**tinyint**, **smallint**, et **int**) à **bigint**.
  
> [!CAUTION]  
>  Lorsque vous utilisez le +, -, \*, /, ou % des opérateurs arithmétiques pour effectuer une conversion implicite ou explicite de **int**, **smallint**, **tinyint**, ou **bigint** des valeurs de constante pour le **float**, **réel**, **décimal** ou **numérique** les types de données, les règles qui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’applique lorsqu’il calcule le type de données et la précision des résultats des expressions diffèrent selon que la requête est automatiquement paramétrable ou non.  
>   
>  Par conséquent, des expressions similaires dans les requêtes peuvent parfois produire des résultats différents. Lorsqu’une requête n’est pas automatiquement paramétrable, la valeur de constante est d’abord convertie à **numérique**, dont la précision est suffisamment grande pour contenir la valeur de la constante, avant de convertir le type de données spécifié. Par exemple, la valeur de constante 1 est convertie pour **numérique (1, 0)**, et la valeur de constante 250 est convertie en **numérique (3, 0)**.  
>   
>  Lorsqu’une requête est automatiquement paramétrable, la valeur de constante est toujours convertie en **numérique (10, 0)** avant de convertir le type de données final. Lorsque l'opérateur / est impliqué, outre la précision du type de résultat, la valeur de résultat peut aussi différer parmi des requêtes similaires. Par exemple, la valeur de résultat d’une requête paramétrée automatiquement qui comprend l’expression `SELECT CAST (1.0 / 7 AS float)`, diffère de la valeur de résultat de la même requête qui n’est pas paramétrée automatiquement, car les résultats de la requête paramétrée automatiquement, sont tronquées pour contenir dans le **numérique (10, 0)** type de données.  
  
## <a name="converting-integer-data"></a>Conversion de données integer
Lorsque les entiers sont convertis implicitement en un type de données character, si l'entier est trop grand pour le champ de caractère, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche le caractère ASCII 42, l'astérisque (*).
  
Constantes entières supérieures à 2 147 483 647 sont converties en la **décimal** de type de données, pas le **bigint** type de données. L’exemple suivant montre que lorsque la valeur de seuil est dépassée, le type de données du résultat de la passe d’un **int** à un **décimal**.
  
```sql
SELECT 2147483647 / 2 AS Result1, 2147483649 / 2 AS Result2 ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result1      Result2  
1073741823   1073741824.500000  
```  
  
## <a name="examples"></a>Exemples  
L’exemple suivant crée une table à l’aide de la **bigint**, **int**, **smallint**, et **tinyint** des types de données. Les valeurs sont insérées dans chaque colonne et retournées dans l'instruction SELECT.
  
```sql
CREATE TABLE dbo.MyTable  
(  
  MyBigIntColumn bigint  
,MyIntColumn  int
,MySmallIntColumn smallint
,MyTinyIntColumn tinyint
);  
  
GO  
  
INSERT INTO dbo.MyTable VALUES (9223372036854775807, 2147483647,32767,255);  
 GO  
SELECT MyBigIntColumn, MyIntColumn, MySmallIntColumn, MyTinyIntColumn  
FROM dbo.MyTable;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
MyBigIntColumn       MyIntColumn MySmallIntColumn MyTinyIntColumn  
-------------------- ----------- ---------------- ---------------  
9223372036854775807  2147483647  32767            255  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
