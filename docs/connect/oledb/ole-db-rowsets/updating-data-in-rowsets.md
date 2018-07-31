---
title: La mise à jour des données dans les ensembles de lignes | Microsoft Docs
description: La mise à jour des données dans les ensembles de lignes à l’aide de OLE DB Driver pour SQL Server
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
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 20484bce71d0e776b4090f743c65e3a78d655a70
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108811"
---
# <a name="updating-data-in-rowsets"></a>Mise à jour des données dans les ensembles de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server met à jour les données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsqu’un consommateur met à jour un ensemble de lignes modifiable contenant ces données. Un ensemble de lignes modifiable est créé lorsque le consommateur demande la prise en charge de l’interface **IRowsetChange** ou **IRowsetUpdate**.  
  
 Tous les pilote OLE DB pour une utilisation d’ensembles de lignes modifiable SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les curseurs pour prendre en charge l’ensemble de lignes. La propriété d'ensemble de lignes DBPROP_LOCKMODE modifie le comportement du contrôle concurrentiel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des curseurs et détermine le comportement de l'extraction de lignes d'un ensemble de lignes et la génération d'erreurs d'intégrité des données dans les ensembles de lignes pouvant être mis à jour.  
  
 Le pilote OLE DB pour SQL Server prend en charge la synchronisation de lignes avant ou après une mise à jour.  
  
> [!NOTE]  
>  IRowChange::SetColumns permet de définir les valeurs d'une ou de plusieurs colonnes nommées d'un objet ligne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mise à jour des données dans les curseurs SQL Server](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Resynchronisation des lignes](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
