---
title: Transactions (pilote OLE DB)
description: Découvrez comment OLE DB Driver pour SQL Server prend en charge les transactions locales. Utilisez Microsoft Distributed Transaction Coordinator pour les transactions distribuées.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e146dd9bc1f560cba4bf1902909dd6b8b317698f
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861843"
---
# <a name="transactions"></a>Transactions
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server implémente la prise en charge des transactions locales. Le consommateur peut utiliser des transactions distribuées ou coordonnées à l'aide de Microsoft Distributed Transaction Coordinator (MS DTC). Pour les consommateurs qui exigent un contrôle des transactions qui couvre plusieurs sessions, le pilote OLE DB pour SQL Server peut joindre des transactions lancées et gérées par MS DTC.  
  
 Par défaut, le pilote OLE DB pour SQL Server utilise un mode de validation automatique des transactions, dans lequel chaque action discrète dans une session de consommateur comprend une transaction complète sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le mode de validation automatique du pilote OLE DB pour SQL Server est local, et les transactions validées automatiquement ne couvrent jamais plus d’une session.  
  
 Le pilote OLE DB pour SQL Server expose l’interface **ITransactionLocal**, ce qui permet au consommateur d’utiliser explicitement et implicitement des transactions de démarrage sur une connexion unique à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. OLE DB Driver pour SQL Server ne prend pas en charge les transactions locales imbriquées.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Prise en charge des transactions locales](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Prise en charge des transactions distribuées](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Niveaux d'isolation &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
