---
title: "Mise à jour des données dans les ensembles de lignes | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5d70cbc3743b1ba0ded077b810c0af7a4af81cab
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="updating-data-in-rowsets"></a>Mise à jour des données dans les ensembles de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mises à jour du fournisseur OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données lorsqu’un consommateur met à jour un ensemble de lignes modifiable qui contient les données. Un ensemble de lignes modifiable est créé lorsque le consommateur demande pris en charge la **IRowsetChange** ou **IRowsetUpdate** interface.  
  
 Tous les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent des ensembles de lignes modifiable par le fournisseur OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseurs pour prendre en charge l’ensemble de lignes. La propriété d'ensemble de lignes DBPROP_LOCKMODE modifie le comportement du contrôle concurrentiel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des curseurs et détermine le comportement de l'extraction de lignes d'un ensemble de lignes et la génération d'erreurs d'intégrité des données dans les ensembles de lignes pouvant être mis à jour.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge la synchronisation de lignes avant ou après une mise à jour.  
  
> [!NOTE]  
>  IRowChange::SetColumns permet de définir les valeurs d'une ou de plusieurs colonnes nommées d'un objet ligne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mise à jour des données dans les curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Resynchronisation des lignes](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
