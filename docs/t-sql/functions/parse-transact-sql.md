---
title: PARSE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSE
- PARSE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PARSE function
ms.assetid: 6a2dbf10-f692-471b-9458-24d246963049
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b332b92c77340c9cc7f6276d28286e048b2b0f2b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="parse-transact-sql"></a>PARSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne le résultat d'une expression, traduit en type de données demandé dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *valeur_de_la_chaîne*  
 **nvarchar**valeur (4000) représentant la valeur mise en forme à analyser dans le type de données spécifié.  
  
 *valeur_de_la_chaîne* doit être une représentation valide du type de données demandé ou PARSE génère une erreur.  
  
 *data_type*  
 Valeur littérale représentant le type de données demandé pour le résultat.  
  
 *culture*  
 Chaîne facultative qui identifie la culture dans laquelle *valeur_de_la_chaîne* est mise en forme.  
  
 Si le *culture* argument n’est pas fourni, puis la langue de la session active est utilisée. Cette langue est défini implicitement, ou explicitement à l'aide de l'instruction SET LANGAGE. *culture* accepte n’importe quelle culture prise en charge par le .NET Framework ; il n’est pas limité aux langues explicitement prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le *culture* argument n’est pas valide, PARSE génère une erreur.  
  
## <a name="return-types"></a>Types de retour  
 Retourne le résultat de l'expression, traduit en type de données demandé.  
  
## <a name="remarks"></a>Notes  
 Les valeurs NULL passées comme arguments à PARSE sont traitées de deux façons :  
  
1.  Si une constante NULL est passée, une erreur est générée. Une valeur NULL ne peut pas être analysée en un type de données différent d'une manière compatible avec la culture.  
  
2.  Si un paramètre avec une valeur NULL est passé au moment de l'exécution, la valeur NULL est retournée, afin d'éviter l'annulation du traitement entier.  
  
 Utilisez PARSE uniquement pour effectuer une conversion d'une chaîne en un type date/heure ou numérique. Pour les conversions de type général, continuez à utiliser CAST ou CONVERT. N'oubliez pas qu'il existe une certaine surcharge des performances lors de l'analyse de la valeur de chaîne.  
  
 L’analyse s’appuie sur la présence de la Common Language Runtime (CLR) .NET Framework.  
  
 Cette fonction ne peut pas être exécutée à distance car elle dépend de la présence du CLR. L'exécution à distance d'une fonction qui nécessite le CLR provoquerait une erreur sur le serveur distant.  
  
 **Plus d’informations sur le paramètre data_type**  
  
 Les valeurs pour le *data_type* paramètre sont limitées aux types répertoriés dans le tableau ci-dessous, ainsi que les styles. Les informations sur le style sont fournies pour aider à déterminer les types de modèles autorisés. Pour plus d’informations sur les styles, consultez la documentation de .NET Framework pour le **System.Globalization.NumberStyles** et **DateTimeStyles** énumérations.  
  
|Catégorie|Type|Type .NET Framework|Styles utilisés|  
|--------------|----------|-------------------------|-----------------|  
|Numérique|bigint|Int64|NumberStyles.Number|  
|Numérique|int|Int32|NumberStyles.Number|  
|Numérique|smallint|Int16|NumberStyles.Number|  
|Numérique|tinyint|Byte|NumberStyles.Number|  
|Numérique|decimal|Décimal|NumberStyles.Number|  
|Numérique|numeric|Décimal|NumberStyles.Number|  
|Numérique|float|Double|NumberStyles.Float|  
|Numérique|real|Unique|NumberStyles.Float|  
|Numérique|smallmoney|Décimal|NumberStyles.Currency|  
|Numérique|money|Décimal|NumberStyles.Currency|  
|Date et heure|date|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Date et heure|time|TimeSpan|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Date et heure|datetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Date et heure|smalldatetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Date et heure|datetime2|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Date et heure|datetimeoffset|DateTimeOffset|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
  
 **Plus d’informations sur le paramètre de culture**  
  
 Le tableau suivant montre les mappages des langues de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux cultures .NET framework.  
  
|Nom complet|Alias|LCID|Culture spécifique|  
|---------------|-----------|----------|----------------------|  
|us_english|Anglais|1033|fr-FR|  
|Deutsch|Allemand|1031|de-DE|  
|Français|Français|1036|fr-FR|  
|日本語|Japonais|1041|ja-JP|  
|Dansk|Danois|1030|da-DK|  
|Español|Espagnol|3082|es-ES|  
|Italiano|Italien|1040|it-IT|  
|Nederlands|Néerlandais|1043|nl-NL|  
|Norsk|Norvégien|2068|nn-NO|  
|Português|Portugais|2070|pt-PT|  
|Suomi|Finlandais|1035|fi|  
|Svenska|Suédois|1053|sv-SE|  
|čeština|Tchèque|1029|Cs-CZ|  
|magyar|Hongrois|1038|Hu-HU|  
|polski|Polonais|1045|Pl-PL|  
|română|Roumain|1048|Ro-RO|  
|hrvatski|Croate|1050|hr-HR|  
|slovenčina|Slovaque|1051|Sk-SK|  
|slovenski|Slovène|1060|Sl-SI|  
|ΕΛΛΗΝΙΚΆ|Grec|1032|El-GR|  
|български|Bulgare|1026|bg-BG|  
|РУССКИЙ|Russe|1049|Ru-RU|  
|Türkçe|Turc|1055|Tr-TR|  
|British|British English|2057|en-GB|  
|eesti|Estonien|1061|Et-EE|  
|latviešu|Letton|1062|lv-LV|  
|lietuvių|Lituanien|1063|lt-LT|  
|Português (Brasil)|Brésilien|1046|pt-BR|  
|繁體中文|Chinois traditionnel|1028|zh-TW|  
|한국어|Coréen|1042|Ko-KR|  
|简体中文|Chinois simplifié|2052|zh-CN|  
|Arabe|Arabe|1025|ar-SA|  
|ไทย|Thaïlandais|1054|Th-TH|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-parse-into-datetime2"></a>A. PARSE en datetime2  
  
```  
SELECT PARSE('Monday, 13 December 2010' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
2010-12-13 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-parse-with-currency-symbol"></a>B. PARSE avec symbole monétaire  
  
```  
SELECT PARSE('€345,98' AS money USING 'de-DE') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
345.98  
  
(1 row(s) affected)  
```  
  
### <a name="c-parse-with-implicit-setting-of-language"></a>C. PARSE avec définition implicite de la langue  
  
```  
-- The English language is mapped to en-US specific culture  
SET LANGUAGE 'English';  
SELECT PARSE('12/16/2010' AS datetime2) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
2010-12-16 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
  

