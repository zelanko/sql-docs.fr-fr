---
title: Transactions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: rothja
ms.author: jroth
ms.openlocfilehash: 1067820e80f9c7a4e1af2c8a14c85bc9dbfdd6aa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85017607"
---
# <a name="transactions"></a>Transactions
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client implémente la prise en charge des transactions locales. Le consommateur peut utiliser des transactions distribuées ou coordonnées à l'aide de Microsoft Distributed Transaction Coordinator (MS DTC). Pour les consommateurs qui requièrent un contrôle des transactions qui s’étend sur plusieurs sessions, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client peut joindre des transactions initiées et gérées par MS DTC.  
  
 Par défaut, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client utilise un mode de transaction AutoCommit, où chaque action discrète sur une session de consommateur comprend une transaction complète sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mode de validation automatique du fournisseur OLE DB Native Client est local, et les transactions de validation automatique ne s’étendent jamais sur plus d’une seule session.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose l’interface **ITransactionLocal** , ce qui permet au consommateur d’utiliser des transactions de démarrage explicite et implicite sur une connexion unique à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client ne prend pas en charge les transactions locales imbriquées.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Prise en charge des transactions locales](supporting-local-transactions.md)  
  
-   [Prise en charge des transactions distribuées](supporting-distributed-transactions.md)  
  
-   [Niveaux d'isolation &#40;OLE DB&#41;](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
