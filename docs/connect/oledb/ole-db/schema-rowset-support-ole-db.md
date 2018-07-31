---
title: Prise en charge de l’ensemble de lignes de schéma (OLE DB) | Microsoft Docs
description: Prise en charge des ensembles de lignes de schéma (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- OLE DB Driver for SQL Server, schema rowsets
- rowsets [OLE DB], schema
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a90779203502c8df145a1b25f628a7657d065edb
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107075"
---
# <a name="schema-rowset-support-ole-db"></a>Prise en charge des ensembles de lignes de schéma (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server prend également en charge le retour des informations de schéma d’un serveur lié lors du traitement de requêtes distribuées [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Bien que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge les synonymes, les métadonnées de synonymes n’est pas retournée par le pilote OLE DB pour SQL Server.  
  
 Les tableaux suivants répertorient les ensembles de lignes de schéma et les colonnes de restriction prises en charge par le pilote OLE DB pour SQL Server.  
  
|Ensemble de lignes de schéma|Colonnes de restriction|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMN_PRIVILEGES|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|DBSCHEMA_COLUMNS|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME<br /><br /> Les colonnes supplémentaires suivantes sont propres à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :<br /><br /> COLUMN_LCID désigne l'ID de paramètres régionaux du classement. COLUMN_LCID affiche une valeur identique à un LCID Windows.<br /><br /> COLUMN_COMPFLAGS définit les comparaisons prises en charge pour le classement. Le format de données est le même que DBPROB_FINDCOMPAREOPS.<br /><br /> COLUMN_SORTID désigne le style de tri de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour le classement.<br /><br /> COLUMN_TDSCOLLATION désigne le classement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de la colonne.<br /><br /> IS_COMPUTED est défini sur VARIANT_TRUE si la colonne est une colonne calculée et sur VARIANT_FALSE autrement.|  
|DBSCHEMA_FOREIGN_KEYS|Toutes les restrictions sont prises en charge.<br /><br /> PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|DBSCHEMA_INDEXES|Les restrictions 1, 2, 3 et 5 sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TABLE_NAME|  
|DBSCHEMA_PRIMARY_KEYS|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Toutes les restrictions sont prises en charge.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|DBSCHEMA_PROCEDURES|Les restrictions 1, 2, et 3 sont prises en charge.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME<br /><br /> DBSCHEMA_PROCEDURES retourne uniquement des procédures que l'utilisateur actuel peut exécuter ou pour lesquelles l'autorisation VIEW DEFINITION lui a été accordée.|  
|DBSCHEMA_PROVIDER_TYPES|Toutes les restrictions sont prises en charge.<br /><br /> DATA_TYPE BEST_MATCH|  
|DBSCHEMA_SCHEMATA|Toutes les restrictions sont prises en charge.<br /><br /> CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|DBSCHEMA_STATISTICS|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_TABLE_CONSTRAINTS|Toutes les restrictions sont prises en charge.<br /><br /> CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|DBSCHEMA_TABLE_PRIVILEGES|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|DBSCHEMA_TABLES|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|DBSCHEMA_TABLES_INFO|Toutes les restrictions sont prises en charge.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma](../../oledb/ole-db/schema-rowsets-distributed-query-support.md)  
  
 [Ensemble de lignes LINKEDSERVERS &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Programmation du pilote OLE DB pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [Utilisation de types définis par l’utilisateur](../../oledb/features/using-user-defined-types.md)  
  
  
