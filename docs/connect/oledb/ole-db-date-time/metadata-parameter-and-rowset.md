---
title: Métadonnées de paramètre et d'ensemble de lignes (pilote OLE DB)
description: Métadonnées de paramètre et d’ensemble de lignes
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- metadata [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: a3356134c542cf90c194924a8fbfc44b357c7123
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244896"
---
# <a name="metadata---parameter-and-rowset"></a>Métadonnées - Paramètres et ensembles de lignes
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cet article fournit des informations sur le type et les membres de type suivants en rapport avec les améliorations de date et d’heure OLE DB.  
  
-   Structure DBBINDING  
  
-   **ICommandWithParameters::GetParameterInfo**  
  
-   **ICommandWithParameters::SetParameterInfo**  
  
-   **IColumnsRowset::GetColumnsRowset**  
  
-   **IColumnsInfo::GetColumnInfo**  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Les informations suivantes sont retournées dans la structure DBPARAMINFO via *prgParamInfo* :  
  
|Type de paramètre|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|Date|DBTYPE_DBDATE|6|10|0|Désactiver|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Définissez|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Désactiver|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Désactiver|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Définissez|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Définissez|  
  
 Notez que, dans certains cas, les plages de valeurs ne sont pas continues. Cela est dû à l'ajout d'une virgule décimale lorsque la précision fractionnaire est supérieure à zéro.  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE est valide seulement en cas de connexion à un serveur [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (ou ultérieur). DBPARAMFLAGS_SS_ISVARIABLESCALE n’est jamais défini en cas de connexion à des serveurs de bas niveau.  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>ICommandWithParameters::SetParameterInfo et types de paramètre implicites  
 Les informations fournies dans la structure DBPARAMBINDINFO doivent respecter les conditions suivantes :  
  
|*pwszDataSourceType*<br /><br /> (spécifique au fournisseur)|*pwszDataSourceType*<br /><br /> (OLE DB générique)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|Ignoré|  
|Date|DBTYPE_DBDATE|6|Ignoré|  
||DBTYPE_DBTIME|10|Ignoré|  
|time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|Ignoré|  
|DATETIME||16|Ignoré|  
|datetime2 ou DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 Le paramètre *bPrecision* est ignoré.  
  
 « DBPARAMFLAGS_SS_ISVARIABLESCALE » est ignoré lors de l'envoi de données au serveur. Les applications peuvent forcer l’utilisation de types TDS (Tabular Data Stream) hérités en utilisant les noms de types spécifiques au fournisseur « **datetime** » et « **smalldatetime** ». En cas de connexion à des serveurs [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (ou ultérieur), le format « **datetime2** » est utilisé et une conversion serveur implicite se produit si nécessaire, quand le nom de type est « **datetime2** » ou « DBTYPE_DBTIMESTAMP ». *bScale* est ignoré si les noms de types spécifiques au fournisseur « **DateTime** » ou « **smalldatetime** » sont utilisés. Dans le cas contraire, les applications doivent s’assurer que *bScale* est correctement défini. Les applications mises à niveau à partir de MDAC et OLE DB Driver pour SQL Server à partir de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] qui utilisent « DBTYPE_DBTIMESTAMP » échouent si elles ne définissent pas *bScale* correctement. En cas de connexion à instances de serveur antérieures à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], une valeur *bScale* autre que 0 ou 3 avec « DBTYPE_DBTIMESTAMP » est une erreur, et E_FAIL est retourné.  
  
 Quand ICommandWithParameters::SetParameterInfo n’est pas appelé, le fournisseur implique le type de serveur à partir du type de liaison, tel que spécifié dans IAccessor::CreateAccessor, comme suit :  
  
|Type de liaison|*pwszDataSourceType*<br /><br /> (spécifique au fournisseur)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|Date|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 **IColumnsRowset::GetColumnsRowset** retourne les colonnes suivantes :  
  
|Type de colonne|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS, DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|Date|DBTYPE_DBDATE|6|10|0|Désactiver|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Définissez|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Désactiver|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Désactiver|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Définissez|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Définissez|  
  
 Dans DBCOLUMN_FLAGS, DBCOLUMNFLAGS_ISFIXEDLENGTH a toujours la valeur True pour les types date/heure et les indicateurs suivants sont toujours False :  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Les indicateurs restants (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE et DBCOLUMNFLAGS_WRITEUNKNOWN) peuvent être définis, en fonction de la manière dont la colonne est définie et de la requête réelle.  
  
 Un nouvel indicateur DBCOLUMNFLAGS_SS_ISVARIABLESCALE est fourni dans DBCOLUMN_FLAGS pour permettre à une application de déterminer le type de serveur de colonnes, où DBCOLUMN_TYPE représente DBTYPE_DBTIMESTAMP. DBCOLUMN_SCALE ou DBCOLUMN_DATETIMEPRECISION doit également être utilisé pour identifier le type de serveur.  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE est valide seulement en cas de connexion à un serveur [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (ou ultérieur). DBCOLUMNFLAGS_SS_ISVARIABLESCALE est non défini en cas de connexion à des serveurs de bas niveau.  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 La structure DBCOLUMNINFO retourne les informations suivantes :  
  
|Type de paramètre|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|Date|DBTYPE_DBDATE|6|10|0|Désactiver|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|Définissez|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Désactiver|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Désactiver|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Définissez|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Définissez|  
  
 Dans *dwFlags*, DBCOLUMNFLAGS_ISFIXEDLENGTH a toujours la valeur True pour les types date/heure et les indicateurs suivants sont toujours False :  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 Les indicateurs restants (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE et DBCOLUMNFLAGS_WRITEUNKNOWN) peuvent être définis.  
  
 Un nouvel indicateur, DBCOLUMNFLAGS_SS_ISVARIABLESCALE, est fourni dans *dwFlags* pour permettre à une application de déterminer le type de serveur des colonnes, où *wType* est DBTYPE_DBTIMESTAMP. *bScale* doit aussi être utilisé pour identifier le type de serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des types de données pour les améliorations de date et heure OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
  
  
