---
title: Exécution de Transactions distribuées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa5c6b607fa7523380950ecd89f9cae20ffc6f21
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63228953"
---
# <a name="performing-distributed-transactions"></a>Exécution de transactions distribuées
  Microsoft Distributed Transaction Coordinator (MS DTC) permet aux applications d'étendre des transactions à deux instances ou plus de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il permet également aux applications de participer à des transactions gérées par des gestionnaires de transactions qui respectent la norme XA DTP d'Open Group.  
  
 Normalement, toutes les commandes de gestion des transactions sont envoyées par l'intermédiaire du pilote ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client au serveur. L’application démarre une transaction en appelant [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) avec le mode de validation automatique désactivé. L’application effectue ensuite les mises à jour comprenant la transaction et appelle [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) avec option le SQL_COMMIT ou SQL_ROLLBACK.  
  
 Lorsque vous utilisez MS DTC, cependant, MS DTC devient le Gestionnaire de transactions et l’application n’utilise plus **SQLEndTran**.  
  
 Une fois inscrit dans une transaction distribuée, puis inscrit dans une deuxième transaction distribuée, le pilote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC fait défection dans la transaction distribuée d'origine et s'inscrit dans la nouvelle transaction. Pour plus d’informations, consultez [de référence du programmeur DTC](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de Transactions &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
