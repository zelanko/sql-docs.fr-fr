---
title: Fonctionnalités de date et d’heure OLE DB avec les versions SQL Server antérieures
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 96976bac-018c-47cc-b1b2-fa9605eb55e5
author: MightyPen
ms.author: genemi
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 100a0b6a96c9359e224e406928b03a2aa776511e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74095454"
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>Nouvelles fonctionnalités de date et d’heure avec les versions précédentes de SQL Server (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique décrit le comportement attendu lorsqu’une application cliente qui utilise des fonctionnalités améliorées de date et d’heure communique [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]une version de antérieure à, et lorsqu’un client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compilé avec une version [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] de Native Client antérieure à envoie des commandes à un serveur qui prend en charge les fonctionnalités de date et d’heure améliorées.  
  
## <a name="down-level-client-behavior"></a>Comportement de client de bas niveau  
 Les applications clientes qui utilisent une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version de native client [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] antérieure à voient les nouveaux types de date/heure en tant que colonnes **nvarchar** . Les contenus des colonnes sont des représentations littérales. Pour plus d’informations, consultez la section « formats de données : chaînes et littéraux » de [type de données prise en charge de OLE DB améliorations de la date et](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)de l’heure. La taille de colonne est la longueur littérale maximale pour la précision spécifiée pour la colonne.  
  
 Les API de catalogue retournent des métadonnées cohérentes avec le code de type de données de niveau supérieur retourné au client (par exemple, **nvarchar**) et la représentation de niveau inférieure associée (par exemple, le format littéral approprié). Toutefois, le nom du type de données retourné est le nom de type [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] réel.  
  
 Quand une application cliente de bas niveau s’exécute [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sur un serveur (ou version ultérieure) sur lequel des modifications de schéma ont été apportées aux types de date/heure, le comportement attendu est le suivant :  
  
|Type du client OLE DB|Type SQL Server 2005|SQL Server 2008 (ou versions ultérieures)|Conversion de résultat (serveur vers client)|Conversion de paramètre (client vers serveur)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|Datetime|Date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Champs d'heure définis à zéro.|IRowsetChange échoue en raison de la troncation de chaîne si le champ d’heure est différent de zéro.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Champs de date définis à la date actuelle.|IRowsetChange échoue en raison de la troncation de chaîne si les fractions de seconde ne sont pas égales à zéro.<br /><br /> La date est ignorée.|  
|DBTYPE_DBTIME||Time(7)|Échec : littéral d’heure non valide.|OK|  
|DBTYPE_DBTIMESTAMP|||Échec : littéral d’heure non valide.|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2 (3)|OK|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2 (7)|OK|OK|  
|DBTYPE_DBDATE|Smalldatetime|Date|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Champs d'heure définis à zéro.|IRowsetChange échoue en raison de la troncation de chaîne si le champ d’heure est différent de zéro.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Champs de date définis à la date actuelle.|IRowsetChange échoue en raison de la troncation de chaîne si les fractions de seconde ne sont pas égales à zéro.<br /><br /> La date est ignorée.|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|OK|OK|  
  
 OK signifie que si cela a fonctionné avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], cela doit continuer à fonctionner avec [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure).  
  
 Seules les modifications de schéma communes suivantes ont été considérées :  
  
-   Utilisation d'un nouveau type alors qu'en toute logique une application requiert uniquement une valeur de date ou d'heure. Toutefois, l’application a été obligée d’utiliser **DateTime** ou **smalldatetime** , car des types de date et d’heure distincts n’étaient pas disponibles.  
  
-   Utilisation d'un nouveau type pour gagner en précision sur les fractions de seconde.  
  
-   Passage à **datetime2** , car il s’agit du type de données par défaut pour la date et l’heure.  
  
 Les applications qui utilisent les métadonnées de serveur obtenues via ICommandWithParameters :: GetParameterInfo ou les ensembles de lignes de schéma pour définir les informations de type de paramètre par le biais de ICommandWithParameters :: SetParameterInfo échouent lors des conversions clientes où la chaîne la représentation d’un type de source est supérieure à la représentation sous forme de chaîne du type de destination. Par exemple, si une liaison cliente utilise DBTYPE_DBTIMESTAMP et que la colonne de serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est date, Native Client convertit la valeur en « yyyy-jj-mm hh : mm : SS. fff », mais les métadonnées de serveur sont retournées en tant que **nvarchar (10)**. Le dépassement de capacité résultant provoque DBSTATUS_E_CATCONVERTVALUE. Des problèmes similaires se produisent avec les conversions de données par IRowsetChange, car les métadonnées de l’ensemble de lignes sont définies à partir des métadonnées du jeu de résultats.  
  
### <a name="parameter-and-rowset-metadata"></a>Métadonnées de paramètre et d'ensemble de lignes  
 Cette section décrit les métadonnées des paramètres, des colonnes de résultats et des ensembles de lignes de schéma pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clients qui sont compilés avec une version de Native Client antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 La structure DBPARAMINFO retourne les informations suivantes par le biais du paramètre *prgParamInfo* :  
  
|Type de paramètre|wType|ulParamSize|bPrecision|bScale|  
|--------------------|-----------|-----------------|----------------|------------|  
|Date|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|~0|~0|  
  
 Notez que certaines de ces plages de valeurs sont discontinues ; par exemple, 9 est manquant dans 8,10..16. Cela est dû à l'ajout d'une virgule décimale lorsque la précision fractionnaire est supérieure à zéro.  
  
#### <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Les colonnes suivantes sont retournées :  
  
|Type de colonne|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|  
|-----------------|--------------------|--------------------------|-------------------------|--------------------------------------------------|  
|Date|DBTYPE_WSTR|10|NULL|NULL|  
|time|DBTYPE_WSTR|8, 10..16|NULL|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 La structure DBCOLUMNINFO retourne les informations suivantes :  
  
|Type de paramètre|wType|ulColumnSize|bPrecision|bScale|  
|--------------------|-----------|------------------|----------------|------------|  
|Date|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|~0|~0|  
  
### <a name="schema-rowsets"></a>Ensembles de lignes de schéma  
 Cette section décrit les métadonnées des paramètres, des colonnes de résultats et des ensembles de lignes de schéma pour les nouveaux types de données. Ces informations sont utiles si vous avez un fournisseur client développé à l’aide d' [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outils antérieurs à Native Client.  
  
#### <a name="columns-rowset"></a>Ensemble de lignes COLUMNS  
 Les valeurs de colonnes suivantes sont retournées pour les types date/heure :  
  
|Type de colonne|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|Date|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8, 10..16|16, 20.. 32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|38, 42.. 54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|52, 56.. 68|NULL|  
  
#### <a name="procedure_parameters-rowset"></a>Ensemble de lignes PROCEDURE_PARAMETERS  
 Les valeurs de colonnes suivantes sont retournées pour les types date/heure :  
  
|Type de colonne|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|Date|DBTYPE_WSTR|10|20|Date|  
|time|DBTYPE_WSTR|8, 10..16|16, 20.. 32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|DATETIME|  
|datetime2|DBTYPE_WSTR|19, 21.. 27|38, 42.. 54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26, 28.. 34|52, 56.. 68|datetimeoffset|  
  
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
 En cas de connexion à un serveur d’une version [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]antérieure à, toute tentative d’utiliser les nouveaux noms de type de serveur (par exemple, avec ICommandWithParameters :: SetParameterInfo ou ITableDefinition :: CreateTable) se traduira par DB_E_BADTYPENAME.  
  
 Si de nouveaux types sont liés pour des paramètres ou des résultats sans l'utilisation d'un nom de type, et si le nouveau type est utilisé pour spécifier le type serveur implicitement ou s'il n'existe pas de conversion valide du type serveur en type client, DB_E_ERRORSOCCURRED est retourné ; par ailleurs, DBBINDSTATUS_UNSUPPORTED_CONVERSION est défini en tant qu'état de liaison pour l'accesseur utilisé au moment de l'exécution.  
  
 S'il existe une conversion cliente prise en charge du type de mémoire tampon en type serveur pour la version du serveur de la connexion, tous les types de mémoires tampons clients peuvent être utilisés. Dans ce contexte, le type de *serveur* correspond au type spécifié par ICommandWithParameters :: SetParameterInfo ou implicite par le type de mémoire tampon si ICommandWithParameters :: SetParameterInfo n’a pas été appelé. En d'autres termes, DBTYPE_DBTIME2 et DBTYPE_DBTIMESTAMPOFFSET peuvent être utilisés avec des serveurs de bas niveau, ou lorsque DataTypeCompatibility=80, si la conversion cliente vers un type serveur pris en charge réussit. Bien entendu, si le type serveur est incorrect, une erreur peut toujours être signalée par le serveur lorsque ce dernier ne peut pas effectuer de conversion implicite vers le type serveur effectif.  
  
## <a name="ssprop_init_datatypecompatibility-behavior"></a>Comportement de SSPROP_INIT_DATATYPECOMPATIBILITY  
 Lorsque SSPROP_INIT_DATATYPECOMPATIBILITY a la valeur SSPROPVAL_DATATYPECOMPATIBILITY_SQL2000, les nouveaux types de date/heure et les métadonnées associées apparaissent aux clients tels qu’ils apparaissent pour les clients de niveau supérieur, comme décrit dans [copie en bloc des modifications pour les types de date et d’heure améliorés &#40;OLE DB et ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
## <a name="comparability-for-irowsetfind"></a>Comparabilité pour IRowsetFind  
 Tous les opérateurs de comparaison sont autorisés pour les nouveaux types date/heure, car ils apparaissent sous forme de types chaîne et non sous forme de types date/heure.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations de la date et de l’heure &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
