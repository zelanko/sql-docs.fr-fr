---
title: DATENAME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATENAME_TSQL
- DATENAME
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATENAME function [SQL Server
- functions [SQL Server], time
- functions [SQL Server], date and time
- dateparts [SQL Server], datename
- date and time [SQL Server], DATENAME
- comparing dates times [SQL Server]
- dates [SQL Server], dateparts
ms.assetid: 11855b56-c554-495d-aad4-ba446990153b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 22dc10851e3185512527f82f593fdc2cdb2b765f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datename-transact-sql"></a>DATENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne une chaîne de caractères qui représente l’élément *datepart* spécifié *date*
  
Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATENAME ( datepart , date )  
```  
  
## <a name="arguments"></a>Arguments  
*partie de date*  
Est la partie de la *date* à retourner. Le tableau suivant répertorie toutes valides *datepart* arguments. Les équivalents de variables définis par l'utilisateur ne sont pas valides.
  
|*partie de date*|Abréviations|  
|---|---|
|**année**|**yy, yyyy**|  
|**trimestre**|**qq, q**|  
|**mois**|**mm, m**|  
|**DAYOFYEAR**|**dy, y**|  
|**jour**|**DD, d**|  
|**semaine**|**wk, ww**|  
|**jour de la semaine**|**entrepôt de données, w**|  
|**heure**|**hh**|  
|**minute**|**héritage multiple, n**|  
|**seconde**|**ss, s**|  
|**milliseconde**|**MS**|  
|**microsecondes**|**MCS**|  
|**nanosecondes**|**NS**|  
|**Date TZoffset**|**TZ**|  
|**ISO_WEEK**|**ISOWK, ISOWW**|  
  
*date*  
Est une expression qui peut être résolue en un **temps**, **date**, **smalldatetime**, **datetime**, **datetime2**, ou **datetimeoffset** valeur. *date* peut être une expression, une expression de colonne, une variable définie par l’utilisateur ou une chaîne littérale.  
Pour éviter toute ambiguïté, représentez les années à l'aide de quatre chiffres. Pour plus d’informations sur les années à deux chiffres, consultez [configurer l’année à deux chiffres cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-type"></a>Type de retour  
**nvarchar**
  
## <a name="return-value"></a>Valeur retournée  
  
-   Chaque *datepart* et ses abréviations retournent la même valeur.  
  
La valeur de retour dépend de l’environnement de langage défini à l’aide de [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) et par le [configurer l’Option de Configuration de serveur de la langue par défaut](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) de la connexion. La valeur de retour dépend de [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) si *date* est une chaîne littérale de certains formats. SET DATEFORMAT n'affecte pas la valeur de retour lorsque la date est une expression de colonne d'un type de données de date ou d'heure.
  
Lorsque le *date* le paramètre a un **date** argument de type de données, la valeur de retour dépend du paramètre spécifié à l’aide de [SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md).
  
## <a name="tzoffset-datepart-argument"></a>Argument de la partie de date TZoffset  
Si *datepart* argument est **date TZoffset** (**tz**) et le *date* argument ne possède aucun décalage de fuseau horaire, 0 est retourné.
  
## <a name="smalldatetime-date-argument"></a>Argument date smalldatetime  
Lorsque *date* est [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), secondes sont retournées sous la forme 00.
  
## <a name="default-returned-for-a-datepart-that-is-not-in-the-date-argument"></a>Valeur par défaut retournée pour une partie de date qui ne figure pas dans l'argument date  
Si le type de données de la *date* argument n’est pas spécifié *datepart*, la valeur par défaut pour ce *datepart* s’affichera uniquement lorsqu’un littéral est spécifié pour *date*.
  
Par exemple, la valeur par défaut année-mois-jour pour toute **date** type de données est 1900-01-01. L’instruction suivante a des arguments de partie de date pour *datepart*, un argument de temps pour *date*et retourne `1900, January, 1, 1, Monday`.
  
```sql
SELECT DATENAME(year, '12:10:30.123')  
    ,DATENAME(month, '12:10:30.123')  
    ,DATENAME(day, '12:10:30.123')  
    ,DATENAME(dayofyear, '12:10:30.123')  
    ,DATENAME(weekday, '12:10:30.123');  
```  
  
Si *date* est spécifiée comme une variable ou colonne de table et les type de données pour que variable ou une colonne n’a pas spécifié *datepart*, erreur 9810 est retournée. Le code suivant exemple échoue, car la partie année de la date n’est pas valide pour le **temps** type de données qui est déclaré pour la variable  *@t* .
  
```sql
DECLARE @t time = '12:10:30.123';   
SELECT DATENAME(year, @t);  
```  
  
## <a name="remarks"></a>Notes  
DATENAME peut être utilisé dans la liste de sélection, WHERE, HAVING, GROUP BY et les clauses ORDER BY.
  
Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], DATENAME convertit implicitement les littéraux de chaîne comme un **datetime2** type. Cela signifie que DATENAME ne prend pas en charge le format YDM lorsque la date est transmise en tant que chaîne. Vous devez convertir explicitement la chaîne à un **datetime** ou **smalldatetime** type à utiliser le format YDM.
  
## <a name="examples"></a>Exemples  
L'exemple suivant retourne les parties de la date spécifiée.
  
`SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');`
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*partie de date*|Valeur retournée|  
|---|---|
|**année, jj, AA**|2007|  
|**trimestre, qq, q**|4|  
|**mois, mm, m**|Octobre|  
|**DAYOFYEAR, dy, y**|303|  
|**Day, jj, d**|30|  
|**semaine, wk, ww**|44|  
|**jour ouvrable, entrepôt de données**|Mardi|  
|**heure, hh**|12|  
|**minute, n**|15|  
|**seconde, ss, s**|32|  
|**milliseconde, ms**|123|  
|**microsecondes, mcs**|123456|  
|**nanosecondes, ns**|123456700|  
|**Date TZoffset, tz**|310|  
|**ISO_WEEK, ISOWK, ISOWW**|44|  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

L'exemple suivant retourne les parties de la date spécifiée.
  
```sql
SELECT DATENAME(datepart,'2007-10-30 12:15:32.1234567 +05:10');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|*partie de date*|Valeur retournée|  
|---|---|
|**année, jj, AA**|2007|  
|**trimestre, qq, q**|4|  
|**mois, mm, m**|Octobre|  
|**DAYOFYEAR, dy, y**|303|  
|**Day, jj, d**|30|  
|**semaine, wk, ww**|44|  
|**jour ouvrable, entrepôt de données**|Mardi|  
|**heure, hh**|12|  
|**minute, n**|15|  
|**seconde, ss, s**|32|  
|**milliseconde, ms**|123|  
|**microsecondes, mcs**|123456|  
|**nanosecondes, ns**|123456700|  
|**Date TZoffset, tz**|310|  
|**ISO_WEEK, ISOWK, ISOWW**|44|  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

