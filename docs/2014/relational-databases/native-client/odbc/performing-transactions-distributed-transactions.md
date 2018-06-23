---
title: Exécution de Transactions distribuées | Documents Microsoft
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
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d6c03f674722e817fc8c16dd712572c3236e73d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044499"
---
# <a name="performing-distributed-transactions"></a>Exécution de transactions distribuées
  Microsoft Distributed Transaction Coordinator (MS DTC) permet aux applications d'étendre des transactions à deux instances ou plus de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il permet également aux applications de participer à des transactions gérées par des gestionnaires de transactions qui respectent la norme XA DTP d'Open Group.  
  
 Normalement, toutes les commandes de gestion des transactions sont envoyées par l'intermédiaire du pilote ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client au serveur. L’application démarre une transaction en appelant [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) avec le mode de validation automatique désactivé. L’application effectue ensuite les mises à jour comprenant la transaction et appelle [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) avec l’option de le SQL_COMMIT ou SQL_ROLLBACK.  
  
 Lorsque vous utilisez MS DTC, MS DTC devient toutefois, le Gestionnaire de transactions et de l’application n’utilise plus **SQLEndTran**.  
  
 Une fois inscrit dans une transaction distribuée, puis inscrit dans une deuxième transaction distribuée, le pilote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC fait défection dans la transaction distribuée d'origine et s'inscrit dans la nouvelle transaction. Pour plus d’informations, consultez [de référence du programmeur DTC](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de Transactions &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  