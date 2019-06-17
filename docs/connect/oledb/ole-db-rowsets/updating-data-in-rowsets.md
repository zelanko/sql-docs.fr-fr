---
title: La mise à jour des données dans les ensembles de lignes | Microsoft Docs
description: La mise à jour des données dans les ensembles de lignes à l’aide de OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, updating data
- OLE DB Driver for SQL Server, data updates
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 3e6a03d5bc379b620db06e0f1308058d647397e1
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803776"
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
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
