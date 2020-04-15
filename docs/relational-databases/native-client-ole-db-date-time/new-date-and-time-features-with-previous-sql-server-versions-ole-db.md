---
title: Caractéristiques DB date et heure avec versions précédentes de serveur SQL
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 96976bac-018c-47cc-b1b2-fa9605eb55e5
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a90863fb061912dd0a6c44fe23ba2baa402662c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301014"
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>Nouvelles fonctionnalités de date et d’heure avec les versions précédentes de SQL Server (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ce sujet décrit le comportement attendu lorsqu’une application client qui utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]fonctionnalités améliorées de date [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et d’heure communique avec une version de plus tôt que , et quand un client compilé avec une version de Native Client plus tôt que [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] envoie des commandes à un serveur qui prend en charge les fonctionnalités améliorées de date et d’heure.  
  
## <a name="down-level-client-behavior"></a>Comportement de client de bas niveau  
 Applications client qui utilisent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une version [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] de Native Client plus tôt que de voir les nouveaux types de date / heure comme colonnes **nvarchar.** Les contenus des colonnes sont des représentations littérales. Pour plus d’informations, consultez la section « Formats de données : chaînes et littérales » de [Data Type Support for OLE DB Date and Time Improvements](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md). La taille de colonne est la longueur littérale maximale pour la précision spécifiée pour la colonne.  
  
 Les API de catalogue retourneront les métadonnées compatibles avec le code de type de données de bas niveau retourné au client (par exemple, **nvarchar**) et la représentation de niveau descendant associé (par exemple, le format littéral approprié). Toutefois, le nom du type de données retourné est le nom de type [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] réel.  
  
 Lorsqu’une application client de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] niveau descendant s’exécute contre un serveur (ou plus tard) sur lequel des modifications de schéma à date/types d’heure ont été faites, le comportement attendu est le suivant :  
  
|Type du client OLE DB|Type SQL Server 2005|SQL Server 2008 (ou versions ultérieures)|Conversion de résultat (serveur vers client)|Conversion de paramètre (client vers serveur)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|Datetime|Date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Champs d'heure définis à zéro.|IRowsetChange échouera en raison de la troncation des cordes si le champ de temps n’est pas zéro.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Champs de date définis à la date actuelle.|IRowsetChange échouera en raison de la troncation des cordes si les secondes fractionnelles ne sont pas nulles.<br /><br /> La date est ignorée.|  
|DBTYPE_DBTIME||Time(7)|Échec - temps invalide littéral.|OK|  
|DBTYPE_DBTIMESTAMP|||Échec - temps invalide littéral.|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2(3)|OK|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2(7)|OK|OK|  
|DBTYPE_DBDATE|Smalldatetime|Date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Champs d'heure définis à zéro.|IRowsetChange échouera en raison de la troncation des cordes si le champ de temps n’est pas zéro.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Champs de date définis à la date actuelle.|IRowsetChange échouera en raison de la troncation des cordes si les secondes fractionnelles ne sont pas nulles.<br /><br /> La date est ignorée.|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|OK|OK|  
  
 OK signifie que si cela a fonctionné avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], cela doit continuer à fonctionner avec [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure).  
  
 Seules les modifications de schéma communes suivantes ont été considérées :  
  
-   Utilisation d'un nouveau type alors qu'en toute logique une application requiert uniquement une valeur de date ou d'heure. Toutefois, l’application a été forcée d’utiliser **le délai** de date ou **le smalldatetime** parce que les types de date et d’heure distincts n’étaient pas disponibles.  
  
-   Utilisation d'un nouveau type pour gagner en précision sur les fractions de seconde.  
  
-   Passer à **datetime2** parce qu’il s’agit du type de données préféré pour la date et l’heure.  
  
 Applications qui utilisent des métadonnées serveur obtenues via ICommandWithParameters::GetParameterInfo ou des rames schémas pour définir des informations de type paramètre via ICommandWithParameters::SetParameterInfo échouera lors des conversions des clients où la représentation des chaînes d’un type source est plus grande que la représentation des chaînes du type de destination. Par exemple, si une liaison client utilise DBTYPE_DBTIMESTAMP et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que la colonne du serveur est la date, Native Client convertira la valeur en "yyyy-dd-mm hh:mm:ss.fff", mais les métadonnées du serveur seront retournées sous **forme de nvarchar(10)**. Le dépassement de capacité résultant provoque DBSTATUS_E_CATCONVERTVALUE. Des problèmes similaires surviennent avec les conversions de données par IRowsetChange, parce que les métadonnées encastrées sont définies à partir des métadonnées de résultats.  
  
### <a name="parameter-and-rowset-metadata"></a>Métadonnées de paramètre et d'ensemble de lignes  
 Cette section décrit les métadonnées pour les paramètres, les colonnes de résultats [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]rangées de schémas pour les clients qui sont compilés avec une version de Native Client plus tôt que .  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 La structure DBPARAMINFO renvoie les informations suivantes via le paramètre *prgParamInfo* :  
  
|Type de paramètre|wType|ulParamSize|bPrecision|bScale|  
|--------------------|-----------|-----------------|----------------|------------|  
|Date|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
 Notez que certaines de ces plages de valeurs sont discontinues ; par exemple, 9 est manquant dans 8,10..16. Cela est dû à l'ajout d'une virgule décimale lorsque la précision fractionnaire est supérieure à zéro.  
  
#### <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Les colonnes suivantes sont retournées :  
  
|Type de colonne|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|  
|-----------------|--------------------|--------------------------|-------------------------|--------------------------------------------------|  
|Date|DBTYPE_WSTR|10|NULL|NULL|  
|time|DBTYPE_WSTR|8, 10..16|NULL|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 La structure DBCOLUMNINFO renvoie les informations suivantes :  
  
|Type de paramètre|wType|ulColumnSize|bPrecision|bScale|  
|--------------------|-----------|------------------|----------------|------------|  
|Date|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
### <a name="schema-rowsets"></a>Ensembles de lignes de schéma  
 Cette section décrit les métadonnées des paramètres, des colonnes de résultats et des ensembles de lignes de schéma pour les nouveaux types de données. Cette information est utile, c’est que [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous avez un fournisseur de clients développé à l’aide d’outils plus tôt que Native Client.  
  
#### <a name="columns-rowset"></a>Ensemble de lignes COLUMNS  
 Les valeurs de colonnes suivantes sont retournées pour les types date/heure :  
  
|Type de colonne|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|Date|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|NULL|  
  
#### <a name="procedure_parameters-rowset"></a>Ensemble de lignes PROCEDURE_PARAMETERS  
 Les valeurs de colonnes suivantes sont retournées pour les types date/heure :  
  
|Type de colonne|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|Date|DBTYPE_WSTR|10|20|Date|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|DATETIME|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|datetimeoffset|  
  
#### <a name="provider_types-rowset"></a>Ensemble de lignes PROVIDER_TYPES  
 Les lignes suivantes sont retournées pour les types date/heure :  
  
|Type -><br /><br /> Colonne|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_WSTR|DBTYPE_WSTR|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_WSTR|DBTYPE_WSTR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_TRUE|VARIANT_FALSE|VARIANT_FALSE|  
|IS_FIXEDLENGTH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
  
## <a name="down-level-server-behavior"></a>Comportement de serveur de bas niveau  
 Lorsqu’il est connecté à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]un serveur d’une version antérieure que , toute tentative d’utiliser les nouveaux noms de type serveur (par exemple, avec ICommandWithParameters::SetParameterInfo ou ITableDefinition::CreateTable) se traduira par DB_E_BADTYPENAME.  
  
 Si de nouveaux types sont liés pour des paramètres ou des résultats sans l'utilisation d'un nom de type, et si le nouveau type est utilisé pour spécifier le type serveur implicitement ou s'il n'existe pas de conversion valide du type serveur en type client, DB_E_ERRORSOCCURRED est retourné ; par ailleurs, DBBINDSTATUS_UNSUPPORTED_CONVERSION est défini en tant qu'état de liaison pour l'accesseur utilisé au moment de l'exécution.  
  
 S'il existe une conversion cliente prise en charge du type de mémoire tampon en type serveur pour la version du serveur de la connexion, tous les types de mémoires tampons clients peuvent être utilisés. Dans ce contexte, le *type de serveur* désigne le type spécifié par ICommandWithParameters::SetParameterInfo, ou implicite par le type de tampon si ICommandWithParameters::SetParameterInfo n’a pas été appelé. En d'autres termes, DBTYPE_DBTIME2 et DBTYPE_DBTIMESTAMPOFFSET peuvent être utilisés avec des serveurs de bas niveau, ou lorsque DataTypeCompatibility=80, si la conversion cliente vers un type serveur pris en charge réussit. Bien entendu, si le type serveur est incorrect, une erreur peut toujours être signalée par le serveur lorsque ce dernier ne peut pas effectuer de conversion implicite vers le type serveur effectif.  
  
## <a name="ssprop_init_datatypecompatibility-behavior"></a>Comportement de SSPROP_INIT_DATATYPECOMPATIBILITY  
 Lorsque SSPROP_INIT_DATATYPECOMPATIBILITY est réglée pour SSPROPVAL_DATATYPECOMPATIBILITY_SQL2000, les nouveaux types de date/heure et les métadonnées associées apparaissent aux clients tels qu’ils apparaissent pour les clients de niveau descendant, comme décrit dans [les modifications de copie en vrac pour les types de date et d’heure améliorés &#40;OLE DB et ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
## <a name="comparability-for-irowsetfind"></a>Comparabilité pour IRowsetFind  
 Tous les opérateurs de comparaison sont autorisés pour les nouveaux types date/heure, car ils apparaissent sous forme de types chaîne et non sous forme de types date/heure.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
