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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 35efd51d640943c4d5293956a0638fa85ac302f1
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66710072"
---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>WillChangeField et FieldChangeComplete, événements (ADO)
Le **WillChangeField** événement est appelé avant qu’une opération en attente modifie la valeur d’une ou plusieurs [champ](../../../ado/reference/ado-api/field-object.md) des objets dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Le **FieldChangeComplete** événement est appelé une fois que la valeur d’un ou plusieurs **champ** objets a changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *cFields*  
 Un **Long** qui indique le nombre de **champ** dans des objets *champs*.  
  
 *Fields*  
 Pour **WillChangeField**, le *champs* paramètre est un tableau de **variantes** contenant **champ** objets avec les valeurs d’origine. Pour **FieldChangeComplete**, le *champs* paramètre est un tableau de **variantes** contenant **champ** objets avec les valeurs modifiées .  
  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Il décrit l’erreur qui s’est produite si la valeur de *ne* est **contraire**; sinon, elle n’est pas définie.  
  
 *adStatus*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état.  
  
 Lorsque **WillChangeField** est appelée, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi. Il est défini sur **adStatusCantDeny** si cet événement ne peut pas demander l’annulation de l’opération en attente.  
  
 Lorsque **FieldChangeComplete** est appelée, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi, ou à **contraire** si l’opération a échoué.  
  
 Avant de **WillChangeField** retourne, définissez ce paramètre sur **adStatusCancel** pour demander l’annulation de l’opération en attente.  
  
 Avant de **FieldChangeComplete** retourne, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification.  
  
 *pRecordset*  
 Un **Recordset** objet. Le **Recordset** pour laquelle cet événement s’est produit.  
  
## <a name="remarks"></a>Notes  
 Un **WillChangeField** ou **FieldChangeComplete** événement peut se produire lors de la définition du [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété et en appelant le [mise à jour](../../../ado/reference/ado-api/update-method.md) (méthode) avec les paramètres de tableau pour le champ et la valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Présentation rapide du gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)
