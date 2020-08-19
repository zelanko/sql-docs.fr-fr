---
description: NumericScale, propriété (ADO)
title: NumericScale, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
author: rothja
ms.author: jroth
ms.openlocfilehash: ce13556c013c527ec16f183001b6042ed501398d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443051"
---
# <a name="numericscale-property-ado"></a>NumericScale, propriété (ADO)
Indique l’échelle des valeurs numériques dans un objet de [paramètre](../../../ado/reference/ado-api/parameter-object.md) ou de [champ](../../../ado/reference/ado-api/field-object.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur d' **octet** qui indique le nombre de décimales auquel les valeurs numériques seront résolues.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **NumericScale** pour déterminer le nombre de chiffres à droite de la virgule décimale qui sera utilisé pour représenter les valeurs d’un objet de **paramètre** ou de **champ** numérique.  
  
 Pour les objets **Parameter** , la propriété **NumericScale** est en lecture/écriture.  
  
 Pour un objet **Field**, **NumericScale** est généralement en lecture seule. Toutefois, pour les nouveaux objets de **champ** qui ont été ajoutés à la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), **NumericScale** est en lecture/écriture uniquement une fois que la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) du **champ** a été spécifiée et que le fournisseur de données a correctement ajouté le nouveau **champ** en appelant la méthode [Update](../../../ado/reference/ado-api/update-method.md) de la collection [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) .  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Objet Field](../../../ado/reference/ado-api/field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter (objet)](../../../ado/reference/ado-api/parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [NumericScale et Precision, exemple de propriétés (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale et Precision, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Precision, propriété (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
