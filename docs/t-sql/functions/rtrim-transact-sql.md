---
title: RTRIM (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RTRIM_TSQL
- RTRIM
dev_langs: TSQL
helpviewer_keywords:
- RTRIM function
- character strings [SQL Server], trailing blanks
- blank characters [SQL Server]
- trailing blanks
ms.assetid: 52fd6e8d-650c-4f66-abcf-67765aa5aa83
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 25675a181225e600a16738f50322fdabcae839a4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="rtrim-transact-sql"></a>RTRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une chaîne de caractères après troncature de tous les espaces de fin.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RTRIM ( character_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) des données de caractères. *character_expression* peut être une constante, une variable ou une colonne de données binaire ou caractère.  
  
 *character_expression* doit être de type de données qui est implicitement convertible en **varchar**. Sinon, utilisez [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) pour convertir explicitement *character_expression*.  
  
## <a name="return-types"></a>Types de retour  
 **varchar** ou **nvarchar**  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-example"></a>A. Exemple simple  
 L'exemple suivant accepte une chaîne de caractères qui contient des espaces à la fin de la phrase, et retourne le texte sans espaces à la fin de la phrase.  
  
```  
SELECT RTRIM('Removes trailing spaces.   ');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
  `Removes trailing spaces.`  
  
### <a name="b-simple-example"></a>B : exemple  
 L’exemple suivant montre comment utiliser `RTRIM` pour supprimer les espaces. Ce temps il est une autre chaîne concaténée à la première chaîne à afficher que les espaces ont disparu.  
  
```  
SELECT RTRIM('Four spaces are after the period in this sentence.    ') + 'Next string.';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
`Four spaces are after the period in this sentence.Next string.`  

### <a name="c-using-rtrim-with-a-variable"></a>C. Utilisation de RTRIM avec une variable  
 Cet exemple illustre l'utilisation de `RTRIM` pour supprimer les espaces à droite d'une variable caractère.  
  
```  
DECLARE @string_to_trim varchar(60);  
SET @string_to_trim = 'Four spaces are after the period in this sentence.    ';  
SELECT @string_to_trim + ' Next string.';  
SELECT RTRIM(@string_to_trim) + ' Next string.';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```sql   
 -------------------------------------------------------------------------  
 Four spaces are after the period in this sentence.     Next string.  
 
 (1 row(s) affected)`  
 
 -------------------------------------------------------------------------  
 Four spaces are after the period in this sentence. Next string.  
 
 (1 row(s) affected)
 ```  
  

  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
 [La fonction TRIM &#40; Transact-SQL &#41;](../../t-sql/functions/trim-transact-sql.md)  
 [LTRIM &#40; Transact-SQL &#41;](../../t-sql/functions/ltrim-transact-sql.md)  
  
  


