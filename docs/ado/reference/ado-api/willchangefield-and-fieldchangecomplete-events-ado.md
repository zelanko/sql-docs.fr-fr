---
title: WillChangeField et FieldChangeComplete, événements (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldChangeComplete
- Recordset::WillChangeField
- Recordset::FieldChangeComplete
- WillChangeField
helpviewer_keywords:
- WillChangeField event [ADO]
- fieldchangecomplete event [ADO]
ms.assetid: 3e49fb89-c45b-4d39-823e-3cc887c59b37
author: rothja
ms.author: jroth
ms.openlocfilehash: e4a4fb74e95bf0e1ba9dc9d0001b3d653f9294c1
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764490"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>WillChangeField et FieldChangeComplete, événements (ADO)
L’événement **WillChangeField** est appelé avant qu’une opération en attente modifie la valeur d’un ou plusieurs objets [Field](../../../ado/reference/ado-api/field-object.md) dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). L’événement **FieldChangeComplete** est appelé après la modification de la valeur d’un ou plusieurs objets **Field** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *cFields*  
 **Valeur de type long** qui indique le nombre d’objets **champ** dans les *champs*.  
  
 *Fields*  
 Pour **WillChangeField**, le paramètre *Fields* est un tableau de **variants** qui contient des objets **Field** avec les valeurs d’origine. Pour **FieldChangeComplete**, le paramètre *Fields* est un tableau de **variants** qui contient des objets **Field** avec les valeurs modifiées.  
  
 *pError*  
 Objet d' [erreur](../../../ado/reference/ado-api/error-object.md) . Il décrit l’erreur qui s’est produite si la valeur de *adStatus* est **adStatusErrorsOccurred**; dans le cas contraire, il n’est pas défini.  
  
 *adStatus*  
 Valeur d’état [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 Lorsque **WillChangeField** est appelé, ce paramètre a la valeur **adStatusOK** si l’opération à l’origine de l’événement a réussi. Elle a la valeur **adStatusCantDeny** si cet événement ne peut pas demander l’annulation de l’opération en attente.  
  
 Lorsque **FieldChangeComplete** est appelé, ce paramètre a la valeur **adStatusOK** si l’opération à l’origine de l’événement s’est déroulée correctement ou **adStatusErrorsOccurred** si l’opération a échoué.  
  
 Avant que **WillChangeField** retourne, définissez ce paramètre sur **adStatusCancel** pour demander l’annulation de l’opération en attente.  
  
 Avant que **FieldChangeComplete** ne retourne, définissez ce paramètre sur **adStatusUnwantedEvent** pour empêcher les notifications suivantes.  
  
 *pRecordset*  
 Objet **Recordset** . **Jeu d’enregistrements** pour lequel cet événement s’est produit.  
  
## <a name="remarks"></a>Remarques  
 Un événement **WillChangeField** ou **FieldChangeComplete** peut se produire lors de la définition de la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) et de l’appel de la méthode [Update](../../../ado/reference/ado-api/update-method.md) avec des paramètres de tableau de valeurs et de champs.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
