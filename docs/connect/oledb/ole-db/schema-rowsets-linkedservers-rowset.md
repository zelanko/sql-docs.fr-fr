---
title: Ensemble de lignes LINKEDSERVERS (OLE DB) | Microsoft Docs
description: Ensemble de lignes LINKEDSERVERS (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9fe4ab1b6fd245bdb7ac0bd08acb0564742e1188
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694943"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Ensembles de lignes de schéma - Ensemble de lignes LINKEDSERVERS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L’ensemble de lignes **LINKEDSERVERS** énumère les sources de données de l’organisation qui peuvent participer aux requêtes distribuées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 L'ensemble de lignes **LINKEDSERVERS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Nom d'un serveur lié.|  
|SVR_PRODUCT|DBTYPE_WSTR|Fabricant ou autre nom identifiant le type de banque de données représenté par le nom du serveur lié.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Nom convivial du fournisseur OLE DB utilisé pour consommer les données du serveur.|  
|SVR_DATASOURCE|DBTYPE_WSTR|Chaîne OLE DB DBPROP_INIT_DATASOURCE utilisée pour acquérir une source de données à partir du fournisseur.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|Valeur OLE DB DBPROP_INIT_PROVIDERSTRING utilisée pour acquérir une source de données à partir du fournisseur.|  
|SVR_LOCATION|DBTYPE_WSTR|Chaîne OLE DB DBPROP_INIT_LOCATION utilisée pour acquérir une source de données à partir du fournisseur.|  
  
 L'ensemble de lignes est trié sur SRV_NAME et une restriction unique est prise en charge sur SRV_NAME.  
  
## <a name="see-also"></a> Voir aussi  
 [Prise en charge des ensembles de lignes de schéma &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)  
  
  
