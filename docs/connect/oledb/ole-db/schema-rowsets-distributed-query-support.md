---
title: Prise en charge de la requête dans les ensembles de lignes de schéma distribuées | Microsoft Docs
description: Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma
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
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], OLE DB Driver for SQL Server
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 77960d1a5b38ef9ae66fe2705f38f10a739daa2a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031729"
---
# <a name="schema-rowsets---distributed-query-support"></a>Ensembles de lignes de schéma - Prise en charge des requêtes distribuées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Pour prendre en charge les requêtes distribuées de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l’interface **IDBSchemaRowset** du pilote OLE DB pour SQL Server retourne des métadonnées sur les serveurs liés.  
  
 Si la propriété DBPROPSET_SQLSERVERSESSION SSPROP_QUOTEDCATALOGNAMES est VARIANT_TRUE, un identificateur entre guillemets peut être spécifié pour le nom de catalogue (par exemple "my.catalog"). Lors de la restriction de la sortie des ensembles de lignes de schéma par catalogue, le pilote OLE DB pour SQL Server reconnaît un nom en deux parties contenant le serveur lié et le nom de catalogue. Pour les ensembles de lignes de schéma dans le tableau ci-dessous, la spécification d’un nom de catalogue en deux parties, comme *serveur_lié ***.*** catalogue* restreint la sortie au catalogue applicable du serveur lié nommé.  
  
|Ensemble de lignes de schéma|Restriction de catalogue|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMNS|TABLE_CATALOG|  
|DBSCHEMA_PRIMARY_KEYS|TABLE_CATALOG|  
|DBSCHEMA_TABLES|TABLE_CATALOG|  
|DBSCHEMA_FOREIGN_KEYS|PK_TABLE_CATALOG FK_TABLE_CATALOG|  
|DBSCHEMA_INDEXES|TABLE_CATALOG|  
|DBSCHEMA_COLUMN_PRIVILEGES|TABLE_CATALOG|  
|DBSCHEMA_TABLE_PRIVILEGES|TABLE_CATALOG|  
  
> [!NOTE]  
>  Pour restreindre un ensemble de lignes de schéma à tous les catalogues d’un serveur lié, utilisez la syntaxe *serveur_lié* (où le point séparateur fait partie de la spécification du nom). Cette syntaxe équivaut à spécifier NULL pour la restriction du nom de catalogue ; elle est également utilisée lorsque le serveur lié indique une source de données qui ne prend pas en charge les catalogues.  
  
 Le pilote OLE DB pour SQL Server définit l’ensemble de lignes de schéma LINKEDSERVERS et retourne une liste des sources de données OLE DB inscrites comme serveurs liés.  
  
## <a name="see-also"></a> Voir aussi  
 [Prise en charge des ensembles de lignes de schéma &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)   
 [Ensemble de lignes LINKEDSERVERS &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
