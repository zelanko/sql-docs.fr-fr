---
title: Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma | Microsoft Docs
description: L’interface IDBSchemaRowset de OLE DB Driver pour SQL Server retourne des métadonnées sur des serveurs liés pour prendre en charge des requêtes distribuées SQL Server.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], OLE DB Driver for SQL Server
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61105b2e974cd111cd4f5dfd10e7f528cd04519a
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861568"
---
# <a name="schema-rowsets---distributed-query-support"></a>Ensembles de lignes de schéma - Prise en charge des requêtes distribuées
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Pour prendre en charge les requêtes distribuées de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l’interface **IDBSchemaRowset** du pilote OLE DB pour SQL Server retourne des métadonnées sur les serveurs liés.  
  
 Si la propriété DBPROPSET_SQLSERVERSESSION SSPROP_QUOTEDCATALOGNAMES est VARIANT_TRUE, un identificateur entre guillemets peut être spécifié pour le nom de catalogue (par exemple "my.catalog"). Lors de la restriction de la sortie des ensembles de lignes de schéma par catalogue, le pilote OLE DB pour SQL Server reconnaît un nom en deux parties contenant le serveur lié et le nom de catalogue. Pour les ensembles de lignes de schéma du tableau ci-dessous, le fait de spécifier un nom de catalogue en deux parties, comme _serveur\_lié_ **.** _catalogue_, a pour effet de restreindre la sortie au catalogue applicable du serveur lié nommé.  
  
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
>  Pour restreindre un ensemble de lignes de schéma à tous les catalogues d’un serveur lié, utilisez la syntaxe *serveur_lié* (le trait de soulignement fait partie de la spécification du nom). Cette syntaxe équivaut à spécifier NULL pour la restriction du nom de catalogue ; elle est également utilisée lorsque le serveur lié indique une source de données qui ne prend pas en charge les catalogues.  
 
 Le pilote OLE DB pour SQL Server définit l’ensemble de lignes de schéma LINKEDSERVERS et retourne une liste des sources de données OLE DB inscrites comme serveurs liés.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des ensembles de lignes de schéma &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)   
 [Ensemble de lignes LINKEDSERVERS &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
