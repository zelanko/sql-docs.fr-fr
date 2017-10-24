---
title: "WillChangeField et FieldChangeComplete, événements (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d9ce0412a76f34f653273d294e7f8add031a9d9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>WillChangeField et FieldChangeComplete, événements (ADO)
Le **WillChangeField** événement est appelé avant qu’une opération en attente modifie la valeur d’un ou plusieurs [champ](../../../ado/reference/ado-api/field-object.md) des objets dans le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Le **FieldChangeComplete** événement est appelé après la valeur d’un ou plusieurs **champ** objets a changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Paramètres  
 *cFields*  
 A **Long** qui indique le nombre de **champ** objets *champs*.  
  
 *Champs*  
 Pour **WillChangeField**, le *champs* paramètre est un tableau de **variantes** contenant **champ** objets avec les valeurs d’origine. Pour **FieldChangeComplete**, le *champs* paramètre est un tableau de **variantes** contenant **champ** objets avec les valeurs modifiées .  
  
 *pError*  
 Un [erreur](../../../ado/reference/ado-api/error-object.md) objet. Elle décrit l’erreur qui s’est produite si la valeur de *ne* est **contraire**; sinon, elle n’est pas définie.  
  
 *N'*  
 Un [il ne](../../../ado/reference/ado-api/eventstatusenum.md) valeur d’état.  
  
 Lorsque **WillChangeField** est appelée, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi. Il est défini sur **adStatusCantDeny** si cet événement ne peut pas demander l’annulation de l’opération en attente.  
  
 Lorsque **FieldChangeComplete** est appelée, ce paramètre est défini sur **adStatusOK** si l’opération qui a provoqué l’événement a réussi, ou pour **contraire** si l’opération a échoué.  
  
 Avant de **WillChangeField** retourne, définissez ce paramètre sur **adStatusCancel** pour demander l’annulation de l’opération en attente.  
  
 Avant de **FieldChangeComplete** retourne, définissez ce paramètre sur **adStatusUnwantedEvent** pour éviter toute notification.  
  
 *Connection*  
 A **Recordset** objet. Le **Recordset** pour laquelle cet événement s’est produit.  
  
## <a name="remarks"></a>Notes  
 A **WillChangeField** ou **FieldChangeComplete** événement peut se produire lors de la définition du [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété et en appelant le [mise à jour](../../../ado/reference/ado-api/update-method.md) (méthode) avec les paramètres de tableau de champ et de valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de modèle d’événements ADO (VC ++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Résumé du Gestionnaire d’événements ADO](../../../ado/guide/data/ado-event-handler-summary.md)

