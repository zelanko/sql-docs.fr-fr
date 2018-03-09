---
title: Utilisez Microsoft Distributed Transaction Coordinator (ODBC) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a1f982500e38722032f1edb9ffda70eee8b12251
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Utiliser Microsoft Distributed Transaction Coordinator (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>Pour mettre à jour plusieurs serveurs SQL en utilisant MS DTC  
  
1.  Connectez-vous à MS DTC en utilisant la fonction MS DTC OLE DtcGetTransactionManager. Pour plus d'informations sur MS DTC, consultez Microsoft Distributed Transaction Coordinator.  
  
2.  Appelez SQL DriverConnect une fois pour chaque connexion Microsoft® SQL Server™ que vous souhaitez établir.  
  
3.  Appelez la fonction MS DTC OLE ITransactionDispenser::BeginTransaction pour commencer une transaction MS DTC et obtenir un objet Transaction qui représente la transaction.  
  
4.  Appelez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) une ou plusieurs fois pour chaque connexion ODBC que vous souhaitez inscrire dans la transaction MS DTC. Le deuxième paramètre [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) doit être SQL_ATTR_ENLIST_IN_DTC et le troisième paramètre doit être l’objet Transaction (obtenu à l’Étape 3).  
  
5.  Appelez [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) une fois pour chaque serveur SQL Server à mettre à jour.  
  
6.  Appelez la fonction MS DTC OLE ITransaction::Commit pour valider la transaction MS DTC. L'objet Transaction n'est plus valide.  
  
 Pour effectuer une série de transactions MS DTC, répétez les Étapes 3 à 6.  
  
 Pour libérer la référence à l'objet Transaction, appelez la fonction MS DTC OLE ITransaction::Return.  
  
 Pour utiliser une connexion ODBC avec une transaction MS DTC, puis utiliser la même connexion avec une transaction SQL Server locale, appelez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec SQL_DTC_DONE.  
  
> [!NOTE]  
>  Vous pouvez également appeler [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) puis [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) pour chaque SQL Server au lieu de les appeler comme suggéré précédemment aux Étapes 4 et 5.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de Transactions &#40; ODBC &#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
