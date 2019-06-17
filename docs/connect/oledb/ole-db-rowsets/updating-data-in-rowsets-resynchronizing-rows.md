---
title: Resynchronisation des lignes | Microsoft Docs
description: Resynchronisation des lignes à l’aide de OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 39119e4444b22fdbeacbf9c1e1b6db22bbf31a79
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803803"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Mise à jour des données dans les ensembles de lignes - Resynchronisation des lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server prend en charge **IRowsetResynch** sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] curseur pris en charge les ensembles de lignes uniquement. **IRowsetResynch** n’est pas disponible à la demande. Le consommateur doit demander l'interface avant d'ouvrir l'ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des données dans les ensembles de lignes](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
