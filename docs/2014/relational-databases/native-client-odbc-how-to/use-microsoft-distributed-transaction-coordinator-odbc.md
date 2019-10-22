---
title: Utiliser Microsoft Distributed Transaction Coordinator (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 425f9fc0b7637aab1869130a2830c2f3c134fe7d
ms.sourcegitcommit: 82a1ad732fb31d5fa4368c6270185c3f99827c97
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688702"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Utiliser Microsoft Distributed Transaction Coordinator (ODBC)
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>Pour mettre à jour plusieurs serveurs SQL en utilisant MS DTC  
  
1.  Connectez-vous à MS DTC en utilisant la fonction MS DTC OLE DtcGetTransactionManager. Pour plus d'informations sur MS DTC, consultez Microsoft Distributed Transaction Coordinator.  
  
2.  Appelez SQL DriverConnect une fois pour chaque connexion Microsoft SQL Server que vous souhaitez établir.  
  
3.  Appelez la fonction MS DTC OLE ITransactionDispenser::BeginTransaction pour commencer une transaction MS DTC et obtenir un objet Transaction qui représente la transaction.  
  
4.  Appelez [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) une ou plusieurs fois pour chaque connexion ODBC que vous souhaitez inscrire dans la transaction MS DTC. Le deuxième paramètre [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) doit être SQL_ATTR_ENLIST_IN_DTC et le troisième paramètre doit être l’objet Transaction (obtenu à l’Étape 3).  
  
5.  Appelez [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) une fois pour chaque serveur SQL Server à mettre à jour.  
  
6.  Appelez la fonction MS DTC OLE ITransaction::Commit pour valider la transaction MS DTC. L'objet Transaction n'est plus valide.  
  
 Pour effectuer une série de transactions MS DTC, répétez les Étapes 3 à 6.  
  
 Pour libérer la référence à l'objet Transaction, appelez la fonction MS DTC OLE ITransaction::Return.  
  
 Pour utiliser une connexion ODBC avec une transaction MS DTC, puis utiliser la même connexion avec une transaction SQL Server locale, appelez [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) avec SQL_DTC_DONE.  
  
> [!NOTE]  
>  Vous pouvez également appeler [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) puis [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) pour chaque SQL Server au lieu de les appeler comme suggéré précédemment aux Étapes 4 et 5.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de &#40;transactions ODBC&#41;](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
