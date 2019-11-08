---
title: Niveaux d’isolement (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4ddfe4bd9d8760fa561e7b0221f61413b3c6d111
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73761618"
---
# <a name="isolation-levels-ole-db"></a>Niveaux d'isolation (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les clients [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent contrôler les niveaux d'isolation des transactions pour une connexion. Pour contrôler le niveau d’isolation des transactions, le consommateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur utilise :  
  
-   DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS de propriétés pour le mode de validation automatique par défaut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du fournisseur OLE DB Native Client.  
  
     Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB par défaut pour le niveau est DBPROPVAL_TI_READCOMMITTED.  
  
-   Le paramètre *isoLevel* de la méthode **ITransactionLocal::StartTransaction** pour les transactions de validation manuelle locales.  
  
-   Le paramètre *isoLevel* de la méthode **ITransactionDispenser::BeginTransaction** pour les transactions distribuées coordonnées par MS DTC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autorise l'accès en lecture seule au niveau d'isolation de lecture erronée. Tous les autres niveaux restreignent la concurrence en appliquant des verrous aux objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Comme le client a besoin de niveaux d'accès concurrentiel supérieurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applique des restrictions supérieures sur l'accès concurrentiel aux données. Pour maintenir le niveau le plus élevé d’accès simultané aux données, le consommateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur doit contrôler intelligemment ses demandes de niveaux de concurrence spécifiques.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] a introduit le niveau d'isolement d'instantané. Pour plus d'informations, consultez [Working with Snapshot Isolation](../../relational-databases/native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
