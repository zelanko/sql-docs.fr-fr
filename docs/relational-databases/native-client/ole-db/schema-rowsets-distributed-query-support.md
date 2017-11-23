---
title: "Prise en charge de la requête dans les ensembles de lignes de schéma distribuées | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da9ecaba4dd896f93d7a8e035dd51ae00c429eb8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="schema-rowsets---distributed-query-support"></a>Ensembles de lignes de schéma - prise en charge des requêtes distribuées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Pour prendre en charge [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed des requêtes, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif **IDBSchemaRowset** interface retourne des métadonnées sur les serveurs liés.  
  
 Si la propriété DBPROPSET_SQLSERVERSESSION SSPROP_QUOTEDCATALOGNAMES est VARIANT_TRUE, un identificateur entre guillemets peut être spécifié pour le nom de catalogue (par exemple "my.catalog"). Lors de la restriction de sortie d’ensemble de lignes de schéma par catalogue, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client reconnaît un nom en deux parties contenant le nom de catalogue et de serveur lié. Pour les ensembles de lignes de schéma dans le tableau ci-dessous, en spécifiant un nom de catalogue en deux parties en tant que *linked_server***.** *catalogue* limite la sortie au catalogue applicable du serveur lié nommé.  
  
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
>  Pour restreindre un ensemble de lignes de schéma à tous les catalogues à partir d’un serveur lié, utilisez la syntaxe *linked_server* (où le point de séparation est la partie de la spécification du nom). Cette syntaxe équivaut à spécifier NULL pour la restriction du nom de catalogue ; elle est également utilisée lorsque le serveur lié indique une source de données qui ne prend pas en charge les catalogues.  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client définit l’ensemble de lignes de schéma LINKEDSERVERS et retourne une liste des sources de données OLE DB inscrits en tant que serveurs liés.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge du jeu de lignes de schéma &#40; OLE DB &#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)   
 [Ensemble de lignes LINKEDSERVERS &#40; OLE DB &#41;](../../../relational-databases/native-client/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  
