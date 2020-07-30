---
title: Prise en charge des ensembles de lignes de schéma (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- SQL Server Native Client OLE DB provider, schema rowsets
- rowsets [OLE DB], schema
ms.assetid: a75b4b69-b095-4690-9b31-a2b32a67489e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: faa764aae707ae785c7cfd1cb324427b9a941376
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243873"
---
# <a name="schema-rowset-support-in-sql-server-native-client-ole-db"></a>Prise en charge des ensembles de lignes de schéma dans SQL Server Native Client (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client prend également en charge le retour des informations de schéma à partir d’un serveur lié lors du traitement des [!INCLUDE[tsql](../../../includes/tsql-md.md)] requêtes distribuées.  
  
> [!NOTE]  
>  Bien que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prenne en charge les synonymes, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ne retourne pas les métadonnées de ces derniers.  
  
 Les tableaux suivants répertorient les ensembles de lignes de schéma et les colonnes de restriction prises en charge par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client.  
  
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
 [Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma](../../../relational-databases/native-client/ole-db/schema-rowsets-distributed-query-support.md)  
  
 [Ensemble de lignes LINKEDSERVERS &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utilisation des types définis par l'utilisateur](../../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
