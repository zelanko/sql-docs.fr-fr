---
title: "WillMove et MoveComplete, événements (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset::MoveComplete
- WillMove
- MoveComplete
- Recordset::WillMove
helpviewer_keywords:
- MoveComplete event [ADO]
- WillMove event [ADO]
ms.assetid: 1a3d1042-4f30-4526-a0c7-853c242496db
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b4cf136ccd49b461578f7a34941465a54c4e4183
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="willmove-and-movecomplete-events-ado"></a>WillMove et MoveComplete, événements (ADO)
Le **WillMove** événement est appelé avant qu’une opération en attente modifie la position actuelle dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Le **MoveComplete** événement est appelé après la position actuelle dans le **Recordset** modifications.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *adReason*  
 Un [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) valeur qui spécifie la raison de cet événement. Sa valeur peut être **adRsnMoveFirst**, **adRsnMoveLast**, **adRsnMoveNext**, **adRsnMovePrevious**, **adRsnMove** , ou **adRsnRequery**.  
  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Elle décrit l’erreur qui s’est produite si la valeur de *ne* est **contraire**; sinon, le paramètre n’est pas défini.  
  
 *N'*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état.  
  
 Lorsque **WillMove** est appelée, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi. Il est défini sur **adStatusCantDeny** si cet événement ne peut pas demander l’annulation de l’opération en attente.  
  
 Lorsque **MoveComplete** est appelée, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi, ou pour **contraire** si le échoué de l’opération.  
  
 Avant de **WillMove** retourne, définissez ce paramètre sur **adStatusCancel** pour demander l’annulation de l’opération en attente, ou définissez ce paramètre sur **adStatusUnwantedEvent** Pour éviter toute notification.  
  
 Avant de **MoveComplete** retourne, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification.  
  
 *Connection*  
 A [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet. Le **Recordset** pour laquelle cet événement s’est produit.  
  
## <a name="remarks"></a>Notes  
 A **WillMove** ou **MoveComplete** événement peut se produire en raison de ce qui suit **Recordset** operations : [ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md), [déplacer](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), et [Requery](../../../ado/reference/ado-api/requery-method.md). Ces événements peuvent se produire en raison des propriétés suivantes : [filtre](../../../ado/reference/ado-api/filter-property.md), [Index](../../../ado/reference/ado-api/index-property.md), [signet](../../../ado/reference/ado-api/bookmark-property-ado.md), [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)et [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md). Ces événements se produisent également si un enfant **Recordset** a **Recordset** événements connectés et le parent **Recordset** est déplacé.  
  
 Vous devez définir le *ne* paramètre **adStatusUnwantedEvent** pour chaque possible *adReason* valeur afin d’arrêter complètement la notification d’événement pour tout événement qui inclut un *adReason* paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
