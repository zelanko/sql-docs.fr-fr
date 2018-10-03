---
title: UnderlyingValue, propriété | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7bcb751fb32634fc544dfa11ee862cd47112514
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836067"
---
# <a name="underlyingvalue-property"></a>UnderlyingValue, propriété
Indique la valeur actuelle d’un [champ](../../../ado/reference/ado-api/field-object.md) objet dans la base de données.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Variant** valeur qui indique la valeur de la **champ**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **UnderlyingValue** propriété pour retourner la valeur du champ à partir de la base de données. La valeur du champ dans le **UnderlyingValue** propriété est la valeur qui est visible pour votre transaction et peut résulter d’une mise à jour récente par une autre transaction. Cela peut différer de la [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) propriété, qui reflète la valeur qui a été retournée à l’origine pour le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Cela ressemble à utiliser le [Resync](../../../ado/reference/ado-api/resync-method.md) (méthode), mais la **UnderlyingValue** propriété renvoie uniquement la valeur d’un champ spécifique à partir de l’enregistrement actif. C’est cette valeur qui le [Resync](../../../ado/reference/ado-api/resync-method.md) méthode utilise pour remplacer le [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété.  
  
 Lorsque vous utilisez cette propriété avec la **OriginalValue** propriété, vous pouvez résoudre les conflits qui proviennent des mises à jour par lots.  
  
## <a name="record"></a>Record  
 Pour [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objets, cette propriété est vide pour les champs ajoutés avant [mise à jour](../../../ado/reference/ado-api/update-method.md) est appelée.  
  
## <a name="applies-to"></a>S'applique à  
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OriginalValue et UnderlyingValue, exemple de propriétés (VB)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [OriginalValue et UnderlyingValue, exemple de propriétés (VC ++)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [OriginalValue, propriété (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Resync, méthode](../../../ado/reference/ado-api/resync-method.md)
