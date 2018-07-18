---
title: Ensemble de lignes LINKEDSERVERS (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60930ce7a43066c9041dfdaa92e0c4be254d78ae
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422398"
---
# <a name="linkedservers-rowset-ole-db"></a>Ensemble de lignes LINKEDSERVERS (OLE DB)
  Le **LINKEDSERVERS** ensemble de lignes énumère les sources de données d’organisation qui peuvent participer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les requêtes distribuées.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des ensembles de lignes de schéma &#40;OLE DB&#41;](schema-rowset-support-ole-db.md)  
  
  
