---
title: FORMAT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FORMAT_TSQL
- FORMAT
dev_langs: TSQL
helpviewer_keywords: FORMAT function
ms.assetid: dad6f24c-b8d9-4dbe-a561-9b167b8f20c8
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 43d702accc0611030c1c7ad0eda74d456711b694
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="format-transact-sql"></a>FORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne une valeur mise en forme avec la culture facultative et le format spécifiés dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Utilisez la fonction FORMAT pour la mise en forme comme chaînes de valeurs de date/heure et de valeurs numériques compatibles avec les paramètres régionaux. Pour les conversions de type de données général, continuez à utiliser CAST ou CONVERT.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FORMAT ( value, format [, culture ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *valeur*  
 Expression d'un type de données pris en charge à mettre en forme. Pour obtenir la liste des types valides, consultez la table dans la section Notes ci-dessous.  
  
 *format*  
 **nvarchar** modèle de format.  
  
 Le *format* argument doit contenir une chaîne de format .NET Framework valide, une chaîne de format standard (par exemple, « C » ou « D »), soit comme un modèle de caractères personnalisés pour les dates et les valeurs numériques (par exemple, « MMMM jj, AAAA (jjjj) »). La mise en forme composite n'est pas prise en charge. Pour obtenir une explication complète de ces modèles de mise en forme, consultez la documentation de .NET Framework sur la chaîne mise en forme en général, date personnalisée et formats d’heure et les formats numériques personnalisés. Un bon point de départ est la rubrique «[les Types de mise en forme](http://go.microsoft.com/fwlink/?LinkId=211776). »  
  
 *culture*  
 Facultatif **nvarchar** argument spécifiant une culture.  
  
 Si le *culture* argument n’est pas fourni, la langue de la session active est utilisée. Cette langue est défini implicitement, ou explicitement à l'aide de l'instruction SET LANGAGE. *culture* accepte n’importe quelle culture prise en charge par le .NET Framework en tant qu’argument ; il n’est pas limité aux langues explicitement prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le *culture* argument n’est pas valide, FORMAT génère une erreur.  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar** ou null  
  
 La longueur de la valeur de retour est déterminée par le *format*.  
  
## <a name="remarks"></a>Notes  
 FORMAT retourne NULL pour les erreurs autres qu’un *culture* qui n’est pas *valide*. Par exemple, la valeur NULL est retournée si la valeur spécifiée dans *format* n’est pas valide.  
 
 La fonction FORMAT est non déterministe.   
  
 FORMAT repose sur la présence de la Common Language Runtime (CLR) .NET Framework.  
  
 Cette fonction ne peut pas être exécutée à distance, car il dépend de la présence du CLR. La communication à distance une fonction qui nécessite le CLR, peut provoquer une erreur sur le serveur distant.  
  
 FORMAT repose sur le CLR mise en forme de règles, qui exigent que les deux-points et points doivent être échappés. Par conséquent, lorsque le format de paramètre de chaîne (deuxième) contient un signe deux-points ou période, le signe deux-points ou la période doivent être précédés d’une barre oblique inverse lorsqu’une valeur d’entrée (premier paramètre) est de le **temps** type de données. Consultez [FORMATD.deavec les types de données heure](#ExampleD).  
  
 Le tableau suivant répertorie les types de données acceptables pour le *valeur* argument ainsi que leurs types équivalents de mappage .NET Framework.  
  
|Catégorie|Type|Type .NET|  
|--------------|----------|---------------|  
|Numérique|bigint|Int64|  
|Numérique|int|Int32|  
|Numérique|smallint|Int16|  
|Numérique|tinyint|Byte|  
|Numérique|decimal|SqlDecimal|  
|Numérique|numeric|SqlDecimal|  
|Numérique|float|Double|  
|Numérique|real|Single|  
|Numérique|smallmoney|Decimal|  
|Numérique|money|Décimal|  
|Date et heure|date|DateTime|  
|Date et heure|time|TimeSpan|  
|Date et heure|datetime|DateTime|  
|Date et heure|smalldatetime|DateTime|  
|Date et heure|datetime2|DateTime|  
|Date et heure|datetimeoffset|DateTimeOffset|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-format-example"></a>A. Exemple FORMAT simple  
 L'exemple suivant retourne une date simple mise en forme pour différentes cultures.  
  
```sql  
DECLARE @d DATETIME = '10/01/2011';  
SELECT FORMAT ( @d, 'd', 'en-US' ) AS 'US English Result'  
      ,FORMAT ( @d, 'd', 'en-gb' ) AS 'Great Britain English Result'  
      ,FORMAT ( @d, 'd', 'de-de' ) AS 'German Result'  
      ,FORMAT ( @d, 'd', 'zh-cn' ) AS 'Simplified Chinese (PRC) Result';   
  
SELECT FORMAT ( @d, 'D', 'en-US' ) AS 'US English Result'  
      ,FORMAT ( @d, 'D', 'en-gb' ) AS 'Great Britain English Result'  
      ,FORMAT ( @d, 'D', 'de-de' ) AS 'German Result'  
      ,FORMAT ( @d, 'D', 'zh-cn' ) AS 'Chinese (Simplified PRC) Result';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
US English Result Great Britain English Result  German Result Simplified Chinese (PRC) Result  
----------------  ----------------------------- ------------- -------------------------------------  
10/1/2011         01/10/2011                    01.10.2011    2011/10/1  
  
(1 row(s) affected)  
  
US English Result            Great Britain English Result  German Result                    Chinese (Simplified PRC) Result  
---------------------------- ----------------------------- -----------------------------  ---------------------------------------  
Saturday, October 01, 2011   01 October 2011               Samstag, 1. Oktober 2011        2011年10月1日  
  
(1 row(s) affected)  
```  
  
### <a name="b-format-with-custom-formatting-strings"></a>B. FORMAT avec chaînes de format personnalisées  
 L'exemple suivant montre la mise en forme des valeurs numériques en spécifiant un format personnalisé. L’exemple suppose que la date actuelle est le 27 septembre 2012. Pour plus d’informations sur ces et d’autres formats personnalisés, consultez [les chaînes de Format numériques personnalisées](http://msdn.microsoft.com/library/0c899ak8.aspx).  
  
```sql  
DECLARE @d DATETIME = GETDATE();  
SELECT FORMAT( @d, 'dd/MM/yyyy', 'en-US' ) AS 'DateTime Result'  
       ,FORMAT(123456789,'###-##-####') AS 'Custom Number Result';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DateTime Result  Custom Number Result  
--------------   --------------------  
27/09/2012       123-45-6789  
  
(1 row(s) affected)  
```  
  
### <a name="c-format-with-numeric-types"></a>C. FORMAT avec types numériques  
 L’exemple suivant retourne 5 lignes de la **Sales.CurrencyRate** de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données. La colonne **EndOfDateRate** est stocké en tant que type **money** dans la table. Dans cet exemple, la colonne est retournée dépourvue de mise en forme, puis mise en forme en spécifiant les types de formats Number, General et Currency .NET. Pour plus d’informations sur celles-ci et d’autres formats numériques, consultez [des chaînes de Format numériques Standard](http://msdn.microsoft.com/library/dwhawy9k.aspx).  
  
```sql  
SELECT TOP(5)CurrencyRateID, EndOfDayRate  
            ,FORMAT(EndOfDayRate, 'N', 'en-us') AS 'Number Format'  
            ,FORMAT(EndOfDayRate, 'G', 'en-us') AS 'General Format'  
            ,FORMAT(EndOfDayRate, 'C', 'en-us') AS 'Currency Format'  
FROM Sales.CurrencyRate  
ORDER BY CurrencyRateID;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CurrencyRateID EndOfDayRate  Numeric Format  General Format  Currency Format  
-------------- ------------  --------------  --------------  ---------------  
1              1.0002        1.00            1.0002          $1.00  
2              1.55          1.55            1.5500          $1.55  
3              1.9419        1.94            1.9419          $1.94  
4              1.4683        1.47            1.4683          $1.47  
5              8.2784        8.28            8.2784          $8.28  
  
(5 row(s) affected)  
  
```  
  
 Cet exemple spécifie la culture allemande (de-de).  
  
```sql  
SELECT TOP(5)CurrencyRateID, EndOfDayRate  
      ,FORMAT(EndOfDayRate, 'N', 'de-de') AS 'Numeric Format'  
      ,FORMAT(EndOfDayRate, 'G', 'de-de') AS 'General Format'  
      ,FORMAT(EndOfDayRate, 'C', 'de-de') AS 'Currency Format'  
FROM Sales.CurrencyRate  
ORDER BY CurrencyRateID;  
```  
  
```  
CurrencyRateID EndOfDayRate  Numeric Format  General Format  Currency Format  
-------------- ------------  --------------  --------------  ---------------  
1              1.0002        1,00            1,0002          1,00 €  
2              1.55          1,55            1,5500          1,55 €  
3              1.9419        1,94            1,9419          1,94 €  
4              1.4683        1,47            1,4683          1,47 €  
5              8.2784        8,28            8,2784          8,28 €  
  
 (5 row(s) affected)  
```  
  
###  <a name="ExampleD"></a> D. Mettre en forme avec les types de données  
 FORMAT retourne la valeur NULL dans ces cas, car `.` et `:` ne sont pas ignorés.  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh.mm');   --> returns NULL  
SELECT FORMAT(cast('07:35' as time), N'hh:mm');   --> returns NULL  
```  
  
 Format retourne une chaîne mise en forme, car le `.` et `:` sont ignorés.  
  
```sql  
SELECT FORMAT(cast('07:35' as time), N'hh\.mm');  --> returns 07.35  
SELECT FORMAT(cast('07:35' as time), N'hh\:mm');  --> returns 07:35  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
