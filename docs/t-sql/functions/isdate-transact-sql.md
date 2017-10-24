---
title: ISDATE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISDATETIME
- ISDATE_TSQL
- ISDATE
- ISDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], ISDATE
- validate dates times [SQL Server]
- formats [SQL Server], time
- dates [SQL Server], validate
- verify dates times [SQL Server]
- functions [SQL Server], time
- formats [SQL Server], dates
- functions [SQL Server], date and time
- time [SQL Server], functions
- time [SQL Server], validate
- ISDATE function [SQL Server]
ms.assetid: 8e2c9ee7-388a-432f-b2c9-7b398f26bf85
caps.latest.revision: 54
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e005b11ad15170dcc2f6f45441d62e6ccc29570
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="isdate-transact-sql"></a>ISDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne 1 si le *expression* n’est valide **date**, **temps**, ou **datetime** valeur ; sinon, 0.  
  
 ISDATE retourne 0 si le *expression* est un **datetime2** valeur.  
  
 Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md). Notez que la plage de données datetime est comprise entre 1753-01-01 et 9999-12-31, tandis que la plage de données date est comprise entre 0001-01-01 et 9999-12-31.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ISDATE ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est une chaîne de caractères ou [expression](../../t-sql/language-elements/expressions-transact-sql.md) qui peut être converti en une chaîne de caractères. L'expression doit comporter moins de 4 000 caractères. Les types de données de date et d'heure, sauf datetime et smalldatetime, ne sont pas autorisés comme argument pour ISDATE.  
  
## <a name="return-type"></a>Type de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 ISDATE est déterministe uniquement si vous l’utilisez avec le [convertir](../../t-sql/functions/cast-and-convert-transact-sql.md) fonctionner, si le paramètre de style CONVERT est spécifié, et style n’est pas égal à 0, 100, 9 ou 109.  
  
 La valeur de retour d’ISDATE dépend des paramètres définis par [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md), [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) et [configurer l’Option de Configuration de serveur de la langue par défaut](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md).  
  
## <a name="isdate-expression-formats"></a>Formats d'expression ISDATE  
 Pour obtenir des exemples de formats valides pour lesquels ISDATE retourne 1, consultez la section « Prise en charge Formats littéraux de chaîne pour datetime » dans le [datetime](../../t-sql/data-types/datetime-transact-sql.md) et [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) rubriques. Pour obtenir des exemples supplémentaires, consultez également la colonne d’entrée/sortie de la section « Arguments » de [CAST et CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
 Le tableau suivant résume les formats d'expression d'entrée qui ne sont pas valides et qui retournent 0 ou une erreur.  
  
|Expression ISDATE|Valeur retournée par ISDATE|  
|-----------------------|-------------------------|  
|NULL|0|  
|Les valeurs des types de données répertoriées dans [des Types de données](../../t-sql/data-types/data-types-transact-sql.md) dans une catégorie de type de données autres que des chaînes de caractères, les chaînes de caractères Unicode, ou date et heure.|0|  
|Les valeurs de **texte**, **ntext**, ou **image** des types de données.|0|  
|Toute valeur qui a une échelle de précision en secondes supérieure à 3 (,0000 à ,0000000...n). ISDATE retourne 0 si le *expression* est un **datetime2** valeur, mais retourne 1 si le *expression* n’est valide **datetime** valeur.|0|  
|Toute valeur qui associe une date valide à une valeur non valide, par exemple 1995-10-1a.|0|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-isdate-to-test-for-a-valid-datetime-expression"></a>A. Utilisation d'ISDATE pour tester une expression datetime valide.  
 L’exemple suivant vous montre comment utiliser `ISDATE` pour tester si une chaîne de caractères est valide **datetime**.  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    PRINT 'VALID'  
ELSE  
    PRINT 'INVALID';  
```  
  
### <a name="b-showing-the-effects-of-the-set-dateformat-and-set-language-settings-on-return-values"></a>B. Illustration des effets des paramètres SET DATEFORMAT et SET LANGUAGE sur les valeurs de retour  
 Les instructions suivantes affichent les valeurs qui sont retournées suite aux paramètres de `SET DATEFORMAT` et `SET LANGUAGE`.  
  
```  
/* Use these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
/* Expression in mdy dateformat */  
SELECT ISDATE('04/15/2008'); --Returns 1.  
/* Expression in mdy dateformat */  
SELECT ISDATE('04-15-2008'); --Returns 1.   
/* Expression in mdy dateformat */  
SELECT ISDATE('04.15.2008'); --Returns 1.   
/* Expression in myd  dateformat */  
SELECT ISDATE('04/2008/15'); --Returns 1.  
  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET DATEFORMAT dmy;  
SELECT ISDATE('15/04/2008'); --Returns 1.  
SET DATEFORMAT dym;  
SELECT ISDATE('15/2008/04'); --Returns 1.  
SET DATEFORMAT ydm;  
SELECT ISDATE('2008/15/04'); --Returns 1.  
SET DATEFORMAT ymd;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET LANGUAGE English;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET LANGUAGE Hungarian;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET LANGUAGE Swedish;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET LANGUAGE Italian;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
/* Return to these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-isdate-to-test-for-a-valid-datetime-expression"></a>C. Utilisation d'ISDATE pour tester une expression datetime valide.  
 L’exemple suivant vous montre comment utiliser `ISDATE` pour tester si une chaîne de caractères est valide **datetime**.  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    SELECT 'VALID';  
ELSE  
    SELECT 'INVALID';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


