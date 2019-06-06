---
title: BeginTrans, CommitTrans et RollbackTrans événements (ADO) | Microsoft Docs
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
manager: jroth
ms.openlocfilehash: 8239a5f9069212b9413216bc3535e3c90e2d5316
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696352"
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>BeginTransComplete, CommitTransComplete et RollbackTransComplete, événements (ADO)
Ces événements seront appelées après l’opération associée sur le [connexion](../../../ado/reference/ado-api/connection-object-ado.md) fin de l’exécution de l’objet.  
  
-   **BeginTransComplete** est appelée après la [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) opération.  
  
-   **CommitTransComplete** est appelée après la [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) opération.  
  
-   **RollbackTransComplete** est appelée après la [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *TransactionLevel*  
 Un **Long** valeur qui contient le nouveau niveau de transaction de la **BeginTrans** qui a provoqué cet événement.  
  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Il décrit l’erreur qui s’est produite si la valeur, il n’est **contraire**; sinon, elle n’est pas définie.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état. Lorsqu’un de ces événements est appelé, ce paramètre est défini **adStatusOK** si l’opération qui a provoqué l’événement a réussi, ou à **contraire** si l’opération a échoué.  
  
 Ces événements peuvent empêcher les notifications ultérieures en définissant ce paramètre sur **adStatusUnwantedEvent** avant le retour de l’événement.  
  
 *pConnection*  
 Le **connexion** de l’objet pour lequel cet événement s’est produite.  
  
## <a name="remarks"></a>Notes  
 Dans Visual C++, plusieurs **connexions** peuvent partager le même événement, méthode de gestion. La méthode utilise retourné **connexion** objet afin de déterminer l’objet qui a provoqué l’événement.  
  
 Si le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) propriété est définie sur **adXactCommitRetaining** ou **adXactAbortRetaining**, une nouvelle transaction démarre après la validation ou la restauration d’une transaction. Utilisez le **BeginTransComplete** événement à ignorer tout, mais le premier événement de début de transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [BeginTrans, CommitTrans et RollbackTrans, méthodes-exemple (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [BeginTrans, CommitTrans et RollbackTrans, méthodes (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
