---
title: BeginTrans, CommitTrans et RollbackTrans événements (ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1598b77bd0c9a205a587b61bff822dc810b70d78
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado"></a>BeginTransComplete, CommitTransComplete et RollbackTransComplete, événements (ADO)
Ces événements sont appelés après l’opération associée sur le [connexion](../../../ado/reference/ado-api/connection-object-ado.md) fin de l’exécution de l’objet.  
  
-   **BeginTransComplete** est appelée après le [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) opération.  
  
-   **CommitTransComplete** est appelée après le [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) opération.  
  
-   **RollbackTransComplete** est appelée après le [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BeginTransComplete TransactionLevel, pError, adStatus, pConnection  
CommitTransComplete pError, adStatus, pConnection  
RollbackTransComplete pError, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *TransactionLevel*  
 A **Long** valeur contenant le nouveau niveau de transaction de la **BeginTrans** qui a provoqué cet événement.  
  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Elle décrit l’erreur qui s’est produite si la valeur, il n’est **contraire**; sinon, elle n’est pas définie.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état. Lorsqu’un de ces événements est appelé, ce paramètre est défini **adStatusOK** si l’opération qui a provoqué l’événement a réussi, ou pour **contraire** si l’opération a échoué.  
  
 Ces événements peuvent empêcher les notifications ultérieures en définissant ce paramètre sur **adStatusUnwantedEvent** avant le retour de l’événement.  
  
 *pConnection*  
 Le **connexion** de l’objet pour laquelle cet événement s’est produit.  
  
## <a name="remarks"></a>Notes  
 Dans Visual C++, plusieurs **connexions** peuvent partager le même événement, méthode de gestion. La méthode utilise retourné **connexion** objet afin de déterminer l’objet qui a provoqué l’événement.  
  
 Si le [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) est définie sur **adXactCommitRetaining** ou **adXactAbortRetaining**, une nouvelle transaction démarre après la validation ou la restauration d’une transaction. Utilisez le **BeginTransComplete** pour ignorer tous les événements, mais le premier événement de début de transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [BeginTrans, CommitTrans et RollbackTrans, méthodes-exemple (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [BeginTrans, CommitTrans et RollbackTrans, méthodes (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)
