---
title: Prise en charge des colonnes éparses (OLE DB) | Microsoft Docs
description: En savoir plus sur le support de OLE DB Driver pour SQL Server pour les colonnes éparses, qui sont des colonnes optimisées pour le stockage de valeurs Null.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f4d96c2d28df216097bb6abe77bcea1982b65e6
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860034"
---
# <a name="sparse-columns-support-ole-db"></a>Prise en charge des colonnes éparses (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cette rubrique fournit des informations sur la prise en charge des colonnes éparses par le fournisseur OLE DB Driver pour SQL Server. Pour obtenir plus d'informations sur les colonnes éparses, consultez [Prise en charge des colonnes éparses dans OLE DB Driver pour SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md). Pour consulter un exemple, voir [Afficher les métadonnées de colonne et de catalogue pour les colonnes éparses &#40;OLE DB&#41;](../../oledb/ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).  
  
## <a name="ole-db-statement-metadata"></a>Métadonnées d'instruction OLE DB  
 À partir de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], une nouvelle valeur d'indicateur DBCOLUMNFLAGS, DBCOLUMNFLAGS_SS_ISCOLUMNSET, est disponible. Cette valeur doit être définie pour les colonnes qui sont des valeurs **column_set**. L’indicateur DBCOLUMNFLAGS peut être récupéré via le paramètre *dwFlags* de IColumnsInfo::GetColumnsInfo et la colonne DBCOLUMN_FLAGS de l’ensemble de lignes retourné par IColumnsRowset::GetColumnsRowset.  
  
## <a name="ole-db-catalog-metadata"></a>Métadonnées de catalogue OLE DB  
 Deux colonnes supplémentaires spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ont été ajoutées à DBSCHEMA_COLUMNS.  
  
|Nom de la colonne|Type de données|Valeur/commentaires|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|Si la colonne est une colonne éparse, la valeur est VARIANT_TRUE ; sinon, VARIANT_FALSE.|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|Si la colonne est la colonne **column_set** éparse, la valeur est VARIANT_TRUE ; sinon, VARIANT_FALSE.|  
  
 Deux ensembles de lignes de schéma supplémentaires ont également été ajoutés. Ces ensembles de lignes ont la même structure que DBSCHEMA_COLUMNS mais retournent un contenu différent. DBSCHEMA_COLUMNS_EXTENDED retourne toutes les colonnes, indépendamment de l’appartenance à **column_set**. DBSCHEMA_SPARSE_COLUMN_SET retourne seulement les colonnes qui sont membres du **column_set** épars.  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>Comportement OLE DB de DataTypeCompatibility  
 Le comportement de **DataTypeCompatibility=80** (dans la chaîne de connexion) est cohérent par rapport à un client [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], comme suit :  
  
-   Les nouveaux ensembles de lignes de schéma ne sont pas visibles, et il n'y a pas de lignes pour eux dans l'ensemble de lignes d'ensembles de lignes de schéma.  
  
-   Les nouvelles colonnes de l'ensemble de lignes COLUMNS ne sont pas visibles.  
  
-   DBCOLUMNFLAGS_SS_ISCOLUMNSET n’est pas défini pour les colonnes de **column_set**.  
  
-   DBCOMPUTEMODE_NOTCOMPUTED est défini pour les colonnes de **column_set**.  
  
## <a name="ole-db-support-for-sparse-columns"></a>Prise en charge OLE DB des colonnes éparses  
 Les interfaces OLE DB suivantes ont été modifiées dans OLE DB Driver pour SQL Server pour prendre en charge les colonnes éparses :  
  
|Type ou fonction membre|Description|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|Une nouvelle valeur d’indicateur DBCOLUMNFLAGS, DBCOLUMNFLAGS_SS_ISCOLUMNSET, est définie pour les colonnes de **column_set** dans *dwFlags*.<br /><br /> DBCOLUMNFLAGS_WRITE est défini pour les colonnes de **column_set**.|  
|IColumsRowset::GetColumnsRowset|Une nouvelle valeur d’indicateur DBCOLUMNFLAGS, DBCOLUMNFLAGS_SS_ISCOLUMNSET, est définie pour les colonnes de **column_set** dans DBCOLUMN_FLAGS.<br /><br /> DBCOLUMN_COMPUTEMODE est défini sur DBCOMPUTEMODE_DYNAMIC pour les colonnes de **column_set**.|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS retourne deux nouvelles colonnes : SS_IS_COLUMN_SET et SS_IS_SPARSE.<br /><br /> DBSCHEMA_COLUMNS retourne seulement les colonnes qui ne sont pas membres d’un **column_set**.<br /><br /> Deux nouveaux ensembles de lignes de schéma ont été ajoutés : DBSCHEMA_COLUMNS_EXTENDED retourne toutes les colonnes, indépendamment du caractère épars de l’appartenance à **column_set**. DBSCHEMA_SPARSE_COLUMN_SET retourne seulement les colonnes qui sont membres d’un **column_set**. Ces nouveaux ensembles de lignes ont les mêmes colonnes et restrictions que DBSCHEMA_COLUMNS.|  
|IDBSchemaRowset::GetSchemas|IDBSchemaRowset::GetSchemas inclut les GUID des nouveaux ensembles de lignes DBSCHEMA_COLUMNS_EXTENDED et DBSCHEMA_SPARSE_COLUMN_SET dans la liste des ensembles de lignes de schéma disponibles.|  
|ICommand::Execute|Si **select \* from** *table* est utilisé, il retourne toutes les colonnes qui ne sont pas membres du **column_set** épars, plus une colonne XML qui contient les valeurs de toutes les colonnes non Null membres du **column_set** épars, le cas échéant.|  
|IOpenRowset::OpenRowset|IOpenRowset::OpenRowset retourne un ensemble de lignes avec les mêmes colonnes que ICommand::Execute, avec une requête **select \*** sur la même table.|  
|ITableDefinition|Il n’y a aucune modification de cette interface pour les colonnes éparses ou les colonnes d’un **column_set**. Les applications qui doivent effectuer des modifications de schéma doivent exécuter le [!INCLUDE[tsql](../../../includes/tsql-md.md)] approprié directement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
