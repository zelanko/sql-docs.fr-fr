---
title: float et real (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- float
- real_TSQL
- real
- float_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- numeric data type, floating point
- float data type
- floating point data [SQL Server]
- real data type
ms.assetid: 08ea66b7-624e-4d8b-86bc-750ff76cdfc5
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 913aa9c71234d1b170a14f9707be82d45b1cd5b8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="float-and-real-transact-sql"></a>float et real (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Types de données approximatives à utiliser avec des données numériques à virgule flottante. Les données à virgule flottante sont approximatives ; il n'est donc pas possible de représenter précisément toutes les valeurs de ce type de données. Le synonyme ISO de **réel** est **float (24)**.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
**float** [ **(***n***)** ] où  *n*  est le nombre de bits qui sont utilisés pour stocker la mantisse de le **float** nombre en notation scientifique et, par conséquent, détermine la taille de la précision et de stockage. Si  *n*  est spécifié, il doit être une valeur comprise entre **1** et **53**. La valeur par défaut  *n*  est **53**.
  
|*n*valeur|Précision|Taille de stockage|  
|---|---|---|
|**1-24**|7 chiffres|4 octets|  
|**25-53**|15 chiffres|8 octets|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]traite  *n*  comme l’une des deux valeurs possibles. Si **1**<=n<=**24**,  *n*  est traité comme **24**. Si **25**<=n<=**53**,  *n*  est traité comme **53**.  
  
Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float**[**(n)**] type de données est conforme à la norme ISO pour toutes les valeurs de  *n*  de **1** via **53**. Le synonyme de **double précision** est **float (53)**.
  
## <a name="remarks"></a>Notes  
  
|Type de données|Plage|Stockage|  
|---|---|---|
|**float**|- 1,79E+308 à -2,23E-308, 0 et 2,23E-308 à 1,79E+308|Dépend de la valeur de*n*|  
|**real**|- 3,40E + 38 à -1,18E - 38, 0 et 1,18E - 38 à 3,40E + 38|Quatre octets|  
  
##  <a name="converting-float-and-real-data"></a>Conversion de données float et real  
Les valeurs de **float** sont tronquées lorsqu’elles sont converties en un type d’entier.
  
Si vous souhaitez convertir à partir de **float** ou **réel** en données caractères, à l’aide de la fonction de chaîne STR est généralement plus utile que CAST (). car STR permet un plus grand contrôle sur le format. Pour plus d’informations, consultez [STR &#40; Transact-SQL &#41; ](../../t-sql/functions/str-transact-sql.md) et [fonctions &#40; Transact-SQL &#41; ](../../t-sql/functions/functions.md).
  
Conversion de **float** valeurs qui utilisent la notation scientifique pour **décimal** ou **numérique** est limitée à des valeurs de précision de 17 chiffres uniquement. Toute valeur avec une précision plus élevée que 17 sera arrondie à zéro.
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Conversion de Type de données &#40; moteur de base de données &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  

