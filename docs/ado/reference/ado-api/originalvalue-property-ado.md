---
title: OriginalValue, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::OriginalValue
helpviewer_keywords:
- OriginalValue property [ADO]
ms.assetid: 6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 512569ce2baa8acabdf8bcbf8f637ebf20e4f613
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917846"
---
# <a name="originalvalue-property-ado"></a>OriginalValue, propriété (ADO)
Indique la valeur d’un [champ](../../../ado/reference/ado-api/field-object.md) qui existaient dans l’enregistrement avant que des modifications ont été apportées.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Variant** valeur qui représente la valeur d’un champ avant toute modification.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **OriginalValue** propriété pour retourner la valeur du champ d’origine pour un champ à partir de l’enregistrement actif.  
  
 Dans *en mode de mise à jour immédiate* (dans lequel le fournisseur écrit les modifications à la source de données sous-jacente après avoir appelé la [mettre à jour](../../../ado/reference/ado-api/update-method.md) méthode), la **OriginalValue** retourne de la propriété la valeur du champ qui existaient avant toute modification (autrement dit, depuis le dernier **mise à jour** appel de méthode). Il s’agit du même valeur que la [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) méthode utilise pour remplacer le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété.  
  
 Dans *mode de mise à jour par lots* (dans lequel le fournisseur met en cache plusieurs modifications et les écrit dans la source de données sous-jacente uniquement lorsque vous appelez le [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) méthode), la **OriginalValue** propriété retourne la valeur du champ qui existaient avant toute modification (autrement dit, depuis le dernier **UpdateBatch** appel de méthode). Il s’agit du même valeur que la [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) méthode utilise pour remplacer le **valeur** propriété. Lorsque vous utilisez cette propriété avec la [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) propriété, vous pouvez résoudre les conflits qui proviennent des mises à jour par lots.  
  
## <a name="record"></a>Enregistrement  
 Pour [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objets, le **OriginalValue** propriété sera vide pour les champs ajoutés avant [mise à jour](../../../ado/reference/ado-api/update-method.md) est appelée.  
  
## <a name="applies-to"></a>S'applique à  
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue et UnderlyingValue, exemple de propriétés (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue et UnderlyingValue, exemple de propriétés (VC ++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [UnderlyingValue, propriété](../../../ado/reference/ado-api/underlyingvalue-property.md)
