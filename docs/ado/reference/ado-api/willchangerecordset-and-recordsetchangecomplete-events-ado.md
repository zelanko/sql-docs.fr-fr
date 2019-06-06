---
title: WillChangeRecordset et RecordsetChangeComplete, événements (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::RecordsetChangeComplete
- RecordsetChangeComplete
- Recordset::WillChangeRecordset
- WillChangeRecordset
helpviewer_keywords:
- RecordsetChangeComplete event [ADO]
- WillChangeRecordset event [ADO]
ms.assetid: d5d44659-e0d9-46d9-a297-99c43555082f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c5ca84c5759523bf17c4e047b22cafbd48dce547
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66710065"
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>WillChangeRecordset et RecordsetChangeComplete, événements (ADO)
Le **WillChangeRecordset** événement est appelé avant qu’une opération en attente modifie la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Le **RecordsetChangeComplete** événement est appelé après le **Recordset** a changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *adReason*  
 Un [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) valeur qui spécifie la raison de cet événement. Sa valeur peut être **adRsnRequery**, **adRsnResynch**, **adRsnClose**, **adRsnOpen**.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état.  
  
 Lorsque **WillChangeRecordset** est appelée, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi. Il est défini sur **adStatusCantDeny** si cet événement ne peut pas demander l’annulation de l’opération en attente.  
  
 Lorsque **RecordsetChangeComplete** est appelée, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi, **contraire** si l’opération a échoué, ou **adStatusCancel** si l’opération associée précédemment acceptées **WillChangeRecordset** événement a été annulé.  
  
 Avant de **WillChangeRecordset** retourne, définissez ce paramètre sur **adStatusCancel** pour demander l’annulation de l’opération en attente ou de définir ce paramètre à adStatusUnwantedEvent pour éviter suivantes notifications.  
  
 Avant de **WillChangeRecordset** ou **RecordsetChangeComplete** retourne, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification.  
  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Il décrit l’erreur qui s’est produite si la valeur de *ne* est **contraire**; sinon, elle n’est pas définie.  
  
 *pRecordset*  
 Un **Recordset** objet. Le **Recordset** pour laquelle cet événement s’est produit.  
  
## <a name="remarks"></a>Notes  
 Un **WillChangeRecordset** ou **RecordsetChangeComplete** événement peut survenir en raison de la **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) ou [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthodes.  
  
 Si le fournisseur ne prend pas en charge les signets, un **RecordsetChange est générée** notification d’événement se produit chaque fois que les nouvelles lignes sont récupérées à partir du fournisseur. La fréquence de cet événement varie selon le **RecordsetCacheSize** propriété.  
  
 Vous devez définir le **ne** paramètre **adStatusUnwantedEvent** pour chaque possible **adReason** valeur permet d’arrêter complètement la notification d’événement pour tout événement qui inclut un **adReason** paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
