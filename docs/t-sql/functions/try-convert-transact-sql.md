---
title: TRY_CONVERT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRY_CONVERT_TSQL
- TRY_CONVERT
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_CONVERT function
ms.assetid: 3e6e7825-6482-4cb2-a8c2-9abc99e265a6
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0cb3854ae349b17dcdb0b0528c6415fd41b1e072
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="tryconvert-transact-sql"></a>TRY_CONVERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne une valeur convertie en type de données spécifié si la conversion aboutit ; sinon, retourne NULL.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TRY_CONVERT ( data_type [ ( length ) ], expression [, style ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *data_type [(longueur)]*  
 Type de données dans lequel convertir l’expression *expression*.  
  
 *expression*  
 Valeur à être converti.  
  
 *style*  
 Expression entière facultative qui spécifie comment la **TRY_CONVERT** fonction consiste à traduire *expression*.  
  
 *style* accepte les mêmes valeurs que le *style* paramètre de la **convertir** (fonction). Pour plus d’informations, consultez [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 La plage de valeurs acceptables est déterminée par la valeur de *data_type*. Si *style* est null, alors **TRY_CONVERT** retourne la valeur null.  
  
## <a name="return-types"></a>Types de retour  
 Retourne une valeur convertie en type de données spécifié si la conversion aboutit ; sinon, retourne NULL.  
  
## <a name="remarks"></a>Notes  
 **TRY_CONVERT** prend la valeur passée et tente de convertir le texte spécifié *data_type*. Si la conversion réussit, **TRY_CONVERT** retourne la valeur comme spécifié *data_type*; si une erreur se produit, la valeur null est retournée. Toutefois si vous demandez une conversion n’est pas explicitement autorisée, puis **TRY_CONVERT** échoue avec une erreur.  
  
 **TRY_CONVERT** est un mot clé réservé au niveau de compatibilité est 110 et supérieur.  
  
 Cette fonction peut être exécutée à distance sur des serveurs [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou version ultérieure. Elle ne peut pas être exécutée à distance sur des serveurs dont la version est antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-tryconvert-returns-null"></a>A. TRY_CONVERT retourne la valeur NULL.  
 L'exemple suivant montre que TRY_CONVERT retourne Null lorsque la conversion échoue.  
  
```tsql  
SELECT   
    CASE WHEN TRY_CONVERT(float, 'test') IS NULL   
    THEN 'Cast failed'  
    ELSE 'Cast succeeded'  
END AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------------  
Cast failed  
  
(1 row(s) affected)  
```  
  
 L'exemple suivant montre que l'expression doit être au format attendu.  
  
```tsql  
SET DATEFORMAT dmy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-tryconvert-fails-with-an-error"></a>B. TRY_CONVERT échoue avec une erreur  
 L'exemple suivant montre que TRY_CONVERT retourne une erreur lorsque la conversion n'est pas autorisée explicitement.  
  
```tsql  
SELECT TRY_CONVERT(xml, 4) AS Result;  
GO  
```  
  
 Le résultat de cette instruction est une erreur, car un entier ne peut pas être converti en un type de données XML.  
  
```  
Explicit conversion from data type int to xml is not allowed.  
```  
  
### <a name="c-tryconvert-succeeds"></a>C. TRY_CONVERT réussit  
 Cet exemple suivant montre que l'expression doit être au format attendu.  
  
```  
SET DATEFORMAT mdy;  
SELECT TRY_CONVERT(datetime2, '12/31/2010') AS Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
----------------------------------  
2010-12-31 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

