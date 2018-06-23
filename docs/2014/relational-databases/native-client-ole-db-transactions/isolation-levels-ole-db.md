---
title: Niveaux d’isolation (OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6a83ec8d81a3c9e07c36c3973735c3a62746bd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152805"
---
# <a name="isolation-levels-ole-db"></a>Niveaux d'isolation (OLE DB)
  Les clients [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent contrôler les niveaux d'isolation des transactions pour une connexion. Pour contrôler le niveau d’isolation des transactions, la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur de fournisseur OLE DB Native Client utilise :  
  
-   Propriété DBPROPSET_SESSION DBPROP_SESS_AUTOCOMMITISOLEVELS pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mode de validation automatique de valeur par défaut de fournisseur OLE DB Native Client.  
  
     Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valeur par défaut du fournisseur OLE DB Native Client pour le niveau est DBPROPVAL_TI_READCOMMITTED.  
  
-   Le *isoLevel* paramètre de la **ITransactionLocal::StartTransaction** méthode pour les transactions de validation manuelle locales.  
  
-   Le *isoLevel* paramètre de la **ITransactionDispenser::BeginTransaction** méthode pour coordonnées MS DTC des transactions distribuées.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autorise l'accès en lecture seule au niveau d'isolation de lecture erronée. Tous les autres niveaux restreignent la concurrence en appliquant des verrous aux objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Comme le client a besoin de niveaux d'accès concurrentiel supérieurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applique des restrictions supérieures sur l'accès concurrentiel aux données. Pour maintenir le niveau le plus élevé d’accès concurrentiel aux données, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client doit contrôler intelligemment ses demandes pour les niveaux d’accès concurrentiel spécifique.  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] a introduit le niveau d'isolement d'instantané. Pour plus d’informations, consultez [Working with Snapshot Isolation](../native-client/features/working-with-snapshot-isolation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions](transactions.md)  
  
  