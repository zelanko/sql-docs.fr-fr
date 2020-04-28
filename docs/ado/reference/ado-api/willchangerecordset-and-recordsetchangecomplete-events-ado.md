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
ms.openlocfilehash: dd4e2f1485c18ce1fecc76d4eb23aa4132d85329
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938688"
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>WillChangeRecordset et RecordsetChangeComplete, événements (ADO)
L’événement **WillChangeRecordset** est appelé avant qu’une opération en attente modifie le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). L’événement **RecordsetChangeComplete** est appelé après la modification du **Recordset** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Reason*  
 Valeur [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) qui spécifie la raison de cet événement. Sa valeur peut être **adRsnRequery**, **adRsnResynch**, **adRsnClose**, **adRsnOpen**.  
  
 *adStatus*  
 Valeur d’état [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 Lorsque **WillChangeRecordset** est appelé, ce paramètre a la valeur **adStatusOK** si l’opération à l’origine de l’événement a réussi. Elle a la valeur **adStatusCantDeny** si cet événement ne peut pas demander l’annulation de l’opération en attente.  
  
 Quand **RecordsetChangeComplete** est appelé, ce paramètre a la valeur **adStatusOK** si l’opération qui a provoqué l’événement a réussi, **adStatusErrorsOccurred** si l’opération a échoué, ou **adStatusCancel** si l’opération associée à l’événement **WillChangeRecordset** précédemment accepté a été annulée.  
  
 Avant le retour de **WillChangeRecordset** , définissez ce paramètre sur **adStatusCancel** pour demander l’annulation de l’opération en attente, ou définissez ce paramètre sur adStatusUnwantedEvent pour empêcher les notifications suivantes.  
  
 Avant que **WillChangeRecordset** ou **RecordsetChangeComplete** ne retourne, définissez ce paramètre sur **adStatusUnwantedEvent** pour empêcher les notifications suivantes.  
  
 *pError*  
 Objet d' [erreur](../../../ado/reference/ado-api/error-object.md) . Il décrit l’erreur qui s’est produite si la valeur de *adStatus* est **adStatusErrorsOccurred**; dans le cas contraire, il n’est pas défini.  
  
 *pRecordset*  
 Objet **Recordset** . **Jeu d’enregistrements** pour lequel cet événement s’est produit.  
  
## <a name="remarks"></a>Notes  
 Un événement **WillChangeRecordset** ou **RecordsetChangeComplete** peut se produire en raison de la [rerequête](../../../ado/reference/ado-api/requery-method.md) de l’ensemble **d’enregistrements** ou des méthodes [ouvertes](../../../ado/reference/ado-api/open-method-ado-recordset.md) .  
  
 Si le fournisseur ne prend pas en charge les signets, une notification d’événement **RecordsetChange** se produit chaque fois que de nouvelles lignes sont extraites du fournisseur. La fréquence de cet événement dépend de la propriété **RecordsetCacheSize** .  
  
 Vous devez définir le paramètre **adStatus** sur **adStatusUnwantedEvent** pour chaque valeur de **adReason** possible afin d’arrêter complètement la notification d’événement pour tout événement qui comprend un paramètre **adReason** .  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
