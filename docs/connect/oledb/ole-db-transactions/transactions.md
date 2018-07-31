---
title: Transactions | Microsoft Docs
description: Transactions dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 04be1dd71842471a05b3d0f46655f13a0113768f
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108681"
---
# <a name="transactions"></a>Transactions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server implémente la prise en charge de la transaction locale. Le consommateur peut utiliser des transactions distribuées ou coordonnées à l'aide de Microsoft Distributed Transaction Coordinator (MS DTC). Pour les consommateurs qui exigent un contrôle des transactions qui couvre plusieurs sessions, le pilote OLE DB pour SQL Server peut joindre des transactions lancées et gérées par MS DTC.  
  
 Par défaut, le pilote OLE DB pour SQL Server utilise un mode de validation automatique des transactions, dans lequel chaque action discrète dans une session de consommateur comprend une transaction complète sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le mode de validation automatique du pilote OLE DB pour SQL Server est local, et les transactions validées automatiquement ne couvrent jamais plus d’une session.  
  
 Le pilote OLE DB pour SQL Server expose l’interface **ITransactionLocal**, ce qui permet au consommateur d’utiliser explicitement et implicitement des transactions de démarrage sur une connexion unique à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le pilote OLE DB pour SQL Server ne prend pas en charge les transactions locales imbriquées.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Prise en charge des transactions locales](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Prise en charge des transactions distribuées](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Niveaux d’isolation &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
