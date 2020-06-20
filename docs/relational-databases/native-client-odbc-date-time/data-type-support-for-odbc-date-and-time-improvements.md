---
title: Prise en charge du type, date et heure ODBC
description: Découvrez les types ODBC qui prennent en charge les types de données de date et d’heure SQL Server, y compris le mappage de type de données et les formats pour les chaînes, les littéraux et les structures de données.
ms.custom: ''
ms.date: 12/18/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC], data type support
- ODBC, date/time improvements
ms.assetid: 8e0d9ba2-3ec1-4680-86e3-b2590ba8e2e9
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cdab7196199b28835d5f21c0c51f3ad787fdc7ac
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967669"
---
# <a name="data-type-support-for-odbc-date-and-time-improvements"></a>Prise en charge des types de données pour les améliorations date/heure (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique fournit des informations sur les types ODBC qui prennent en charge les types des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date et time.  
  
## <a name="data-type-mapping-in-parameters-and-resultsets"></a>Mappage de type de données dans les paramètres et les jeux de résultats  
 En plus des types de données ODBC (SQL_TYPE_TIMESTAMP et SQL_TIMESTAMP), deux nouveaux types de données ont été ajoutés dans ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client pour exposer les nouveaux types de serveur :  
  
-   SQL_SS_TIME2  
  
-   SQL_SS_TIMESTAMPOFFSET  
  
 Le tableau ci-dessous correspond au mappage complet de type serveur. Remarquez que certaines cellules contiennent deux entrées ; dans ces cas, la première est la valeur ODBC 3.0 et la seconde la valeur ODBC 2.0.  
  
|Type de données SQL Server|Type de données SQL|Value|  
|--------------------------|-------------------|-----------|  
|Datetime|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|93 (sql.h)<br /><br /> 11 (sqlext.h)|  
|Smalldatetime|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|93 (sql.h)<br /><br /> 11 (sqlext.h)|  
|Date|SQL_TYPE_DATE<br /><br /> SQL_DATE|91 (SQL. h)<br /><br /> 9 (Sqlext. h)|  
|Heure|SQL_SS_TIME2|-154 (SQLNCLI. h)|  
|DatetimeOFFSET|SQL_SS_TIMESTAMPOFFSET|-155 (SQLNCLI.h)|  
|Datetime2|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|93 (sql.h)<br /><br /> 11 (sqlext.h)|  
||||

 Le tableau suivant répertorie les structures et les types ODBC correspondants. Comme ODBC n'autorise pas les types C définis par le pilote, SQL_C_BINARY est utilisé pour les types time et datetimeoffset comme structures binaires.  
  
|Type de données SQL|Disposition en mémoire|Type de données C par défaut|Valeur (sqlext.h)|  
|-------------------|-------------------|-------------------------|------------------------|  
|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|SQL_TIMESTAMP_STRUCT<br /><br /> TIMESTAMP_STRUCT|SQL_C_TYPE_TIMESTAMP<br /><br /> SQL_C_TIMESTAMP|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|  
|SQL_TYPE_DATE<br /><br /> SQL_DATE|SQL_DATE_STRUCT<br /><br /> DATE_STRUCT|SQL_C_TYPE_DATE<br /><br /> SQL_C_DATE|SQL_TYPE_DATE<br /><br /> SQL_DATE|  
|SQL_SS_TIME2|SQL_SS_TIME2_STRUCT|SQL_C_SS_TIME2<br /><br /> SQL_C_BINARY (ODBC 3.5 et versions antérieures)|0x4000 (sqlncli.h)<br /><br /> SQL_BINARY (-2)|  
|SQL_SS_TIMESTAMPOFFSET|SQL_SS_TIMESTAMPOFFSET_STRUCT|SQL_C_SS_TIMESTAMPOFFSET<br /><br /> SQL_C_BINARY (ODBC 3.5 et versions antérieures)|0x4001 (sqlncli.h)<br /><br /> SQL_BINARY (-2)|  
|||||

 Lorsque la liaison SQL_C_BINARY est spécifiée, la vérification de l'alignement est effectuée et une erreur signalée en cas d'alignement incorrect. Dans le cas de cette erreur, SQLSTATE a la valeur IM016, avec le message « Alignement des structures non valide ».  
  
## <a name="data-formats-strings-and-literals"></a>Formats de données : chaînes et littéraux  
 Le tableau suivant représente les mappages entre les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les types de données ODBC et les littéraux de chaîne ODBC.  
  
|Type de données SQL Server|Type de données ODBC|Format de chaîne pour les conversions clientes|  
|--------------------------|--------------------|------------------------------------------|  
|Datetime|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|'aaaa-mm-jj hh:mm:ss[.999]'<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge jusqu'à trois chiffres de fractions de seconde pour le type Datetime.|  
|Smalldatetime|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|'aaaa-mm-jj hh:hh:ss'<br /><br /> Ce type de données possède une précision d'une minute. Le composant des secondes sera égal à zéro en sortie et arrondi par le serveur en entrée.|  
|Date|SQL_TYPE_DATE<br /><br /> SQL_DATE|'aaaa-mm-jj'|  
|Heure|SQL_SS_TIME2|'hh:mm:ss[.9999999]'<br /><br /> Le cas échéant, les fractions de seconde peuvent être spécifiées à l'aide de sept chiffres au plus.|  
|Datetime2|SQL_TYPE_TIMESTAMP<br /><br /> SQL_TIMESTAMP|'aaaa-mm-jj hh : mm : SS [. 9999999] '<br /><br /> Le cas échéant, les fractions de seconde peuvent être spécifiées à l'aide de sept chiffres au plus.|  
|DatetimeOFFSET|SQL_SS_TIMESTAMPOFFSET|'aaaa-mm-jj hh:mm:ss[.9999999] +/- hh:mm'<br /><br /> Le cas échéant, les fractions de seconde peuvent être spécifiées à l'aide de sept chiffres au plus.|  
||||

 Il n'y a pas de modifications aux séquences d'échappement ODBC pour les littéraux de type date/time.  
  
 Dans les résultats, les fractions de seconde utilisent toujours un point (.), plutôt que les deux-points (:).  
  
 Les valeurs de chaîne retournées aux applications sont toujours de la même longueur pour une colonne donnée. La longueur maximale des composants année, mois, jour, heure, minute et seconde, est complétée avec des zéros non significatifs, et le jour et l'heure des valeurs datetime sont séparés par un espace. Il y a également un espace entre l'heure et le décalage horaire dans une valeur datetimeoffset. Un décalage horaire est toujours précédé d'un signe ; quand le décalage est nul, le signe est un plus (+). Les fractions de seconde sont complétées si nécessaire avec des zéros à droite, jusqu'à la précision maximale définie pour la colonne. Pour les colonnes datetime, il y a trois chiffres de fractions de seconde. Pour les colonnes smalldatetime, il n'y a pas de chiffres de fractions de seconde et les secondes sont toujours égales à zéro.  
  
 Une chaîne vide n'est pas un littéral de date et d'heure valide et ne représente pas une valeur NULL. La tentative de convertir une chaîne vide en valeur date/time provoque l'erreur SQLState 22018 et le message « Valeur de caractère non valide pour la spécification de la casse ».  
  
 Les conversions de paramètres de chaîne attendent des chaînes au même format, si ce n'est que le signe d'une valeur timezone avec les heures et les minutes nulles peut être plus ou moins, et que les zéros à droite sont autorisés pour les fractions de seconde composées au plus de 9 chiffres. Un composant heure peut se terminer avec une virgule décimale et aucun chiffre de fractions de seconde.  
  
 Actuellement, le pilote autorise un espace supplémentaire autour des caractères de ponctuation et l'espace entre l'heure et le décalage horaire est facultatif. Toutefois, il se peut qu'il en aille différemment dans une version ultérieure ; les applications ne doivent pas s'appuyer sur le comportement actuel.  
  
## <a name="data-formats-data-structures"></a>Formats de données : structures de données  
 Dans les structures décrites ci-après, ODBC spécifie les contraintes suivantes, extraites du calendrier grégorien :  
  
-   La plage des mois s'étend de 1 à 12.  
  
-   La plage des jours s'étend de 1 au nombre de jours dans le mois, et doit être cohérente avec les années et les mois  en tenant compte des années bissextiles.  
  
-   La plage des heures s'étend de 0 à 23.  
  
-   La plage des minutes s'étend de 0 à 59.  
  
-   La plage des secondes est 0 comprise entre 0 et 61.9 (n). Ceci permet d’ajouter jusqu’à deux secondes intercalaires pour conserver la synchronisation avec l’heure sidérale.  
  
     Notez que, comme [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'autorise pas les secondes intercalaires, les valeurs de de secondes supérieures à 59 provoquent une erreur de serveur.  
  
 Les implémentations pour les structs ODBC existants suivants ont été modifiées afin de prendre en charge les nouveaux types de données date et time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, les définitions n'ont pas changé.  
  
-   DATE_STRUCT  
  
-   TIME_STRUCT  
  
-   TIMESTAMP_STRUCT  
  
 Il existe aussi deux nouveaux structs :  
  
-   SQL_SS_TIME2_STRUCT  
  
-   SQL_SS_TIMESTAMPOFFSET_STRUCT  
  
### <a name="sql_ss_time2_struct"></a>SQL_SS_TIME2_STRUCT  
 Ce struct est complété jusqu'à 12 octets sur les systèmes d'exploitation 32 bits et 64 bits.  
  
```cpp
typedef struct tagSS_TIME2_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;  
} SQL_SS_TIME2_STRUCT;  
```  
  
### <a name="sql_ss_timestampoffset_struct"></a>SQL_SS_TIMESTAMPOFFSET_STRUCT  
  
```cpp
typedef struct tagSS_TIMESTAMPOFFSET_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;  
   SQLSMALLINT timezone_hour;  
   SQLSMALLINT timezone_minute;  
} SQL_SS_TIMESTAMPOFFSET_STRUCT;  
```  
  
 Si le **timezone_hour** est négatif, le **timezone_minute** doit être négatif ou égal à zéro. Si le **timezone_hour** est positif, le **timezone_minute** doit être positif ou zéro. Si la **timezone_hour** est égale à zéro, la **timezone_minute** peut avoir n’importe quelle valeur comprise dans la plage comprise entre-59 et + 59.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations de la date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
