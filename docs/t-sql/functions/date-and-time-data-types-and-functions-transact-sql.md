---
title: "Données de date et heure fonctions (Transact-SQL) et Types | Documents Microsoft"
ms.custom: 
ms.date: 09/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- dates [SQL Server]
- date and time [SQL Server], all data types and functions
- date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: 83e378a2-6e89-4c80-bc4f-644958d9e0a9
caps.latest.revision: "79"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 05ce8f3240590e1be28722ded5a526ad2dd2d6df
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="date-and-time-data-types-and-functions-transact-sql"></a>Types de données et fonctions de date et d'heure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Les sections suivantes dans cette rubrique fournissent une vue d'ensemble de tous les types de données et fonctions de date et d'heure [!INCLUDE[tsql](../../includes/tsql-md.md)].
-   [Date et heure les Types de données](#DateandTimeDataTypes)  
-   [Fonctions de date et heure](#DateandTimeFunctions)  
    -   [Fonction Get Date et heure système des valeurs](#GetSystemDateandTimeValues)  
    -   [Fonctions permettant d’obtenir la Date et l’heure des parties](#GetDateandTimeParts)  
    -   [Fonctions permettant d’obtenir les valeurs de Date et heure à partir de leurs parties](#fromParts)  
    -   [Fonctions permettant d’obtenir la Date et l’heure de différence](#GetDateandTimeDifference)  
    -   [Fonctions qui modifient les Date et les valeurs d’heure](#ModifyDateandTimeValues)  
    -   [Fonctions de définir ou obtenir des fonctions de Format de Session](#SetorGetSessionFormatFunctions)  
    -   [Les fonctions qui valident les Date et les valeurs d’heure](#ValidateDateandTimeValues)  
-   [Date et les rubriques relatives à la fois](#DateandTimeRelatedTopics)  
  
##  <a name="DateandTimeDataTypes"></a>Types de données de date et heure
Le [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure sont répertoriées dans le tableau suivant :
  
|Type de données|Format|Plage|Analyse de précision|Taille de stockage (en octets)|Précision à la fraction de seconde définie par l'utilisateur|Décalage de fuseau horaire|  
|---|---|---|---|---|---|---|
|[time](../../t-sql/data-types/time-transact-sql.md)|hh:mm:ss [.nnnnnnn]|00:00:00.0000000 à 23:59:59.9999999|100 nanosecondes|De 3 à 5|Oui|Non|  
|[date](../../t-sql/data-types/date-transact-sql.md)|AAAA-MM-JJ|0001-01-01 à 9999-12-31|1 jour|3|Non|Non|  
|[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)|AAAA-MM-JJ hh:mm:ss|1900-01-01 à 2079-06-06|1 minute|4|Non|Non|  
|[datetime](../../t-sql/data-types/datetime-transact-sql.md)|AAAA-MM-JJ hh:mm:ss[.nnn]|1753-01-01 à 9999-12-31|0,00333 seconde|8|Non|Non|  
|[datetime2](../../t-sql/data-types/datetime2-transact-sql.md)|AAAA-MM-JJ hh:mm:ss[.nnnnnnn]|0001-01-01 00:00:00.0000000 à 9999-12-31 23:59:59.9999999|100 nanosecondes|6 à 8|Oui|Non|  
|[datetimeoffset](../../t-sql/data-types/datetimeoffset-transact-sql.md)|AAAA-MM-JJ HH : mm : [.nnnnnnn] [+ &#124;-] HH : mm|0001-01-01 00:00:00,0000000 à 9999-12-31 23:59:59,9999999 (au format UTC)|100 nanosecondes|8 à 10|Oui|Oui|  
  
> [!NOTE]  
>  Le [!INCLUDE[tsql](../../includes/tsql-md.md)] [rowversion](../../t-sql/data-types/rowversion-transact-sql.md) type de données n’est pas un type de données date ou heure. **horodatage** est un synonyme déconseillé pour **rowversion**.  
  
##  <a name="DateandTimeFunctions"></a>Fonctions de date et heure  
Les fonctions de date et d'heure [!INCLUDE[tsql](../../includes/tsql-md.md)] sont répertoriées dans les tableaux suivants. Pour plus d’informations sur le déterminisme, consultez [fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
###  <a name="GetSystemDateandTimeValues"></a>Fonctions permettant d’obtenir des valeurs de Date et heure système 
Toutes les valeurs système de date et d'heure sont dérivées du système d'exploitation de l'ordinateur sur lequel l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute.
  
#### <a name="higher-precision-system-date-and-time-functions"></a>Fonctions système de date et d'heure de plus grande précision  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Obtient les valeurs de date et d’heure à l’aide de l’API Windows GetSystemTimeAsFileTime(). La précision dépend des composants matériels de l'ordinateur et de la version de Windows sur laquelle s'exécute l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La précision de cette API est fixée à 100 nanosecondes. La précision peut être déterminée à l’aide de l’API Windows GetSystemTimeAdjustment().
  
|Fonction|Syntaxe|Valeur retournée|Type de données de retour|Propriété de déterminisme|  
|---|---|---|---|---|
|[SYSDATETIME](../../t-sql/functions/sysdatetime-transact-sql.md)|SYSDATETIME ()|Retourne un **datetime2 (7)** valeur qui contient la date et l’heure de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Le décalage de fuseau horaire n'est pas inclus.|**datetime2(7)**|Non déterministe|  
|[SYSDATETIMEOFFSET](../../t-sql/functions/sysdatetimeoffset-transact-sql.md)|SYSDATETIMEOFFSET ()|Retourne un **datetimeoffset(7)** valeur qui contient la date et l’heure de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Le décalage de fuseau horaire est inclus.|**DateTimeOffset(7)**|Non déterministe|  
|[SYSUTCDATETIME](../../t-sql/functions/sysutcdatetime-transact-sql.md)|SYSUTCDATETIME ( )|Retourne un **datetime2 (7)** valeur qui contient la date et l’heure de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. La date et l’heure est retourné en tant que l’heure UTC (Coordinated Universal Time).|**datetime2(7)**|Non déterministe|  
  
#### <a name="lower-precision--system-date-and-time-functions"></a>Fonctions de Date et heure du système de moindre précision
  
|Fonction|Syntaxe|Valeur retournée|Type de données de retour|Propriété de déterminisme|  
|---|---|---|---|---|
|[CURRENT_TIMESTAMP](../../t-sql/functions/current-timestamp-transact-sql.md)|CURRENT_TIMESTAMP|Retourne un **datetime** valeur qui contient la date et l’heure de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Le décalage de fuseau horaire n'est pas inclus.|**datetime**|Non déterministe|  
|[GETDATE](../../t-sql/functions/getdate-transact-sql.md)|GETDATE ( )|Retourne un **datetime** valeur qui contient la date et l’heure de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Le décalage de fuseau horaire n'est pas inclus.|**datetime**|Non déterministe|  
|[GETUTCDATE](../../t-sql/functions/getutcdate-transact-sql.md)|GETUTCDATE ( )|Retourne un **datetime** valeur qui contient la date et l’heure de l’ordinateur sur lequel l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. La date et l’heure est retourné en tant que l’heure UTC (Coordinated Universal Time).|**datetime**|Non déterministe|  
  
###  <a name="GetDateandTimeParts"></a>Fonctions permettant d’obtenir des parties de Date et d’heure
  
|Fonction|Syntaxe|Valeur retournée|Type de données de retour|Propriété de déterminisme|  
|--------------|------------|------------------|----------------------|-----------------|  
|[DATENAME](../../t-sql/functions/datename-transact-sql.md)|DATENAME ( *datepart* , *date* )|Retourne une chaîne de caractères qui représente l’élément *datepart* de la date spécifiée.|**nvarchar**|Non déterministe|  
|[DATEPART](../../t-sql/functions/datepart-transact-sql.md)|DATEPART ( *datepart* , *date* )|Retourne un entier qui représente l’élément *datepart* spécifié *date*.|**int**|Non déterministe|  
|[DAY](../../t-sql/functions/day-transact-sql.md)|JOUR ( *date* )|Retourne un entier qui représente la partie jour de l’objet *date*.|**int**|Déterministe|  
|[MONTH](../../t-sql/functions/month-transact-sql.md)|MOIS ( *date* )|Retourne un entier qui représente la partie mois d’un *date*.|**int**|Déterministe|  
|[YEAR](../../t-sql/functions/year-transact-sql.md)|ANNÉE ( *date* )|Retourne un entier qui représente la partie année d’un *date*.|**int**|Déterministe|  
  
###  <a name="fromParts"></a>Fonctions permettant d’obtenir les valeurs de Date et heure à partir de leurs parties
  
|Fonction|Syntaxe|Valeur retournée|Type de données de retour|Propriété de déterminisme|  
|---|---|---|---|---|
|[DATEFROMPARTS](../../t-sql/functions/datefromparts-transact-sql.md)|DATEFROMPARTS ( *année*, *mois*, *jour* )|Retourne un **date** valeur pour l’année, mois et jour.|**date**|Déterministe|  
|[DATETIME2FROMPARTS](../../t-sql/functions/datetime2fromparts-transact-sql.md)|DATETIME2FROMPARTS ( *année*, *mois*, *jour*, *heure*, *minute*, *secondes* , *fractions*, *précision*)|Retourne un **datetime2** valeur pour la date et heure spécifiées et avec la précision spécifiée.|**datetime2 (** *précision* **)**|Déterministe|  
|[DATETIMEFROMPARTS](../../t-sql/functions/datetimefromparts-transact-sql.md)|DATETIMEFROMPARTS ( *année*, *mois*, *jour*, *heure*, *minute*, *secondes* , *millisecondes*)|Retourne un **datetime** valeur pour la date et heure spécifiées.|**datetime**|Déterministe|  
|[DATETIMEOFFSETFROMPARTS](../../t-sql/functions/datetimeoffsetfromparts-transact-sql.md)|DATETIMEOFFSETFROMPARTS ( *année*, *mois*, *jour*, *heure*, *minute*,  *secondes*, *fractions*, *hour_offset*, *minute_offset*, *précision*)|Retourne un **datetimeoffset** valeur pour la date et heure spécifiées et avec la précision et le décalage spécifiés.|**DateTime (** *précision* **)**|Déterministe|  
|[SMALLDATETIMEFROMPARTS](../../t-sql/functions/smalldatetimefromparts-transact-sql.md)|SMALLDATETIMEFROMPARTS ( *année*, *mois*, *jour*, *heure*, *minute* )|Retourne un **smalldatetime** valeur pour la date et heure spécifiées.|**smalldatetime**|Déterministe|  
|[TIMEFROMPARTS](../../t-sql/functions/timefromparts-transact-sql.md)|TIMEFROMPARTS ( *heure*, *minute*, *secondes*, *fractions*, *précision* )|Retourne un **temps** valeur pour l’heure spécifiée et avec la précision spécifiée.|**heure (** *précision* **)**|Déterministe|  
  
###  <a name="GetDateandTimeDifference"></a>Fonctions permettant d’obtenir la différence de Date et d’heure
  
|Fonction|Syntaxe|Valeur retournée|Type de données de retour|Propriété de déterminisme|  
|---|---|---|---|---|
|[DATEDIFF](../../t-sql/functions/datediff-transact-sql.md)|DATEDIFF ( *datepart* , *startdate* , *enddate* )|Retourne le nombre de date ou heure *datepart* limites qui sont comprises entre deux dates spécifiées.|**int**|Déterministe|  
|[DATEDIFF_BIG](../../t-sql/functions/datediff-big-transact-sql.md)|DATEDIFF_BIG ( *datepart* , *startdate* , *enddate* )|Retourne le nombre de date ou heure *datepart* limites qui sont comprises entre deux dates spécifiées.|**bigint**|Déterministe|  
  
###  <a name="ModifyDateandTimeValues"></a>Fonctions qui modifient les valeurs de Date et d’heure
  
|Fonction|Syntaxe|Valeur retournée|Type de données de retour|Propriété de déterminisme|  
|---|---|---|---|---|
|[DATEADD](../../t-sql/functions/dateadd-transact-sql.md)|DATEADD (*datepart* , *nombre* , *date* )|Retourne un nouveau **datetime** valeur en ajoutant un intervalle spécifié *datepart* spécifié *date*.|Type de données de la *date* argument|Déterministe|  
|[EOMONTH](../../t-sql/functions/eomonth-transact-sql.md)|EOMONTH ( *start_date* [, *month_to_add* ])|Retourne le dernier jour du mois qui contient la date spécifiée, avec un décalage facultatif.|Type de retour est le type de *start_date* ou **date**.|Déterministe|  
|[SWITCHOFFSET](../../t-sql/functions/switchoffset-transact-sql.md)|COMMUTATEUR*décalage* (*DATETIMEOFFSET* , *time_zone*)|COMMUTATEUR*OFFSET* modifie le décalage de fuseau horaire d’une valeur DATETIMEOFFSET et préserve la valeur UTC.|**DateTimeOffset** avec une précision de fractions de seconde le *DATETIMEOFFSET*|Déterministe|  
|[TODATETIMEOFFSET](../../t-sql/functions/todatetimeoffset-transact-sql.md)|TODATETIMEOFFSET (*expression* , *time_zone*)|TODATETIMEOFFSET transforme une valeur datetime2 en une valeur datetimeoffset. La valeur datetime2 est interprétée en heure locale pour le time_zone spécifié.|**DateTimeOffset** avec une précision de fractions de seconde le *datetime* argument|Déterministe|  
  
###  <a name="SetorGetSessionFormatFunctions"></a>Fonctions qui obtient ou définit le format de session
  
|Fonction|Syntaxe|Valeur retournée|Type de données de retour|Propriété de déterminisme|  
|---|---|---|---|---|
|[@@DATEFIRST](../../t-sql/functions/datefirst-transact-sql.md)|@@DATEFIRST |Retourne la valeur actuelle, pour la session, de SET DATEFIRST.|**tinyint**|Non déterministe|  
|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)|SET DATEFIRST { *nombre* &#124;  **@**  *var_nombre* }|Affecte au premier jour de la semaine un nombre allant de 1 à 7.|Non applicable|Non applicable|  
|[SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)|SET DATEFORMAT { *format* &#124;  **@**  *format_var* }|Définit l’ordre des parties de date (jour/mois/année) pour l’entrée **datetime** ou **smalldatetime** données.|Non applicable|Non applicable|  
|[@@LANGUAGE](../../t-sql/functions/language-transact-sql.md)|@@LANGUAGE |Retourne le nom de la langue actuellement utilisée. @@LANGUAGE n’est pas une fonction de date ou d’heure. Toutefois, le paramètre de langue peut affecter la sortie de fonctions de date.|Non applicable|Non applicable|  
|[DÉFINITION DE LA LANGUE](../../t-sql/statements/set-language-transact-sql.md)|SET LANGUAGE {[N] **'***langage***'** &#124;  **@**  *var_langue* }|Définit l'environnement de la langue pour la session et les messages système. SET LANGUAGE n'est pas une fonction de date ou d'heure. Toutefois, le paramètre de langue affecte la sortie de fonctions de date.|Non applicable|Non applicable|  
|[sp_helplanguage](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)|**sp_helplanguage** [[  **@language =** ] **'***langage***'** ]|Retourne des informations sur les formats de date de toutes les langues prises en charge. **sp_helplanguage** n’est pas une date ou heure procédure stockée. Toutefois, le paramètre de langue affecte la sortie de fonctions de date.|Non applicable|Non applicable|  
  
###  <a name="ValidateDateandTimeValues"></a>Fonctions permettant de valider les valeurs de Date et heure
  
|Fonction|Syntaxe|Valeur retournée|Type de données de retour|Propriété de déterminisme|  
|---|---|---|---|---|
|[ISDATE](../../t-sql/functions/isdate-transact-sql.md)|ISDATE ( *expression* )|Détermine si un **datetime** ou **smalldatetime** expression d’entrée est une date valide ou une valeur d’heure.|**int**|ISDATE est déterministe uniquement si elle est utilisée avec la fonction CONVERT, lorsque le paramètre de style CONVERT est spécifié et que le style est différent de 0, 100, 9 ou 109.|  
  
##  <a name="DateandTimeRelatedTopics"></a>Date et les rubriques relatives à la fois 
  
|Rubrique| Description|  
|-----------|-----------------|  
|[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)|Fournit des informations sur la conversion des valeurs de date et d'heure depuis et vers des littéraux de chaîne et d'autres formats de date et d'heure.|  
|[Rédiger des instructions Transact-SQL internationales](../../relational-databases/collations/write-international-transact-sql-statements.md)|Fournit des instructions pour la portabilité des bases de données et les applications de base de données qui utilisent [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions d’une langue à l’autre ou qui prennent en charge plusieurs langues.|  
|[Fonctions scalaires ODBC &#40; Transact-SQL &#41;](../../t-sql/functions/odbc-scalar-functions-transact-sql.md)|Fournit des informations sur les fonctions scalaires ODBC qui peut être utilisé dans [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions. Cela inclut les fonctions de date et d’heure ODBC.|  
|[FUSEAU horaire &AMP;#40; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)|Fournit la conversion du fuseau horaire.|  
  
## <a name="see-also"></a>Voir aussi
[Fonctions](../../t-sql/functions/functions.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
