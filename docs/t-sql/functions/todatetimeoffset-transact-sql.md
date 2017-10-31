---
title: TODATETIMEOFFSET (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TO_DATETIMEOFFSET_TSQL
- SWITCH_TZ_TSQL
- SWITCH_TZ
- TO_DATETIMEOFFSET
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], TODATETIMEOFFSET
- TODATETIMEOFFSET function
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: b5fafc08-efd4-4a3b-a0b3-068981a0a685
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 6c0ff45ae5842950d9f15d7b131ad107fba351b5
ms.contentlocale: fr-fr
ms.lasthandoff: 10/24/2017

---
# <a name="todatetimeoffset-transact-sql"></a>TODATETIMEOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne un **datetimeoffset** valeur convertie à partir un **datetime2** expression.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TODATETIMEOFFSET ( expression , time_zone )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) qui se résout en un [datetime2](../../t-sql/data-types/datetime2-transact-sql.md) valeur.  
  
> [!NOTE]  
>  L’expression ne peut pas être de type **texte**, **ntext**, ou **image** , car ces types ne peut pas être implicitement convertis en **varchar** ou **nvarchar**.  
  
 *time_zone*  
 Expression qui représente le décalage de fuseau horaire en minutes (pour un entier), par exemple -120, les heures et les minutes (pour une chaîne), par exemple « +13.00 ». La plage va de +14 à -14 (en heures). L'expression est interprétée en heure locale pour le time_zone spécifié.  
  
> [!NOTE]  
>  Si l'expression est une chaîne de caractères, elle doit être au format {+|-}TZH:THM.  
  
## <a name="return-type"></a>Type de retour  
 **DateTimeOffset**. La précision fractionnaire est identique à la *datetime* argument.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-the-time-zone-offset-of-the-current-date-and-time"></a>A. Modification du décalage de fuseau horaire de la date et de l'heure actuelles  
 L'exemple suivant modifie le décalage de fuseau horaire de la date et de l'heure actuelles au fuseau horaire `-07:00`.  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="b-changing-the-time-zone-offset-in-minutes"></a>B. Modification du décalage de fuseau horaire en minutes  
 L'exemple suivant modifie le fuseau horaire actuel à `-120` minutes.  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="c-adding-a-13-hour-time-zone-offset"></a>C. Ajout d'un décalage de fuseau horaire de 13 heures  
 L'exemple suivant ajoute un décalage de fuseau horaire de 13 heures à une date et une heure.  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Données de date et heure les fonctions et Types de &#40; Transact-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [FUSEAU horaire &AMP;#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  


