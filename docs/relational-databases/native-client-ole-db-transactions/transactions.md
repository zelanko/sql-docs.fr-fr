---
title: Transactions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d54dbe8e3df6e930ebd026e638d0a21f2f88f32e
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73772559"
---
# <a name="transactions"></a>Transactions
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le fournisseur d’OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client implémente la prise en charge des transactions locales. Le consommateur peut utiliser des transactions distribuées ou coordonnées à l'aide de Microsoft Distributed Transaction Coordinator (MS DTC). Pour les consommateurs qui requièrent un contrôle des transactions qui s’étend sur plusieurs sessions, le fournisseur de OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut joindre des transactions initiées et gérées par MS DTC.  
  
 Par défaut, le fournisseur de OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise un mode de transaction AutoCommit, où chaque action discrète sur une session de consommateur comprend une transaction complète sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le mode de validation automatique du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB est local, et les transactions de validation automatique ne s’étendent jamais sur une seule session.  
  
 Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB expose l’interface **ITransactionLocal** , ce qui permet au consommateur d’utiliser des transactions de démarrage explicite et implicite sur une connexion unique à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le fournisseur d’OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ne prend pas en charge les transactions locales imbriquées.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Prise en charge des transactions locales](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [Prise en charge des transactions distribuées](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [Niveaux &#40;d’isolement OLE DB&#41;](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
