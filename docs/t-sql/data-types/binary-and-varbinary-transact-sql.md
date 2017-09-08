---
title: binary et varbinary (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- binary_TSQL
- varbinary_TSQL
- binary
- varbinary
dev_langs:
- TSQL
helpviewer_keywords:
- varbinary data type
- binary [SQL Server], about binary data type
ms.assetid: bcce65f9-10db-4b3e-bfaf-dfc06c6f820f
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e6aaf00b8e846316c92897360932703a013150e8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="binary-and-varbinary-transact-sql"></a>binary et varbinary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Données de type binaire de longueur fixe (binary) ou variable (varbinary).
  
## <a name="arguments"></a>Arguments  
**binaire** [(  *n*  )] données binaires de longueur fixe avec une longueur de  *n*  octets, où  *n*  est une valeur comprise entre 1 et 8 000 caractères. La taille de stockage est  *n*  octets.
  
**varbinary** [(  *n*   |  **max**)] données binaires de longueur Variable. *n*peut être une valeur comprise entre 1 et 8 000 caractères. **max** indique que la taille de stockage maximale est de 2 ^ 31-1 octets. La taille mémoire est la longueur réelle des données entrées, plus deux octets. Les données entrées peuvent avoir une longueur de 0 octet. Le synonyme SQL ANSI de **varbinary** est **variable binaire**.
  
## <a name="remarks"></a>Notes  
Lorsque  *n*  n’est pas spécifié dans une définition de données ou d’une instruction de déclaration de variable, la longueur par défaut est 1. Lorsque  *n*  n’est pas spécifié avec la fonction CAST, la longueur par défaut est 30.

| Type de données | Cas d’utilisation |
| --- | --- |
| **binaire** | les tailles des entrées de données de colonne sont cohérentes.|
| **varbinary** | les tailles des entrées de données de colonne de varient considérablement.|
| **varbinary(max)** | les entrées de données de colonne dépassent 8 000 octets.|


## <a name="converting-binary-and-varbinary-data"></a>Conversion de données binary et varbinary
Lorsque les données sont converties à partir d’un type de données string (**char**, **varchar**, **nchar**, **nvarchar**, **binaire**, **varbinary**, **texte**, **ntext**, ou **image**) à un **binaire** ou **varbinary** type de données de longueur différente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] complète ou tronque les données sur la droite. Lorsque les autres types de données sont convertis en **binaire** ou **varbinary**, les données sont complétées ou tronquées à gauche. Elles sont complétées avec des zéros hexadécimaux.
  
Conversion de données pour le **binaire** et **varbinary** des types de données est utile si **binaire** données sont le moyen le plus simple pour vous déplacer dans les données. Conversion d’une valeur de n’importe quel type en une valeur binaire de grande taille suffisante et puis vers le type, engendre toujours la même valeur si les deux conversions sont en cours sur la même version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La représentation binaire d'une valeur peut varier d'une version à l'autre de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
Vous pouvez convertir **int**, **smallint**, et **tinyint** à **binaire** ou **varbinary**, mais si vous convertissez la **binaire** valeur à une valeur entière, cette valeur sera différente de la valeur d’entier d’origine si la troncation s’est produite. Par exemple, l'instruction SELECT suivante montre que la valeur entière `123456` est généralement stockée sous forme binaire `0x0001e240` :
  
```sql
SELECT CAST( 123456 AS BINARY(4) );  
```  
  
Toutefois, ce qui suit `SELECT` instruction montre que si la **binaire** cible est trop petite pour contenir la valeur entière, les chiffres de début sont tronquées en mode silencieux afin que le même nombre soit stocké en tant que `0xe240`:
  
```sql
SELECT CAST( 123456 AS BINARY(2) );  
```  
  
L'instruction suivante montre que la troncation discrète peut affecter les opérations arithmétiques sans engendrer d'erreur :
  
```sql
DECLARE @BinaryVariable2 BINARY(2);  
  
SET @BinaryVariable2 = 123456;  
SET @BinaryVariable2 = @BinaryVariable2 + 1;  
  
SELECT CAST( @BinaryVariable2 AS INT);  
GO  
```  
  
Le résultat final est `57921`, et non pas `123457`.
  
> [!NOTE]  
>  Conversions entre des données de type et le **binaire** des types de données ne sont pas garanti que le même entre différentes versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Conversion de Type de données &#40; moteur de base de données &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

