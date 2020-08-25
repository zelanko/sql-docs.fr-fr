---
description: Precision, propriété (ADO)
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
ms.openlocfilehash: 59a42a7f577ae8f4712e679853d53939fd6f6ed1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88773138"
---
# <a name="precision-property-ado"></a>Precision, propriété (ADO)
Indique le degré de précision des valeurs numériques dans un objet de [paramètre](./parameter-object.md) ou pour les objets de [champ](./field-object.md) numérique.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur d' **octet** qui indique le nombre maximal de chiffres utilisés pour représenter des valeurs.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **précision** pour déterminer le nombre maximal de chiffres utilisés pour représenter les valeurs d’un objet de **paramètre** ou de **champ** numérique.  
  
 La valeur est en lecture/écriture sur un objet de **paramètre** .  
  
 Pour un objet de **champ**, la **précision** est généralement en lecture seule. Toutefois, pour les nouveaux objets de **champ** qui ont été ajoutés à la collection de [champs](./fields-collection-ado.md) d’un [enregistrement](./record-object-ado.md), la **précision** est en lecture/écriture uniquement après la spécification de la propriété [value](./value-property-ado.md) pour le **champ** et le fournisseur de données a correctement ajouté le nouveau **champ** en appelant la méthode [Update](./update-method.md) de la collection **Fields** .  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Objet Field](./field-object.md)  
    :::column-end:::
    :::column:::
        [Objet Parameter](./parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [NumericScale et Precision, exemple de propriétés (VB)](./numericscale-and-precision-properties-example-vb.md)   
 [NumericScale et Precision, exemple de propriétés (VC + +)](./numericscale-and-precision-properties-example-vc.md)   
 [NumericScale, propriété (ADO)](./numericscale-property-ado.md)