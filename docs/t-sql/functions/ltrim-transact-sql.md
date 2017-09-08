---
title: LTRIM (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LTRIM
- LTRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- leading blanks
- deleting blank spaces
- characters [SQL Server], blanks
- removing blank spaces
- LTRIM function
- blank characters [SQL Server]
ms.assetid: 369ed340-1a09-4597-a9eb-6720156cd39a
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad63999f685b31848ea505fd5a671d1e163ddc91
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="ltrim-transact-sql"></a>LTRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une expression de caractères après la suppression de tous les espaces à gauche.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
LTRIM ( character_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de type binaire ou caractère. *character_expression* peut être une constante, une variable ou une colonne. *character_expression* doit être d’un type de données, hormis **texte**, **ntext**, et **image**, qui est implicitement convertible en **varchar**. Sinon, utilisez [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) pour convertir explicitement *character_expression*.  
  
## <a name="return-type"></a>Type de retour  
 **varchar** ou **nvarchar**  
  
## <a name="examples"></a>Exemples  

### <a name="a-simple-example"></a>A. Exemple simple   

 L’exemple suivant utilise la fonction LTRIM pour supprimer les espaces à partir d’une expression de caractères.  
  
```tsql  
SELECT LTRIM('     Five spaces are at the beginning of this string.') FROM sys.databases;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `---------------------------------------------------------------`  
  `Five spaces are at the beginning of this string.`  

### <a name="b-example-using-a-variable"></a>B : exemple à l’aide d’une variable   
  
 L'exemple suivant utilise `LTRIM` pour supprimer les espaces à droite d'une variable caractère.  
  
```  
DECLARE @string_to_trim varchar(60);  
SET @string_to_trim = '     5 spaces are at the beginning of this string.';  
SELECT 
    @string_to_trim AS 'Original string',
    LTRIM(@string_to_trim) AS 'Without spaces';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Original string Without spaces
--------------------------------------------------- ---------------------------------------------
     5 spaces are at the beginning of this string.  5 spaces are at the beginning of this string.
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  



