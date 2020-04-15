---
title: Date dans les versions SQL (ODBC)
ms.custom: ''
ms.date: 12/18/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC], enhanced behavior with earlier SQL Server versions
ms.assetid: cd4e137f-dc5e-4df7-bc95-51fe18c587e0
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8e5147a8eef08c70605bf13f6c1cb04887d0d926
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301879"
---
# <a name="enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc"></a>Comportement des types de date et d'heure améliorés avec les versions SQL Server antérieures (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique décrit le comportement attendu lorsqu'une application cliente qui utilise les fonctionnalités améliorées de date et d'heure communique avec une version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], et lorsqu'une application cliente qui utilise Microsoft Data Access Components, Windows Data Access Components ou une version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] envoie des commandes à un serveur qui prend en charge les fonctionnalités améliorées de date et d'heure.  
  
## <a name="down-level-client-behavior"></a>Comportement de client de bas niveau  
 Les applications clientes compilées à l'aide d'une version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] voient les nouveaux types de date et d'heure sous la forme de colonnes nvarchar. Le contenu de la colonne sont les représentations littérales, comme décrit dans la section « Formats de données : cordes et littérales » de [data Type Support for ODBC Date and Time Improvements](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md). La taille de colonne correspond à la longueur littérale maximale pour la précision en fractions de seconde spécifiée pour la colonne.  
  
 Les API du catalogue retournent des métadonnées conformes au code du type de données de bas niveau retourné au client (nvarchar, par exemple) et à la représentation de bas niveau associée (le format littéral approprié, par exemple). Toutefois, le nom du type de données retourné est le nom de type [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] réel.  
  
 Les métadonnées de déclaration retournées par SQLDescribeCol, SQLDescribeParam, SQGetDescField et SQLColAttribute retourneront des métadonnées compatibles avec le type de bas niveau à tous égards, y compris le nom de type. Un exemple d’un tel type de bas de gamme est **nvarchar**.  
  
 Lorsqu’une application client de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] niveau descendant s’exécute contre un serveur (ou plus tard) sur lequel des modifications de schéma à date/types d’heure ont été faites, le comportement attendu est le suivant :  
  
|Type SQL Server 2005|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]Type  (ou version ultérieure)|Type de client ODBC|Conversion des résultats (de SQL vers C)|Conversion des paramètres (de C vers SQL)|  
|--------------------------|----------------------------------------------|----------------------|------------------------------------|---------------------------------------|  
|Datetime|Date|SQL_C_TYPE_DATE|OK|OK (1)|  
|||SQL_C_TYPE_TIMESTAMP|Champs d'heure définis à zéro.|OK (2)<br /><br /> Échoue si le champ d'heure n'est pas nul. Fonctionne avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(0)|SQL_C_TYPE_TIME|OK|OK (1)|  
|||SQL_C_TYPE_TIMESTAMP|Champs de date définis à la date actuelle.|OK (2)<br /><br /> La date est ignorée. Échec si les secondes fractionnelles ne sont pas nulles. Fonctionne avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(7)|SQL_C_TIME|Échec - temps invalide littéral.|OK (1)|  
|||SQL_C_TYPE_TIMESTAMP|Échec - temps invalide littéral.|OK (1)|  
||Datetime2(3)|SQL_C_TYPE_TIMESTAMP|OK|OK (1)|  
||Datetime2(7)|SQL_C_TYPE_TIMESTAMP|OK|La valeur sera arrondie à 1/300e de seconde par la conversion cliente.|  
|Smalldatetime|Date|SQL_C_TYPE_DATE|OK|OK|  
|||SQL_C_TYPE_TIMESTAMP|Champs d'heure définis à zéro.|OK (2)<br /><br /> Échoue si le champ d'heure n'est pas nul. Fonctionne avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Time(0)|SQL_C_TYPE_TIME|OK|OK|  
|||SQL_C_TYPE_TIMESTAMP|Champs de date définis à la date actuelle.|OK (2)<br /><br /> La date est ignorée. Échoue si les fractions de seconde ne sont pas nulles.<br /><br /> Fonctionne avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||Datetime2(0)|SQL_C_TYPE_TIMESTAMP|OK|OK|  
|||||

## <a name="key-to-symbols"></a>Liste des symboles  
  
|Symbole|Signification|  
|------------|-------------|  
|1|Si cela a fonctionné avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] cela doit continuer à fonctionner avec une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|2|Une application qui fonctionnait avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] pourrait échouer avec une version plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|||

 Notez que seules les modifications de schéma courantes ont été considérées. Les modifications courantes sont les suivantes :  
  
-   Utilisation d'un nouveau type alors qu'en toute logique une application requiert uniquement une valeur de date ou d'heure. Toutefois, l'application a été forcée d'utiliser des données datetime ou smalldatetime en raison du manque de types de date et d'heure distincts.  
  
-   Utilisation d'un nouveau type pour gagner en précision sur les fractions de seconde.  
  
-   Passage à datetime2, car il représente le type de données de date et d'heure préféré.  
  
### <a name="column-metadata-returned-by-sqlcolumns-sqlprocedurecolumns-and-sqlspecialcolumns"></a>Métadonnées de colonne retournées par SQLColumns, SQLProcedureColumns et SQLSpecialColumns  
 Les valeurs de colonnes suivantes sont retournées pour les types date/heure :  
  
|Type de colonne|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_WVARCHAR|SQL_WVARCHAR|  
|TYPE_NAME|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|COLUMN_SIZE|10|8,10..16|16|23|19, 21..27|26, 28..34|  
|BUFFER_LENGTH|20|16, 20..32|16|16|38, 42..54|52, 56..68|  
|DECIMAL_DIGITS|NULL|NULL|0|3|NULL|NULL|  
|SQL_DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_DATETIME|SQL_DATETIME|SQL_WVARCHAR|SQL_WVARCHAR|  
|SQL_DATETIME_SUB|NULL|NULL|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|NULL|NULL|  
|CHAR_OCTET_LENGTH|NULL|NULL|NULL|NULL|NULL|NULL|  
|SS_DATA_TYPE|0|0|111|111|0|0|  
||||||||

 SQLSpecialColumns ne retourne pas SQL_DATA_TYPE, SQL_DATETIME_SUB, CHAR_OCTET_LENGTH ni SS_DATA_TYPE.  
  
### <a name="data-type-metadata-returned-by-sqlgettypeinfo"></a>Métadonnées de type de données retournées par SQLGetTypeInfo  
 Les valeurs de colonnes suivantes sont retournées pour les types date/heure :  
  
|Type de colonne|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|-----------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_TYPE_TIMESTAMP|SQL_TYPE_TIMESTAMP|SQL_WVARCHAR|SQL_WVARCHAR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|SQL_NULLABLE|  
|CASE_SENSITIVE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|SQL_PRED_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FXED_PREC_SCALE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|SQL_FALSE|  
|AUTO_UNIQUE_VALUE|NULL|NULL|NULL|NULL|NULL|NULL|  
|LOCAL_TYPE_NAME|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|0|3|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|0|3|NULL|NULL|  
|SQL_DATA_TYPE|SQL_WVARCHAR|SQL_WVARCHAR|SQL_DATETIME|SQL_DATETIME|SQL_WVARCHAR|SQL_WVARCHAR|  
|SQL_DATETIME_SUB|NULL|NULL|SQL_CODE_TIMESTAMP|SQL_CODE_TIMESTAMP|NULL|NULL|  
|NUM_PREC_RADIX|NULL|NULL|NULL|NULL|NULL|NULL|  
|INTERVAL_PRECISION|NULL|NULL|NULL|NULL|NULL|NULL|  
|USERTYPE|0|0|12|22|0|0|  
||||||||

## <a name="down-level-server-behavior"></a>Comportement de serveur de bas niveau  
 En cas de connexion à une instance de serveur d'une version antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], toute tentative d'utiliser les nouveaux types de serveur ou les codes de métadonnées et les champs de descripteur associés provoquera le renvoi d'une erreur SQL_ERROR. Un enregistrement de diagnostic sera généré avec SQLSTATE HY004 et le message « Type de données SQL non valide pour la version du serveur lors de la connexion », ou avec 07006 et « Violation de l'attribut de type de données restreint ».  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations de la date et de l’heure &#40;&#41;ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
