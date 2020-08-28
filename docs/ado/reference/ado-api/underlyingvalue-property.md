---
description: UnderlyingValue, propriété
title: Propriété UnderlyingValue | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: a96924a682a0c916da8c6834ea7b290b88b6f690
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988170"
---
# <a name="underlyingvalue-property"></a>UnderlyingValue, propriété
Indique la valeur actuelle d’un objet [champ](./field-object.md) dans la base de données.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Retourne une valeur de **type Variant** qui indique la valeur du **champ**.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **UnderlyingValue** pour retourner la valeur de champ actuelle de la base de données. La valeur de champ dans la propriété **UnderlyingValue** est la valeur qui est visible pour votre transaction et peut être le résultat d’une mise à jour récente par une autre transaction. Cela peut être différent de la propriété [OriginalValue](./originalvalue-property-ado.md) , qui reflète la valeur retournée à l’origine à l' [objet Recordset](./recordset-object-ado.md).  
  
 Cela est similaire à l’utilisation de la méthode [Resync](./resync-method.md) , mais la propriété **UnderlyingValue** retourne uniquement la valeur d’un champ spécifique de l’enregistrement en cours. Il s’agit de la même valeur que celle utilisée par la méthode [Resync](./resync-method.md) pour remplacer la propriété [value](./value-property-ado.md) .  
  
 Lorsque vous utilisez cette propriété avec la propriété **OriginalValue** , vous pouvez résoudre les conflits qui résultent des mises à jour par lots.  
  
## <a name="record"></a>Enregistrement  
 Pour les objets [Record](./record-object-ado.md) , cette propriété est vide pour les champs ajoutés avant l’appel de la méthode [Update](./update-method.md) .  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Field](./field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue et UnderlyingValue, exemples de propriétés (VB)](./originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue et UnderlyingValue, exemples de propriétés (VC + +)](./originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [OriginalValue, propriété (ADO)](./originalvalue-property-ado.md)   
 [Resync, méthode](./resync-method.md)