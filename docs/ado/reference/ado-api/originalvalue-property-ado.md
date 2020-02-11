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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917846"
---
# <a name="originalvalue-property-ado"></a>OriginalValue, propriété (ADO)
Indique la valeur d’un [champ](../../../ado/reference/ado-api/field-object.md) qui existait dans l’enregistrement avant toute modification.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **type Variant** qui représente la valeur d’un champ avant toute modification.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **OriginalValue** pour retourner la valeur de champ d’origine d’un champ de l’enregistrement actif.  
  
 En *mode de mise à jour immédiate* (dans lequel le fournisseur enregistre les modifications apportées à la source de données sous-jacente après l’appel de la méthode [Update](../../../ado/reference/ado-api/update-method.md) ), la propriété **OriginalValue** retourne la valeur de champ qui existait avant toute modification (autrement dit, depuis le dernier appel de la méthode **Update** ). Il s’agit de la même valeur que celle utilisée par la méthode [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) pour remplacer la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) .  
  
 En *mode de mise à jour par lot* (dans lequel le fournisseur met en cache plusieurs modifications et les écrit dans la source de données sous-jacente uniquement lorsque vous appelez la méthode [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) ), la propriété **OriginalValue** retourne la valeur de champ qui existait avant toute modification (autrement dit, depuis le dernier appel de la méthode **UpdateBatch** ). Il s’agit de la même valeur que celle utilisée par la méthode [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) pour remplacer la propriété **value** . Lorsque vous utilisez cette propriété avec la propriété [UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md) , vous pouvez résoudre les conflits qui résultent des mises à jour par lots.  
  
## <a name="record"></a>Enregistrement  
 Pour les objets [Record](../../../ado/reference/ado-api/record-object-ado.md) , la propriété **OriginalValue** est vide pour les champs ajoutés avant l’appel de la méthode [Update](../../../ado/reference/ado-api/update-method.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue et UnderlyingValue, exemples de propriétés (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue et UnderlyingValue, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [UnderlyingValue, propriété](../../../ado/reference/ado-api/underlyingvalue-property.md)
