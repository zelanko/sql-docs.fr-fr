---
description: Métadonnées-date et heure et ensembles de lignes de schéma dans SQL Server Native Client
title: Ensembles de lignes de date et d’heure et de schéma
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], schema rowsets
ms.assetid: 8c35e86f-0597-4ef4-b2b8-f643e53ed4c2
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f3aa326a76a752ac7e85bd852051663f46b8c4a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486718"
---
# <a name="metadata---date-and-time-and-schema-rowsets-in-sql-server-native-client"></a>Métadonnées-date et heure et ensembles de lignes de schéma dans SQL Server Native Client
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Cette rubrique fournit des informations sur l'ensemble de lignes COLUMNS et l'ensemble de lignes PROCEDURE_PARAMETERS. Ces informations concernent les améliorations apportées aux date et heure OLE DB pour [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="columns-rowset"></a>Ensemble de lignes COLUMNS  
 Les valeurs de colonnes suivantes sont retournées pour les types date/heure :  
  
|Type de colonne|DATA_TYPE|COLUMN_FLAGS, DBCOLUMFLAGS_SS_ISVARIABLESCALE|DATETIME_PRECISION|  
|-----------------|----------------|------------------------------------------------------|-------------------------|  
|Date|DBTYPE_DBDATE|Désactiver|0|  
|time|DBTYPE_DBTIME2|Définissez|0..7|  
|smalldatetime|DBTYPE_DBTIMESTAMP|Désactiver|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|Désactiver|3|  
|datetime2|DBTYPE_DBTIMESTAMP|Définissez|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|Définissez|0..7|  
  
 Dans COLUMN_FLAGS, DBCOLUMNFLAGS_ISFIXEDLENGTH a toujours la valeur True pour les types date/heure et les indicateurs suivants ont toujours la valeur False :  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Les indicateurs restants (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE et DBCOLUMNFLAGS_WRITEUNKNOWN) peuvent être définis, en fonction de la manière dont la colonne est définie.  
  
 Un nouvel indicateur, DBCOLUMNFLAGS_SS_ISVARIABLESCALE, est fourni dans COLUMN_FLAGS pour permettre à une application de déterminer le type de serveur de colonnes, où DATA_TYPE représente DBTYPE_DBTIMESTAMP. DATETIME_PRECISION doit aussi être utilisé pour identifier le type de serveur.  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE est valide seulement en cas de connexion à un serveur [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou ultérieur. DBCOLUMNFLAGS_SS_ISFIXEDSCALE est non défini en cas de connexion à des serveurs de bas niveau.  
  
## <a name="procedure_parameters-rowset"></a>Ensemble de lignes PROCEDURE_PARAMETERS  
 DATA_TYPE contient les mêmes valeurs que l'ensemble de lignes de schéma COLUMNS et TYPE_NAME contient le type de serveur.  
  
 Une nouvelle colonne, SS_DATETIME_PRECISION, a été ajoutée pour retourner la précision du type comme dans la colonne DATETIME_PRECISION, semblable à l'ensemble de lignes COLUMNS.  
  
## <a name="provider_types-rowset"></a>Ensemble de lignes PROVIDER_TYPES  
 Les lignes suivantes sont retournées pour les types date/heure :  
  
|Type -><br /><br /> Colonne|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_DBDATE|DBTYPE_DBTIME2|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMPOFFSET|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|scale|NULL|NULL|scale|scale|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|Date|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|0|NULL|NULL|0|0|  
|MAXIMUM_SCALE|NULL|7|NULL|NULL|7|7|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE à moins que l'un des éléments suivants ne soit vrai :<br /><br /> Client connecté à un serveur de bas niveau.<br /><br /> La propriété de connexion de compatibilité de type de données spécifie un niveau de compatibilité égal à 80.|VARIANT_TRUE à moins que l'un des éléments suivants ne soit vrai :<br /><br /> Client connecté à un serveur de bas niveau.<br /><br /> La propriété de connexion de compatibilité de type de données spécifie un niveau de compatibilité égal à 80.|VARIANT_TRUE|  
|IS_FIXEDLENGTH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
  
 Comme OLE DB ne définit MINIMUM_SCALE et MAXIMUM_SCALE que pour les types numériques et décimaux, l'utilisation par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client de ces colonnes pour les types time, datetime2 et datetimeoffset n'est pas standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Métadonnées &#40;OLE DB&#41;](https://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
  
  
