---
title: IDBProperties (OLE DB) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d6bbf3fea3d9b2c80e441d2461266503d6edbd25
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  La spécification standard OLE DB permet aux fournisseurs de spécifier VT_EMPTY pour **DBPROPINFO::vValues**. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client retourne toujours VT_EMPTY lorsque vous appelez **IDBProperties::GetPropertyInfo** avec **DBPROPSET_ROWSETALL** pour récupérer les propriétés de l’ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40; OLE DB &#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
