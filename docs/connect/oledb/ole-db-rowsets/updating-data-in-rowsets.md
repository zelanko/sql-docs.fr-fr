---
title: Mise à jour des données dans les ensembles de lignes | Documents Microsoft
description: Mise à jour des données dans les ensembles de lignes à l’aide du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
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
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dd1941aed59e16497f081b7d6029a8a3a3582b2f
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="updating-data-in-rowsets"></a>Mise à jour des données dans les ensembles de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour les mises à jour de SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] données lorsqu’un consommateur met à jour un ensemble de lignes modifiable qui contient les données. Un ensemble de lignes modifiable est créé lorsque le consommateur demande pris en charge la **IRowsetChange** ou **IRowsetUpdate** interface.  
  
 Tous les pilote OLE DB pour une utilisation d’ensembles de lignes modifiable SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les curseurs pour prendre en charge l’ensemble de lignes. La propriété d'ensemble de lignes DBPROP_LOCKMODE modifie le comportement du contrôle concurrentiel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des curseurs et détermine le comportement de l'extraction de lignes d'un ensemble de lignes et la génération d'erreurs d'intégrité des données dans les ensembles de lignes pouvant être mis à jour.  
  
 Le pilote OLE DB pour SQL Server prend en charge la synchronisation de lignes avant ou après une mise à jour.  
  
> [!NOTE]  
>  IRowChange::SetColumns permet de définir les valeurs d'une ou de plusieurs colonnes nommées d'un objet ligne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mise à jour des données dans les curseurs SQL Server](../../oledb/ole-db-rowsets/updating-data-in-sql-server-cursors.md)  
  
-   [Resynchronisation des lignes](../../oledb/ole-db-rowsets/updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
