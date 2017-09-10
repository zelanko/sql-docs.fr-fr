---
title: ASCII (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASCII_TSQL
- ASCII
dev_langs:
- TSQL
helpviewer_keywords:
- ASCII function
- characters [SQL Server], ASCII
- code [SQL Server], ASCII
- leftmost character of expression
ms.assetid: 45c2044a-0593-4805-8bae-0fad4bde2e6b
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d2c65df1f005b3d624f6a56f689f4125ec8175a7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="ascii-transact-sql"></a>ASCII (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne la valeur du code ASCII du caractère situé le plus à gauche dans une expression de caractères.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
ASCII ( character_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*character_expression*  
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) du type **char** ou **varchar**.
  
## <a name="return-types"></a>Types de retour
 **int**  
  
## <a name="remarks"></a>Notes
ASCII est l’abréviation de American Code Standard pour l’échange d’informations. Il s’agit d’un standard utilisé par les ordinateurs de codage de caractères. Pour obtenir la liste des caractères ASCII, consultez le **caractères imprimables** section de [ASCII](https://www.wikipedia.org/wiki/ASCII).

## <a name="examples"></a>Exemples  
L’exemple suivant suppose un jeu de caractères ASCII et retourne le `ASCII` valeur de 6 caractères.
  
```sql
SELECT ASCII('A') AS A, ASCII('B') AS B,   
ASCII('a') AS a, ASCII('b') AS b,  
ASCII(1) AS [1], ASCII(2) AS [2];  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
A           B           a           b           1           2  
----------- ----------- ----------- ----------- ----------- -----------  
65          66          97          98          49          50  
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)
  
  



