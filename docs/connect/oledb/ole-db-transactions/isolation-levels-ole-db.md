---
title: Niveaux d’isolation (OLE DB) | Documents Microsoft
description: Niveaux d'isolation (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e0ecb2f1f790eb38afaed514cc8881a9047dbd41
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="isolation-levels-ole-db"></a>Niveaux d'isolation (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les clients [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent contrôler les niveaux d'isolation des transactions pour une connexion. Pour contrôler le niveau d’isolation de la transaction, le pilote OLE DB pour le consommateur de SQL Server utilise :  
  
-   Propriété DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS pour le pilote OLE DB pour le mode de validation automatique par défaut de SQL Server.  
  
     Le pilote OLE DB pour SQL Server par défaut pour le niveau est DBPROPVAL_TI_READCOMMITTED.  
  
-   Le *isoLevel* paramètre de la **ITransactionLocal::StartTransaction** méthode pour les transactions de validation manuelle locales.  
  
-   Le *isoLevel* paramètre de la **ITransactionDispenser::BeginTransaction** méthode pour coordonnées MS DTC des transactions distribuées.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autorise l'accès en lecture seule au niveau d'isolation de lecture erronée. Tous les autres niveaux restreignent la concurrence en appliquant des verrous aux objets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Comme le client a besoin de niveaux d'accès concurrentiel supérieurs, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applique des restrictions supérieures sur l'accès concurrentiel aux données. Pour garantir un niveau élevé d’accès concurrentiel aux données, le pilote OLE DB pour le consommateur de SQL Server doit contrôler intelligemment ses demandes pour les niveaux d’accès concurrentiel spécifique.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] a introduit le niveau d'isolement d'instantané. Pour plus d’informations, consultez [Working with Snapshot Isolation](../../oledb/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions](../../oledb/ole-db-transactions/transactions.md)  
  
  
