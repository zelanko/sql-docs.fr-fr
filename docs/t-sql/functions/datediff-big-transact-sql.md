---
title: DATEDIFF_BIG (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
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
- DATEDIFF_BIG
- DATEDIFF_BIG_TSQL
helpviewer_keywords:
- DATEDIFF_BIG function [SQL Server]
- dates [SQL Server]. functions
- date and time [SQL Server], DATEDIFF_BIG
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 19ac1693-3cfa-400d-bf83-20a9cb46599a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6c8228f0db3e37fe3bf6425d60fd4f9067e92220
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Retourne le nombre (entier long signé) spécifié *datepart* limites comprises entre spécifié *startdate* et *enddate*.
  
Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Arguments  
*partie de date*  
Est la partie de *startdate* et *enddate* qui spécifie le type de limite traversée. Le tableau suivant répertorie toutes valides *datepart* arguments. Les équivalents de variables définis par l'utilisateur ne sont pas valides.
  
|*partie de date*|Abréviations|  
|---|---|
|**année**|**yy, yyyy**|  
|**trimestre**|**qq, q**|  
|**mois**|**mm, m**|  
|**DAYOFYEAR**|**dy, y**|  
|**jour**|**DD, d**|  
|**semaine**|**wk, ww**|  
|**heure**|**hh**|  
|**minute**|**héritage multiple, n**|  
|**seconde**|**ss, s**|  
|**milliseconde**|**MS**|  
|**microsecondes**|**MCS**|  
|**nanosecondes**|**NS**|  
  
*startdate*  
Est une expression qui peut être résolue en un **temps**, **date**, **smalldatetime**, **datetime**, **datetime2**, ou **datetimeoffset** valeur. *date* peut être une expression, l’expression de colonne, variable définie par l’utilisateur ou de chaîne littérale. *StartDate* est soustraite de *enddate*.  
Pour éviter toute ambiguïté, représentez les années à l'aide de quatre chiffres. Pour plus d’informations sur les années de deux chiffres, consultez [configurer l’année à deux chiffres cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*date de fin*  
Consultez *startdate*.
  
## <a name="return-type"></a>Type de retour  
 Signé   
        **bigint**  
  
## <a name="return-value"></a>Valeur retournée  
Count retourne (signé bigint) de limites datepart spécifiées dépassées entre les dates de début et de fin.
-   Chaque *datepart* et ses abréviations retournent la même valeur.  
  
Si la valeur de retour est hors limites pour **bigint** (-9,223,372,036,854,775,808 à 9,223,372,036,854,775,807), une erreur est retournée. Pour **milliseconde**, la différence maximale entre *startdate* et *enddate* est de 24 jours, 20 heures, 31 minutes et 23,647 secondes. Pour **deuxième**, la différence maximale est de 68 ans.
  
Si *startdate* et *enddate* assignées à la fois une valeur d’heure et la *datepart* n’est pas une heure *datepart*, 0 est retourné.
  
Un fuseau horaire de composant de décalage *startdate* ou *endate* n’est pas utilisé dans le calcul de la valeur de retour.
  
Étant donné que [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) est exacte uniquement à la minute, lorsqu’un **smalldatetime** valeur est utilisée pour *startdate* ou *enddate*, secondes et les millisecondes sont toujours définies sur 0 dans la valeur de retour.
  
Si une valeur d'heure uniquement est assignée à une variable d'un type de données date, la valeur de la partie date manquante est égale à la valeur par défaut : 1900-01-01. Si une valeur de date uniquement est assignée à une variable d'un type de données date ou heure, la valeur de la partie heure manquante est égale à la valeur par défaut : 00-00-00. Si le paramètre *startdate* ou *enddate* avoir uniquement une partie de l’heure et l’autre uniquement une partie de date, heure manquante et parties de date sont définis pour les valeurs par défaut.
  
Si *startdate* et *enddate* sont des types de données date différents et l’autre a plus de parties heure ou de précision en fractions de seconde à l’autre, les parties manquantes de l’autre sont définies sur 0.
  
## <a name="datepart-boundaries"></a>limites de DATEPART
Les instructions suivantes ont la même *startdate* et le même *endate*. Ces dates sont adjacentes et ont une différence horaire de .0000001 seconde. La différence entre la *startdate* et *endate* dans chaque instruction traverse un calendrier ou limite d’heure de son *datepart*. Chaque instruction retourne 1. Si des années différentes sont utilisées pour cet exemple et si les deux *startdate* et *endate* se trouvent dans la même semaine de calendrier, la valeur de retour pour **semaine** serait 0.

```sql
SELECT DATEDIFF_BIG(year, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Notes  
DATEDIFF_BIG peut être utilisé dans la liste de sélection, clauses WHERE, HAVING, GROUP BY et ORDER BY.
  
DATEDIFF_BIG convertit implicitement les littéraux de chaîne comme un **datetime2** type. Cela signifie que DATEDIFF_BIG ne prend pas en charge le format YDM lorsque la date est transmise en tant que chaîne. Vous devez convertir explicitement la chaîne à un **datetime** ou **smalldatetime** type à utiliser le format YDM.
  
La spécification SET DATEFIRST n’a aucun effet sur DATEDIFF_BIG. DATEDIFF_BIG utilise toujours dimanche comme premier jour de la semaine pour vous assurer de que la fonction est déterministe.
  
## <a name="examples"></a>Exemples  
Les exemples suivants utilisent différents types d’expressions comme arguments pour le *startdate* et *enddate* paramètres.
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>Spécification de colonnes pour les dates de début et de fin  
L'exemple suivant calcule le nombre de limites de jour qui sont traversées entre des dates de deux colonnes dans une table.
  
```sql
CREATE TABLE dbo.Duration  
    (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT DATEDIFF_BIG(day,startDate,endDate) AS 'Duration'  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
Pour de nombreux exemples supplémentaires, consultez les exemples étroitement liés dans [DATEDIFF &#40; Transact-SQL &#41; ](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF &#40; Transact-SQL &#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  
