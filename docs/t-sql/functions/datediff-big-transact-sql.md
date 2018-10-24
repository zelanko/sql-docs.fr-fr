---
title: DATEDIFF_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4516965f66256e21e5e68310f7668770e17cabb9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644847"
---
# <a name="datediffbig-transact-sql"></a>DATEDIFF_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Cette fonction retourne le nombre (valeur entière très grande signée) de limites *datepart* spécifiées, traversées entre les valeurs *startdate* et *enddate* spécifiées.
  
Pour obtenir une vue d’ensemble de tous les types de données et fonctions de date et d’heure [!INCLUDE[tsql](../../includes/tsql-md.md)], consultez [Types de données et fonctions de date et d’heure &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
  
DATEDIFF_BIG ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Arguments  
*datepart*  
Partie de *startdate* et *enddate* qui spécifie le type de limite traversée. `DATEDIFF_BIG` n’accepte pas d’équivalents de variables définis par l’utilisateur. Ce tableau répertorie tous les arguments *datepart* valides.

> [!NOTE]
> `DATEDIFF_BIG` n’accepte pas d’équivalents de variables définis par l’utilisateur pour les arguments *datepart*.
  
|*datepart*|Abréviations|  
|---|---|
|**year**|**yy, yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy, y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**hh**|  
|**minute**|**mi, n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
Expression qui peut être résolue en valeur, parmi les suivantes :

+ **date**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**

Pour *date*, `DATEDIFF_BIG` accepte une expression de colonne, une expression, un littéral de chaîne ou une variable définie par l’utilisateur. Une valeur de littéral de chaîne doit être résolue en **datetime**. Pour éviter toute ambiguïté, utilisez des années à quatre chiffres. `DATEDIFF_BIG` soustrait *startdate* de *enddate*. Pour éviter toute ambiguïté, représentez les années à l'aide de quatre chiffres. Pour obtenir des informations sur les années à deux chiffres, consultez [Configurer l’option de configuration du serveur two digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*enddate*  
Consultez *startdate*.
  
## <a name="return-type"></a>Type de retour  

**bigint** signé  
  
## <a name="return-value"></a>Valeur retournée  
Retourne le nombre (valeur entière très grande signée) des limites datepart spécifiées, traversées entre les valeurs startdate et enddate spécifiées.
-   Chaque *datepart* spécifique et les abréviations pour ce *datepart* retournent la même valeur.  
  
Si une valeur de retour est hors limites pour **bigint** (-9 223 372 036 854 775 808 à +9 223 372 036 854 775 807), `DATEDIFF_BIG` retourne une erreur. Pour **millisecond**, la différence maximale entre *enddate* et *startdate* est de 24 jours, 20 heures, 31 minutes et 23,647 secondes. Pour **second**, la différence maximale est de 68 ans.
  
Si *startdate* et *enddate* se voient tous les deux assigner uniquement une valeur d’heure et que *datepart* n’est pas un *datepart* d’heure, `DATEDIFF_BIG` retourne 0.
  
`DATEDIFF_BIG` n’utilise pas un composant de décalage de fuseau horaire de *startdate* ou *enddate* pour calculer la valeur de retour.
  
Quand vous utilisez une valeur **smalldatetime** pour *startdate* ou *enddate*, `DATEDIFF_BIG` définit toujours les secondes et millisecondes avec la valeur 0 dans la valeur de retour dans la mesure où [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) n’offre qu’une précision à la minute.
  
Si seule une valeur d’heure est assignée à une variable d’un type de données date, `DATEDIFF_BIG` affecte à la partie date manquante la valeur par défaut : 1900-01-01. Si seule une valeur de date est assignée à une variable d’un type de données date ou heure, `DATEDIFF_BIG` affecte à la partie heure manquante la valeur par défaut : 00:00:00. Si *startdate* ou *enddate* a uniquement une partie heure et que l’autre a uniquement une partie date, `DATEDIFF_BIG` affecte aux parties heure et date manquantes les valeurs par défaut.
  
Si *startdate* et *enddate* ont des types de données date différents et que l’un a plus de parties heure ou une meilleure précision en fractions de seconde que l’autre, `DATEDIFF_BIG` affecte aux parties manquantes de l’autre la valeur 0.
  
## <a name="datepart-boundaries"></a>Limites de datepart
Les instructions suivantes ont les mêmes valeurs *startdate* et *enddate*. Ces dates sont adjacentes et ont une différence horaire de 0,0000001 seconde. La différence entre les *startdate* et *endate* dans chaque instruction traverse une limite d’heure ou de calendrier de son *datepart*. Chaque instruction retourne 1. Si *startdate* et *enddate* ont des valeurs d’année différentes, mais les mêmes valeurs de semaine de calendrier, `DATEDIFF_BIG` retourne 0 pour *datepart* **week**.

```sql
SELECT DATEDIFF_BIG(year,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(quarter,     '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(month,       '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(dayofyear,   '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(day,         '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(week,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(hour,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(minute,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(second,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF_BIG(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Notes   
Utilisez `DATEDIFF_BIG` dans les clauses SELECT, <list>WHERE, HAVING, GROUP BY et ORDER BY.
  
`DATEDIFF_BIG` caste implicitement les littéraux de chaîne en type **datetime2**. Cela signifie que `DATEDIFF_BIG` ne prend pas en charge le format YDM quand la date est passée comme chaîne. Vous devez caster explicitement la chaîne en type **datetime** ou **smalldatetime** pour utiliser le format AJM.
  
La spécification de SET DATEFIRST n’a aucun effet sur `DATEDIFF_BIG`. `DATEDIFF_BIG` utilise toujours Dimanche comme premier jour de la semaine pour que la fonction soit déterministe.
  
## <a name="examples"></a>Exemples 
  
### <a name="specifying-columns-for-startdate-and-enddate"></a>Spécification de colonnes pour les dates de début et de fin  
Cet exemple utilise différents types d’expressions comme arguments pour les paramètres *startdate* et *enddate*. Il calcule le nombre de limites de jour qui sont traversées entre les dates de deux colonnes d’une table.
  
```sql
CREATE TABLE dbo.Duration  
    (startDate datetime2, endDate datetime2);  
    
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09', '2007-05-07 12:10:09');  
    
SELECT DATEDIFF_BIG(day, startDate, endDate) AS 'Duration'  
    FROM dbo.Duration;  
-- Returns: 1  
```  

Pour obtenir des exemples plus étroitement liés, consultez [DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md).
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[DATEDIFF &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-transact-sql.md)
  
  
