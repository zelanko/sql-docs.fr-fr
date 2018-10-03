---
title: Exécution de Transactions distribuées | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4b3839b9300cda1d20860965bc740ca2ce9c068d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765977"
---
# <a name="performing-transactions---distributed-transactions"></a>Exécution de transactions - Transactions distribuées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft Distributed Transaction Coordinator (MS DTC) permet aux applications d'étendre des transactions à deux instances ou plus de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il permet également aux applications de participer à des transactions gérées par des gestionnaires de transactions qui respectent la norme XA DTP d'Open Group.  
  
 Normalement, toutes les commandes de gestion des transactions sont envoyées par l'intermédiaire du pilote ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client au serveur. L’application démarre une transaction en appelant [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec le mode de validation automatique désactivé. L’application effectue ensuite les mises à jour comprenant la transaction et appelle [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) avec option le SQL_COMMIT ou SQL_ROLLBACK.  
  
 Lorsque vous utilisez MS DTC, cependant, MS DTC devient le Gestionnaire de transactions et l’application n’utilise plus **SQLEndTran**.  
  
 Une fois inscrit dans une transaction distribuée, puis inscrit dans une deuxième transaction distribuée, le pilote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC fait défection dans la transaction distribuée d'origine et s'inscrit dans la nouvelle transaction. Pour plus d’informations, consultez [de référence du programmeur DTC](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de Transactions &#40;ODBC&#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
