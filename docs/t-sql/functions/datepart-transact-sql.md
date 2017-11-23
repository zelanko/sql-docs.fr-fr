---
title: DATEPART (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
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
- DATEPART_TSQL
- DATEPART
dev_langs: TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], DATEPART
- dateparts [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
- dateparts [SQL Server], datepart
- comparing dates times [SQL Server]
- DATEPART function [SQL Server]
- dates [SQL Server], dateparts
ms.assetid: 15f1a5bc-4c0c-4c48-848d-8ec03473e6c1
caps.latest.revision: "57"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a972e0646d68620b915fe441e35ebfb617d06859
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datepart-transact-sql"></a>DATEPART (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne un entier qui représente l’élément *datepart* spécifié *date*.
  
Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATEPART ( datepart , date )  
```  
  
## <a name="arguments"></a>Arguments  
*partie de date*  
Est la partie de *date* (une valeur de date ou heure) pour lequel un **entier** sera retourné. Le tableau suivant répertorie toutes valides *datepart* arguments. Les équivalents de variables définis par l'utilisateur ne sont pas valides.
  
|*partie de date*|Abréviations|  
|---|---|
|**année**|**aa**, **aaaa**|  
|**trimestre**|**qq**, **q**|  
|**mois**|**mm**, **m**|  
|**DAYOFYEAR**|**dy**, **y**|  
|**jour**|**DD**, **d**|  
|**semaine**|**wk**, **ww**|  
|**jour de la semaine**|**entrepôt de données**|  
|**heure**|**hh**|  
|**minute**|**héritage multiple, n**|  
|**seconde**|**ss**, **s**|  
|**milliseconde**|**MS**|  
|**microsecondes**|**MCS**|  
|**nanosecondes**|**NS**|  
|**Date TZoffset**|**TZ**|  
|**ISO_WEEK**|**isowk**, **isoww**|  
  
*date*  
Est une expression qui peut être résolue en un **temps**, **date**, **smalldatetime**, **datetime**, **datetime2**, ou **datetimeoffset** valeur. *date* peut être une expression, une expression de colonne, une variable définie par l’utilisateur ou une chaîne littérale.  
Pour éviter toute ambiguïté, représentez les années à l'aide de quatre chiffres. Pour plus d’informations sur les années de deux chiffres, consultez [configurer l’année à deux chiffres cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Type de retour  
 **int**  
  
## <a name="return-value"></a>Valeur retournée  
Chaque *datepart* et ses abréviations retournent la même valeur.
  
La valeur de retour dépend de l’environnement de langage défini à l’aide de [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) et par le [configurer l’Option de Configuration de serveur de la langue par défaut](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) de la connexion. Si *date* est une chaîne littérale pour certains formats, la valeur de retour dépend du format spécifié à l’aide de [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md). SET DATEFORMAT n'affecte pas la valeur de retour lorsque la date est une expression de colonne d'un type de données de date ou d'heure.
  
Le tableau suivant répertorie tous les *datepart* arguments avec les valeurs de retour pour l’instruction `SELECT DATEPART(datepart,'2007-10-30 12:15:32.1234567 +05:10')`. Type de données de la *date* argument est **datetimeoffset(7)**. Le **nanosecondes***datepart* retournent la valeur a une échelle de 9 (. 123456700) et les deux dernières positions sont toujours 00.
  
|*partie de date*|Valeur retournée|  
|---|---|
|**année, jj, AA**|2007|  
|**trimestre, qq, q**|4|  
|**mois, mm, m**|10|  
|**DAYOFYEAR, dy, y**|303|  
|**Day, jj, d**|30|  
|**semaine, wk, ww**|45|  
|**jour ouvrable, entrepôt de données**|1|  
|**heure, hh**|12|  
|**minute, n**|15|  
|**seconde, ss, s**|32|  
|**milliseconde, ms**|123|  
|**microsecondes, mcs**|123456|  
|**nanosecondes, ns**|123456700|  
|**Date TZoffset, tz**|310|  
  
## <a name="week-and-weekday-datepart-arguments"></a>Arguments de partie de date semaine et jour de la semaine
Lorsque *datepart* est **semaine** (**wk**, **ww**) ou **semaine** (**dw**), la valeur de retour dépend de la valeur est définie à l’aide de [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
Le 1er janvier d’une année définit le numéro de départ de la **semaine***datepart*, par exemple : DATEPART (**wk**, ' Jan 1, *xxx*x') = 1, où *xxxx* représente une année.
  
Le tableau suivant répertorie la valeur de retour pour **semaine** et **semaine***datepart* pour ' 2007-04-21' pour chaque argument SET DATEFIRST. Le 1er janvier est un lundi dans l'année 2007. Le 21 avril est un samedi dans l'année 2007. SET DATEFIRST 7, Sunday, est la valeur par défaut pour l'anglais des États-Unis Anglais.
  
|SET DATEFIRST<br /><br /> argument|week<br /><br /> retourné|weekday<br /><br /> retourné|  
|---|---|---|
|1|16|6|  
|2|17|5|  
|3|17|4|  
|4|17|3|  
|5|17|2|  
|6|17|1|  
|7|16|7|  
  
## <a name="year-month-and-day-datepart-arguments"></a>Arguments des parties de date année, mois et jour  
Les valeurs qui sont retournées pour DATEPART (**année**, *date*), DATEPART (**mois**, *date*) et DATEPART (**jour**, *date*) sont les mêmes que celles retournées par les fonctions [année](../../t-sql/functions/year-transact-sql.md), [mois](../../t-sql/functions/month-transact-sql.md), et [jour](../../t-sql/functions/day-transact-sql.md), f respectivement.
  
## <a name="isoweek-datepart"></a>Partie de date ISO_WEEK  
ISO 8601 inclut le système semaine-date ISO, un système de numérotation pour les semaines. Chaque semaine est associée à l'année dans laquelle jeudi se produit. Par exemple, la semaine 1 de 2004 (2004W01) a eu lieu du lundi 29 décembre 2003 au dimanche 4 janvier 2004. Le numéro de semaine le plus élevé dans une année peut être 52 ou 53. Ce style de numérotation est utilisé en général dans les pays européens, plus rarement ailleurs.
  
Le système de numérotation des différents pays peut ne pas se conformer à la norme ISO. Il existe au moins six possibilités comme illustré dans le tableau suivant
  
|Premier jour de semaine|La première semaine de l'année contient|Semaines assignées deux fois|Utilisé par/dans|  
|---|---|---|---|
|Dimanche|1er janvier,<br /><br /> Premier samedi,<br /><br /> 1 à 7 jours de l'année|Oui|United States|  
|Lundi|1er janvier,<br /><br /> Premier dimanche,<br /><br /> 1 à 7 jours de l'année|Oui|Majorité de l'Europe et Royaume-Uni|  
|Lundi|4 janvier,<br /><br /> Premier jeudi,<br /><br /> 4 – 7 jours de l’année|Non|ISO 8601, Norvège et Suède|  
|Lundi|7 janvier,<br /><br /> Premier lundi,<br /><br /> 7 jours de l'année|Non||  
|Mercredi|1er janvier,<br /><br /> Premier mardi,<br /><br /> 1 à 7 jours de l'année|Oui||  
|Samedi|1er janvier,<br /><br /> Premier vendredi,<br /><br /> 1 à 7 jours de l'année|Oui||  
  
## <a name="tzoffset"></a>TZoffset  
Le **date TZoffset** (**tz**) est retourné en tant que le nombre de minutes (signé). L'instruction suivante retourne un décalage de fuseau horaire de 310 minutes.
  
```sql
SELECT DATEPART (TZoffset, '2007-05-10  00:00:01.1234567 +05:10');  
```  
La valeur de date TZoffset est restituée comme suit :
- Pour datetimeoffset et datetime2, date TZoffset retourne le décalage horaire en minutes, où le décalage pour datetime2 est toujours 0 minutes.
- Pour les types de données qui peuvent être convertis implicitement datetimeoffset ou datetime2, à l’exception des autres types de données de date/heure, il retourne le décalage horaire en minutes.
- Paramètres de tous les autres types génère une erreur.
  
  
## <a name="smalldatetime-date-argument"></a>Argument date smalldatetime  
Lorsque *date* est [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), secondes sont retournées sous la forme 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-a-date-argument"></a>Valeur par défaut retournée pour une partie de date qui ne figure pas dans un argument date  
Si le type de données de la *date* argument n’est pas spécifié *datepart*, la valeur par défaut pour ce *datepart* s’affichera uniquement lorsqu’un littéral est spécifié pour *date*.
  
Par exemple, la valeur par défaut année-mois-jour pour toute **date** type de données est 1900-01-01. L’instruction suivante a des arguments de partie de date pour *datepart*, un argument de temps pour *date*et retourne `1900, 1, 1, 1, 2`.
  
```sql
SELECT DATEPART(year, '12:10:30.123')  
    ,DATEPART(month, '12:10:30.123')  
    ,DATEPART(day, '12:10:30.123')  
    ,DATEPART(dayofyear, '12:10:30.123')  
    ,DATEPART(weekday, '12:10:30.123');  
```  
  
Si *date* est spécifiée comme une variable ou colonne de table et les type de données pour que variable ou une colonne n’a pas spécifié *datepart*, erreur 9810 est retournée. Le code suivant exemple échoue, car la partie année de la date n’est pas valide pour le **temps** type de données qui est déclaré pour la variable  *@t* .
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATEPART(year, @t);  
```  
  
## <a name="fractional-seconds"></a>Les fractions de secondes
Les fractions de seconde sont retournées comme illustré dans les instructions suivantes :
  
```sql
SELECT DATEPART(millisecond, '00:00:01.1234567'); -- Returns 123  
SELECT DATEPART(microsecond, '00:00:01.1234567'); -- Returns 123456  
SELECT DATEPART(nanosecond,  '00:00:01.1234567'); -- Returns 123456700  
```  
  
## <a name="remarks"></a>Notes  
DATEPART peut être utilisé dans la liste de sélection et les clauses WHERE, HAVING, GROUP BY et ORDER BY.
  
Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], DATEPART convertit implicitement les littéraux de chaîne comme un **datetime2** type. Cela signifie que DATEPART ne prend pas en charge le format YDM lorsque la date est transmise en tant que chaîne. Vous devez convertir explicitement la chaîne à un **datetime** ou **smalldatetime** type à utiliser le format YDM.
  
## <a name="examples"></a>Exemples  
L'exemple suivant retourne l'année de base. L'année de base est utile pour les calculs de date. Dans l'exemple, la date est spécifiée comme un nombre. Notez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprète 0 comme représentant le 1er janvier 1900.
  
```sql
SELECT DATEPART(year, 0), DATEPART(month, 0), DATEPART(day, 0);  
-- Returns: 1900    1    1 */  
```  
  
L’exemple suivant renvoie la partie jour de la date `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (day,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
--------
20
```  
  
L’exemple suivant retourne la partie année de la date `12/20/1974`.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEPART (year,'12/20/1974') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
--------
1974
```  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
