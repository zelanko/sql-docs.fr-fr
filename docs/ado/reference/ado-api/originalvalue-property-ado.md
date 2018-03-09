---
title: "OriginalValue, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8cc3597b6f3b476a889f836ae899f558b38eff20
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
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
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue et UnderlyingValue, propriétés-exemple (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue et UnderlyingValue, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [UnderlyingValue, propriété](../../../ado/reference/ado-api/underlyingvalue-property.md)
