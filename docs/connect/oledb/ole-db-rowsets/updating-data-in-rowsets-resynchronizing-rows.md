---
title: Resynchronisation des lignes | Documents Microsoft
description: Resynchronisation des lignes à l’aide du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b59417b2d82f647ea428a782e20158da6b55b724
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Mise à jour des données dans les ensembles de lignes - resynchronisation des lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour SQL Server prend en charge **IRowsetResynch** sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] curseur pris en charge les ensembles de lignes uniquement. **IRowsetResynch** n’est pas disponible à la demande. Le consommateur doit demander l'interface avant d'ouvrir l'ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des données dans les ensembles de lignes](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
