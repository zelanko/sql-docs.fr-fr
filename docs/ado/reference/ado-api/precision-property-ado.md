---
title: Precision, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords:
- Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
author: rothja
ms.author: jroth
ms.openlocfilehash: a7a9b9a0a8416cb47adf8d959990ba1e39c60595
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242593"
---
# <a name="precision-property-ado"></a>Precision, propriété (ADO)
Indique le degré de précision des valeurs numériques dans un objet de [paramètre](../../../ado/reference/ado-api/parameter-object.md) ou pour les objets de [champ](../../../ado/reference/ado-api/field-object.md) numérique.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur d' **octet** qui indique le nombre maximal de chiffres utilisés pour représenter des valeurs.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **précision** pour déterminer le nombre maximal de chiffres utilisés pour représenter les valeurs d’un objet de **paramètre** ou de **champ** numérique.  
  
 La valeur est en lecture/écriture sur un objet de **paramètre** .  
  
 Pour un objet de **champ**, la **précision** est généralement en lecture seule. Toutefois, pour les nouveaux objets de **champ** qui ont été ajoutés à la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), la **précision** est en lecture/écriture uniquement après la spécification de la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) pour le **champ** et le fournisseur de données a correctement ajouté le nouveau **champ** en appelant la méthode [Update](../../../ado/reference/ado-api/update-method.md) de la collection **Fields** .  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Objet Field](../../../ado/reference/ado-api/field-object.md)  
    :::column-end:::
    :::column:::
        [Objet Parameter](../../../ado/reference/ado-api/parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [NumericScale et Precision, exemple de propriétés (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale et Precision, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [NumericScale, propriété (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
