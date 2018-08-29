---
title: Prise en charge des Transactions distribuées | Microsoft Docs
description: Transactions distribuées dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9486af5a9dbd4f607f376a5f916e35ace88be872
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028423"
---
# <a name="supporting-distributed-transactions"></a>Prise en charge des transactions distribuées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les consommateurs du pilote OLE DB pour SQL Server peuvent utiliser la méthode **ITransactionJoin::JoinTransaction** pour participer à une transaction distribuée coordonnée par MS DTC (Microsoft Distributed Transaction Coordinator).  
  
 MS DTC expose les objets COM qui permettent aux clients d'initialiser des transactions coordonnées et d'y participer sur plusieurs connexions à diverses banques de données. Pour lancer une transaction, le pilote OLE DB pour le consommateur SQL Server utilise MS DTC **ITransactionDispenser** interface. Le membre **BeginTransaction** de **ITransactionDispenser** retourne une référence sur un objet de transaction distribué. Cette référence est passée pour le pilote OLE DB pour SQL Server à l’aide **JoinTransaction**.  
  
 MS DTC prend en charge l'abandon et la validation asynchrones sur les transactions distribuées. Pour la notification sur l’état de transaction asynchrone, le consommateur implémente l’interface **ITransactionOutcomeEvents** et connecte l’interface à un objet de transaction MS DTC.  
  
 Pour les transactions distribuées, le pilote OLE DB pour SQL Server implémente les paramètres **ITransactionJoin::JoinTransaction** de la façon suivante :  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*punkTransactionCoord*|Pointeur vers un objet de transaction MS DTC.|  
|*IsoLevel*|Ignoré par OLE DB Driver pour SQL Server. Le niveau d'isolation pour les transactions coordonnées MS DTC est déterminé lorsque le consommateur acquiert un objet de transaction à partir de MS DTC.|  
|*IsoFlags*|Doit être égal à 0. Le pilote OLE DB pour SQL Server retourne XACT_E_NOISORETAIN si toute autre valeur est spécifiée par le consommateur.|  
|*POtherOptions*|Si ce n’est pas NULL, le pilote OLE DB pour SQL Server demande l’objet d’options à partir de l’interface. Le pilote OLE DB pour SQL Server retourne XACT_E_NOTIMEOUT si l’objet d’options *ulTimeout* membre n’est pas égal à zéro. Le pilote OLE DB pour SQL Server ignore la valeur de la *szDescription* membre.|  
  
 Cet exemple coordonne la transaction à l'aide de MS DTC.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Transactions](../../oledb/ole-db-transactions/transactions.md)  
  
  
