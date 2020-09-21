---
title: Prise en charge des transactions locales (pilote OLE DB)
description: Découvrez comment OLE DB Driver pour SQL Server prend en charge des transactions locales et comment utiliser ITransactionLocal pour un contrôle plus précis de l’étendue de la transaction locale.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- OLE DB Driver for SQL Server, transactions
- local transactions [OLE DB]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5923c9f475a20fe31963b907f9e7cc76ef68bb04
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861893"
---
# <a name="supporting-local-transactions"></a>Prise en charge des transactions locales
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Une session délimite l'étendue de transaction pour une transaction locale du fournisseur OLE DB Driver pour SQL Server. Lorsque, à l'initiative d'un consommateur, le fournisseur OLE DB Driver pour SQL Server soumet une demande à une instance connectée de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la demande constitue une unité de travail pour le fournisseur OLE DB Driver pour SQL Server. Les transactions locales encapsulent toujours une ou plusieurs unités de travail sur une seule session de fournisseur OLE DB Driver pour SQL Server.  
  
 À l’aide du mode de validation automatique par défaut du pilote OLE DB pour SQL Server, une même unité de travail est traitée comme étendue d’une transaction locale. Une seule unité participe à la transaction locale. Quand une session est créée, le fournisseur OLE DB Driver pour SQL Server commence une transaction pour la session. Une fois que l'unité de travail a été exécutée avec succès, le travail est validé. En cas d'échec, tout travail commencé est annulé et l'erreur est signalée au consommateur. Dans l’un et l’autre cas, le pilote OLE DB pour SQL Server commence une nouvelle transaction locale pour la session, afin que tout le travail soit effectué au sein d’une transaction.  
  
 Le consommateur du pilote OLE DB pour SQL Server peut obtenir un contrôle plus précis sur l’étendue de la transaction locale en utilisant l’interface **ITransactionLocal**. Lorsqu’une session de consommateur démarre une transaction, toutes les unités de travail de la session entre le point de départ de la transaction et les appels éventuels de la méthode **Commit** ou **Abort** sont traités comme une unité atomique. Le fournisseur OLE DB Driver pour SQL Server commence implicitement une transaction lorsque le consommateur le lui demande. Si le consommateur ne demande pas la rétention, la session revient au comportement parent du niveau de la transaction, soit le plus généralement le mode de validation automatique.  
  
 Le fournisseur OLE DB Driver pour SQL Server prend en charge les paramètres **ITransactionLocal::StartTransaction** comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*isoLevel*[in]|Niveau d'isolation à utiliser avec cette transaction. Dans les transactions locales, OLE DB Driver pour SQL Server prend en charge les éléments suivants :<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Remarque : Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et versions ultérieures, ISOLATIONLEVEL_SNAPSHOT est valide pour l’argument *isoLevel*, que le suivi des versions soit activé ou non pour la base de données. Cependant, une erreur se produit si l'utilisateur essaie d'exécuter une instruction et que le suivi des versions n'est pas activé et/ou que la base de données n'est pas en lecture seule. De plus, l’erreur XACT_E_ISOLATIONLEVEL se produit si ISOLATIONLEVEL_SNAPSHOT est spécifié comme *isoLevel* lors de la connexion à une version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieure à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|Le fournisseur OLE DB Driver pour SQL Server retourne une erreur pour toute valeur autre que zéro.|  
|*pOtherOptions*[in]|Si la valeur est différente de NULL, le fournisseur OLE DB Driver pour SQL Server demande l'objet d'options de l'interface. Le fournisseur OLE DB Driver pour SQL Server retourne XACT_E_NOTIMEOUT si le membre *ulTimeout* de l'objet d'options est différent de zéro. Le fournisseur OLE DB Driver pour SQL Server ignore la valeur du membre *szDescription*.|  
|*pulTransactionLevel*[out]|Si la valeur est différente de NULL, le fournisseur OLE DB Driver pour SQL Server retourne le niveau imbriqué de la transaction.|  
  
 Pour les transactions locales, le fournisseur OLE DB Driver pour SQL Server implémente les paramètres **ITransaction::Abort** comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pboidReason*[in]|Ignoré s'il est défini. Peut être égal à NULL en toute sécurité.|  
|*fRetaining*[in]|Lorsque la valeur est TRUE, une nouvelle transaction est commencée implicitement pour la session. La transaction doit être validée ou terminée par le consommateur. Lorsque la valeur est FALSE, le fournisseur OLE DB Driver pour SQL Server retourne au mode de validation automatique pour la session.|  
|*fAsync*[in]|L'abandon asynchrone n'est pas pris en charge par le fournisseur OLE DB Driver pour SQL Server. Le fournisseur OLE DB Driver pour SQL Server retourne XACT_E_NOTSUPPORTED si la valeur n'est pas FALSE.|  
  
 Pour les transactions locales, le fournisseur OLE DB Driver pour SQL Server implémente les paramètres **ITransaction::Commit** comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*fRetaining*[in]|Lorsque la valeur est TRUE, une nouvelle transaction est commencée implicitement pour la session. La transaction doit être validée ou terminée par le consommateur. Lorsque la valeur est FALSE, le fournisseur OLE DB Driver pour SQL Server retourne au mode de validation automatique pour la session.|  
|*grfTC*[in]|Les retours asynchrones et en une seule phase ne sont pas pris en charge par le fournisseur OLE DB Driver pour SQL Server. Le fournisseur OLE DB Driver pour SQL Server retourne XACT_E_NOTSUPPORTED pour toute valeur autre que XACTTC_SYNC.|  
|*grfRM*[in]|Doit être égal à 0.|  
  
 Les ensembles de lignes du pilote OLE DB pour SQL Server de la session sont conservés lors d’une opération de validation ou d’abandon, selon les valeurs des propriétés d’ensemble de lignes DBPROP_ABORTPRESERVE et DBPROP_COMMITPRESERVE. Par défaut, ces propriétés ont toutes les deux la valeur VARIANT_FALSE, et tous les ensembles de lignes du pilote OLE DB pour SQL Server de la session sont perdus après une opération d’abandon ou de validation.  
  
 Le fournisseur OLE DB Driver pour SQL Server n'implémente pas l'interface **ITransactionObject**. La tentative d'un consommateur pour extraire une référence sur l'interface retourne E_NOINTERFACE.  
  
 L’exemple suivant utilise **ITransactionLocal**.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
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
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions](../../oledb/ole-db-transactions/transactions.md)   
 [Utilisation du niveau d’isolement de capture instantanée](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
