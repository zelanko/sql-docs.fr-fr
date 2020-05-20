---
title: Propriété UnderlyingValue | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::GetUnderlyingValue
- Field20::get_UnderlyingValue
- Field20::UnderlyingValue
helpviewer_keywords:
- UnderlyingValue property
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
author: rothja
ms.author: jroth
ms.openlocfilehash: 67dd3f7a6892d4fa139ffd14b3dc33e4231a6cb2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759525"
---
# <a name="underlyingvalue-property"></a>UnderlyingValue, propriété
Indique la valeur actuelle d’un objet [champ](../../../ado/reference/ado-api/field-object.md) dans la base de données.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Retourne une valeur de **type Variant** qui indique la valeur du **champ**.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **UnderlyingValue** pour retourner la valeur de champ actuelle de la base de données. La valeur de champ dans la propriété **UnderlyingValue** est la valeur qui est visible pour votre transaction et peut être le résultat d’une mise à jour récente par une autre transaction. Cela peut être différent de la propriété [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) , qui reflète la valeur retournée à l’origine à l' [objet Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Cela est similaire à l’utilisation de la méthode [Resync](../../../ado/reference/ado-api/resync-method.md) , mais la propriété **UnderlyingValue** retourne uniquement la valeur d’un champ spécifique de l’enregistrement en cours. Il s’agit de la même valeur que celle utilisée par la méthode [Resync](../../../ado/reference/ado-api/resync-method.md) pour remplacer la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) .  
  
 Lorsque vous utilisez cette propriété avec la propriété **OriginalValue** , vous pouvez résoudre les conflits qui résultent des mises à jour par lots.  
  
## <a name="record"></a>Enregistrement  
 Pour les objets [Record](../../../ado/reference/ado-api/record-object-ado.md) , cette propriété est vide pour les champs ajoutés avant l’appel de la méthode [Update](../../../ado/reference/ado-api/update-method.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue et UnderlyingValue, exemples de propriétés (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue et UnderlyingValue, exemples de propriétés (VC + +)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [OriginalValue, propriété (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Resync, méthode](../../../ado/reference/ado-api/resync-method.md)
