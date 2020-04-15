---
title: Prise en charge des transactions locales | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8533747bbe5ccb79a06b10a754c4af45ab241843
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280151"
---
# <a name="supporting-local-transactions"></a>Prise en charge des transactions locales
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Une session délimite la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] portée des transactions d’une transaction locale de fournisseur de DB OLE de fournisseur de clients autochtones. Lorsque, sous la direction d’un consommateur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE du client autochtone soumet une demande à un exemple connecté de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la demande constitue une unité de travail pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE du client autochtone. Les transactions locales enveloppent toujours une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou plusieurs unités de travail sur une seule session de fournisseur de DB OLE de client autochtone.  
  
 En utilisant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le mode autocommit du fournisseur de fournisseur Native Client OLE DB par défaut, une seule unité de travail est traitée comme la portée d’une transaction locale. Une seule unité participe à la transaction locale. Lorsqu’une session est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée, le fournisseur de DB OLE de native Client commence une transaction pour la session. Une fois que l'unité de travail a été exécutée avec succès, le travail est validé. En cas d'échec, tout travail commencé est annulé et l'erreur est signalée au consommateur. Dans les deux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cas, le fournisseur de DB OLE de client autochtone entame une nouvelle transaction locale pour la session afin que tous les travaux se déroulent dans le cadre d’une transaction.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de fournisseurs Native Client OLE DB peut diriger un contrôle plus précis sur la portée des transactions locales en utilisant l’interface **ITransactionLocal.** Lorsqu’une session de consommateur démarre une transaction, toutes les unités de travail de la session entre le point de départ de la transaction et les appels éventuels de la méthode **Commit** ou **Abort** sont traités comme une unité atomique. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone commence implicitement une transaction lorsqu’il est dirigé par le consommateur. Si le consommateur ne demande pas la rétention, la session revient au comportement parent du niveau de la transaction, soit le plus généralement le mode de validation automatique.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB prend en charge **ITransactionLocal::StartTransaction** paramètres comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*isoLevel*[in]|Niveau d'isolation à utiliser avec cette transaction. Dans le domaine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des transactions locales, le fournisseur de DB OLE de native Client prend en charge ce qui suit :<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> Remarque : Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures, ISOLATIONLEVEL_SNAPSHOT est valide pour l’argument *isoLevel*, que le suivi des versions soit activé ou non pour la base de données. Cependant, une erreur se produit si l'utilisateur essaie d'exécuter une instruction et que le suivi des versions n'est pas activé et/ou que la base de données n'est pas en lecture seule. De plus, l’erreur XACT_E_ISOLATIONLEVEL se produit si ISOLATIONLEVEL_SNAPSHOT est spécifié comme *isoLevel* lors de la connexion à une version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieure à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client renvoie une erreur pour toute valeur autre que zéro.|  
|*pOtherOptions*[in]|Si ce n’est pas NULL, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE Native Client demande l’objet d’options à partir de l’interface. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB retourne XACT_E_NOTIMEOUT si le membre *ulTimeout* de l’objet d’options n’est pas nul. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone ignore la valeur du membre *szDescription.*|  
|*pulTransactionLevel*[out]|Si ce n’est pas NULL, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE du client autochtone retourne le niveau imbriqué de la transaction.|  
  
 Pour les transactions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locales, le fournisseur native Client OLE DB implémente **ITransaction::Abort** paramètres comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pboidReason*[in]|Ignoré s'il est défini. Peut être égal à NULL en toute sécurité.|  
|*fRetaining*[in]|Lorsque la valeur est TRUE, une nouvelle transaction est commencée implicitement pour la session. La transaction doit être validée ou terminée par le consommateur. Lorsque FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de DB OLE native De client retourne en mode autocommit pour la session.|  
|*fAsync*[in]|L’avorte asynchrone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas pris en charge par le fournisseur de DB OLE de client autochtone. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone retourne XACT_E_NOTSUPPORTED si la valeur n’est pas FALSE.|  
  
 Pour les transactions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locales, le fournisseur de DB OLE native Client implémente **ITransaction::Commit** parameters as follows.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*fRetaining*[in]|Lorsque la valeur est TRUE, une nouvelle transaction est commencée implicitement pour la session. La transaction doit être validée ou terminée par le consommateur. Lorsque FALSE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de DB OLE native De client retourne en mode autocommit pour la session.|  
|*grfTC*[in]|Les retours asynchrones et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] phase 1 ne sont pas pris en charge par le fournisseur de DB OLE de client autochtone. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone retourne XACT_E_NOTSUPPORTED pour n’importe quelle valeur autre que XACTTC_SYNC.|  
|*grfRM*[in]|Doit être égal à 0.|  
  
 Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensembles de rames du fournisseur de DB OLE de client autochtone sur la session sont conservés sur une opération locale de validation ou d’interruption en fonction des valeurs des propriétés en rangée DBPROP_ABORTPRESERVE et DBPROP_COMMITPRESERVE. Par défaut, ces propriétés sont à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la fois VARIANT_FALSE et tous les ensembles de fournisseurs de fournisseurs de fournisseurs OLE DB de client autochtone sur la session sont perdus à la suite d’une interruption ou d’une opération de validation.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB ne met pas en œuvre l’interface **ITransactionObject.** La tentative d'un consommateur pour extraire une référence sur l'interface retourne E_NOINTERFACE.  
  
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
 [Transactions](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
 [Utilisation de l’isolement de capture instantanée](../../relational-databases/native-client/features/working-with-snapshot-isolation.md)  
  
  
