---
title: BeginTrans, CommitTrans, RollbackTrans, événements (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CommitTransComplete
- Connection::BeginTransComplete
- Connection::RollbackTransComplete
- Connection::CommitTransComplete
- RollbackTransComplete
- BeginTransComplete
helpviewer_keywords:
- CommitTransComplete event [ADO]
- RollbackTransComplete event [ADO]
- BeginTransComplete event [ADO]
ms.assetid: ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 750e89e97eb916c7db23e71475b753a57a4d90e9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920448"
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>Événements BeginTransComplete, CommitTransComplete et RollbackTransComplete (ADO)
Ces événements sont appelés après la fin de l’exécution de l’opération associée sur l’objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
-   **BeginTransComplete** est appelé après l’opération [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) .  
  
-   **CommitTransComplete** est appelé après l’opération [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) .  
  
-   **RollbackTransComplete** est appelé après l’opération [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *TransactionLevel*  
 Valeur de **type long** qui contient le nouveau niveau de transaction du **BeginTrans** à l’origine de cet événement.  
  
 *pError*  
 Objet d' [erreur](../../../ado/reference/ado-api/error-object.md) . Il décrit l’erreur qui s’est produite si la valeur de EventStatusEnum est **adStatusErrorsOccurred**; dans le cas contraire, il n’est pas défini.  
  
 *adStatus*  
 Valeur d’état [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) . Lorsque l’un de ces événements est appelé, ce paramètre a la valeur **adStatusOK** si l’opération à l’origine de l’événement a réussi, ou à **adStatusErrorsOccurred** si l’opération a échoué.  
  
 Ces événements peuvent empêcher les notifications suivantes en affectant à ce paramètre la valeur **adStatusUnwantedEvent** avant le retour de l’événement.  
  
 *pConnection*  
 Objet de **connexion** pour lequel cet événement s’est produit.  
  
## <a name="remarks"></a>Notes  
 Dans Visual C++, plusieurs **connexions** peuvent partager la même méthode de gestion des événements. La méthode utilise l’objet de **connexion** retourné pour déterminer l’objet qui a provoqué l’événement.  
  
 Si la propriété [attributes](../../../ado/reference/ado-api/attributes-property-ado.md) a la valeur **adXactCommitRetaining** ou **adXactAbortRetaining**, une nouvelle transaction démarre après la validation ou la restauration d’une transaction. Utilisez l’événement **BeginTransComplete** pour ignorer tous les événements de début de transaction sauf le premier.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [BeginTrans, CommitTrans et RollbackTrans, exemples de méthodes (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Résumé du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [BeginTrans, CommitTrans et RollbackTrans, méthodes (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
