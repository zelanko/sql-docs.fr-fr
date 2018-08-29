---
title: Resynchronisation des lignes | Microsoft Docs
description: Resynchronisation des lignes à l’aide de OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: dc7d722f4d4b97cd4242195d49ff7d5290c52f24
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017460"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Mise à jour des données dans les ensembles de lignes - Resynchronisation des lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server prend en charge **IRowsetResynch** sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] curseur pris en charge les ensembles de lignes uniquement. **IRowsetResynch** n’est pas disponible à la demande. Le consommateur doit demander l'interface avant d'ouvrir l'ensemble de lignes.  
  
## <a name="see-also"></a> Voir aussi  
 [Mise à jour des données dans les ensembles de lignes](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
