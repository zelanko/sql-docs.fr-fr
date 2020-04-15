---
title: Ensemble de lignes LINKEDSERVERS (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 130cfb23f1d0a1eefa90868cf4c59f4c6d3f1e8e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304950"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>Ensembles de lignes de schéma - Ensemble de lignes LINKEDSERVERS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  L’ensemble de lignes **LINKEDSERVERS** énumère les sources de données de l’organisation qui peuvent participer aux requêtes distribuées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 L'ensemble de lignes **LINKEDSERVERS** contient les colonnes suivantes.  
  
|Nom de la colonne|Indicateur de type|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Nom d'un serveur lié.|  
|SVR_PRODUCT|DBTYPE_WSTR|Fabricant ou autre nom identifiant le type de banque de données représenté par le nom du serveur lié.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Nom convivial du fournisseur OLE DB utilisé pour consommer les données du serveur.|  
|SVR_DATASOURCE|DBTYPE_WSTR|Chaîne OLE DB DBPROP_INIT_DATASOURCE utilisée pour acquérir une source de données à partir du fournisseur.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|Valeur OLE DB DBPROP_INIT_PROVIDERSTRING utilisée pour acquérir une source de données à partir du fournisseur.|  
|SVR_LOCATION|DBTYPE_WSTR|Chaîne OLE DB DBPROP_INIT_LOCATION utilisée pour acquérir une source de données à partir du fournisseur.|  
  
 L'ensemble de lignes est trié sur SRV_NAME et une restriction unique est prise en charge sur SRV_NAME.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des ensembles de lignes de schéma &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
  
