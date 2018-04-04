---
title: Ensemble de lignes LINKEDSERVERS (OLE DB) | Documents Microsoft
description: Ensemble de lignes LINKEDSERVERS (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1d3090ad79cf5a8a41812fa5a51ca2ddc076ae99
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Schema Rowsets - LINKEDSERVERS Rowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le **LINKEDSERVERS** ensemble de lignes énumère les sources de données d’organisation qui peuvent participer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les requêtes distribuées.  
  
 L'ensemble de lignes **LINKEDSERVERS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type| Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Nom d'un serveur lié.|  
|SVR_PRODUCT|DBTYPE_WSTR|Fabricant ou autre nom identifiant le type de banque de données représenté par le nom du serveur lié.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Nom convivial du fournisseur OLE DB utilisé pour consommer les données du serveur.|  
|SVR_DATASOURCE|DBTYPE_WSTR|Chaîne OLE DB DBPROP_INIT_DATASOURCE utilisée pour acquérir une source de données à partir du fournisseur.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|Valeur OLE DB DBPROP_INIT_PROVIDERSTRING utilisée pour acquérir une source de données à partir du fournisseur.|  
|SVR_LOCATION|DBTYPE_WSTR|Chaîne OLE DB DBPROP_INIT_LOCATION utilisée pour acquérir une source de données à partir du fournisseur.|  
  
 L'ensemble de lignes est trié sur SRV_NAME et une restriction unique est prise en charge sur SRV_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge du jeu de lignes de schéma &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
