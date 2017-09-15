---
title: "OriginalValue, propriété (ADO) | Documents Microsoft"
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
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 018f07a06e96f9284d0a8e63742a5abebca925e1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="originalvalue-property-ado"></a>OriginalValue, propriété (ADO)
Indique la valeur d’un [champ](../../../ado/reference/ado-api/field-object.md) qui existaient dans l’enregistrement, avant que des modifications ont été apportées.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **Variant** valeur qui représente la valeur d’un champ avant toute modification.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **OriginalValue** propriété pour retourner la valeur d’origine d’un champ à partir de l’enregistrement actif.  
  
 Dans *en mode de mise à jour immédiate* (dans lequel le fournisseur écrit les modifications dans la source de données sous-jacente après l’appel de la [mettre à jour](../../../ado/reference/ado-api/update-method.md) méthode), la **OriginalValue** retourne de la propriété la valeur du champ qui existaient avant toute modification (autrement dit, depuis le dernier **mise à jour** appel de méthode). Il s’agit du même valeur que la [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) méthode utilise pour remplacer la [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété.  
  
 Dans *mode de mise à jour par lot* (dans lequel le fournisseur met en cache plusieurs modifications et les écrit dans la source de données sous-jacente uniquement lorsque vous appelez le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) méthode), la **OriginalValue** propriété retourne la valeur du champ qui existaient avant toute modification (autrement dit, depuis le dernier **UpdateBatch** appel de méthode). Il s’agit du même valeur que la [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) méthode utilise pour remplacer la **valeur** propriété. Lorsque vous utilisez cette propriété avec la [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) propriété, vous pouvez résoudre les conflits générés par les mises à jour par lots.  
  
## <a name="record"></a>Record  
 Pour [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objets, la **OriginalValue** propriété est vide pour les champs ajoutés avant [mise à jour](../../../ado/reference/ado-api/update-method.md) est appelée.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue et UnderlyingValue, propriétés-exemple (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue et UnderlyingValue, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Propriété UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)

