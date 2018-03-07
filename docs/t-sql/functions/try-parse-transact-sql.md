---
title: TRY_PARSE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- TRY_PARSE_TSQL
- TRY_PARSE
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_PARSE function
ms.assetid: 292bac1d-edd8-468c-8ff1-8c7de625bc55
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0b26f46431909dd4fbfaa820db8c3869333f555d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="tryparse-transact-sql"></a>TRY_PARSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne le résultat d'une expression, traduit en type de données demandé, ou NULL si la conversion échoue dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez TRY_PARSE uniquement pour effectuer une conversion d'une chaîne en un type date/heure ou numérique.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TRY_PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *valeur_de_la_chaîne*  
 **nvarchar (4000)** valeur représentant la valeur mise en forme à analyser dans le type de données spécifié.  
  
 *valeur_de_la_chaîne* doit être une représentation valide du type de données demandé ou TRY_PARSE retourne la valeur null.  
  
 *data_type*  
 Littéral représentant le type de données demandé pour le résultat.  
  
 *culture*  
 Chaîne facultative qui identifie la culture dans laquelle *valeur_de_la_chaîne* est mise en forme.  
  
 Si le *culture* argument n’est pas fourni, la langue de la session active est utilisée. Cette langue est définie implicitement, ou explicitement à l'aide de l'instruction SET LANGAGE. *culture* accepte n’importe quelle culture prise en charge par le .NET Framework ; il n’est pas limité aux langues explicitement prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le *culture* argument n’est pas valide, PARSE génère une erreur.  
  
## <a name="return-types"></a>Types de retour  
 Retourne le résultat de l'expression, traduit en type de données demandé, ou NULL si la conversion échoue.  
  
## <a name="remarks"></a>Notes  
 Utilisez TRY_PARSE uniquement pour effectuer une conversion d'une chaîne en un type date/heure ou numérique. Pour les conversions de type général, continuez à utiliser CAST ou CONVERT. N'oubliez pas qu'il existe une certaine surcharge des performances lors de l'analyse de la valeur de chaîne.  
  
 TRY_PARSE repose sur la présence du CLR (Common Langage Runtime) .NET Framework.  
  
 Cette fonction ne peut pas être exécutée à distance car elle dépend de la présence du CLR. L'exécution à distance d'une fonction qui nécessite le CLR provoquerait une erreur sur le serveur distant.  
  
 **Plus d’informations sur le paramètre data_type**  
  
 Les valeurs pour le *data_type* paramètre sont limitées aux types répertoriés dans le tableau ci-dessous, ainsi que les styles. Les informations sur le style sont fournies pour aider à déterminer les types de modèles autorisés. Pour plus d’informations sur les styles, consultez la documentation de .NET Framework pour le **System.Globalization.NumberStyles** et **DateTimeStyles** énumérations.  
  
|Catégorie|Type|Type .NET|Styles utilisés|  
|--------------|----------|---------------|-----------------|  
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
  
### <a name="a-simple-example-of-tryparse"></a>A. Exemple simple de TRY_PARSE  
  
```  
SELECT TRY_PARSE('Jabberwokkie' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-detecting-nulls-with-tryparse"></a>B. Détection de valeurs NULL avec TRY_PARSE  
  
```  
SELECT  
    CASE WHEN TRY_PARSE('Aragorn' AS decimal USING 'sr-Latn-CS') IS NULL  
        THEN 'True'  
        ELSE 'False'  
END  
AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
True  
  
(1 row(s) affected)  
```  
  
### <a name="c-using-iif-with-tryparse-and-implicit-culture-setting"></a>C. Utilisation de IIF avec TRY_PARSE et paramètre de culture implicite  
  
```  
SET LANGUAGE English;  
SELECT IIF(TRY_PARSE('01/01/2011' AS datetime2) IS NULL, 'True', 'False') AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
False  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [PARSE &#40; Transact-SQL &#41;](../../t-sql/functions/parse-transact-sql.md)   
 [Fonctions de conversion &#40; Transact-SQL &#41;](../../t-sql/functions/conversion-functions-transact-sql.md)   
 [TRY_CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/try-convert-transact-sql.md)   
 [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
