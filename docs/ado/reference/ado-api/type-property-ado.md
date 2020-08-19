---
description: Type, propriété (ADO)
title: Type, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Type
- Field20::Type
helpviewer_keywords:
- Type property [ADO]
ms.assetid: 8a4c079f-9f4f-4545-801d-85983b8db71e
author: rothja
ms.author: jroth
ms.openlocfilehash: de97e62a8152e7d14d1442cc1da9b5138ddc39fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441741"
---
# <a name="type-property-ado"></a>Type, propriété (ADO)
Indique le type opérationnel ou le type de données d’un [paramètre](../../../ado/reference/ado-api/parameter-object.md), d’un [champ](../../../ado/reference/ado-api/field-object.md)ou d’un objet de [propriété](../../../ado/reference/ado-api/property-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) .  
  
## <a name="remarks"></a>Notes  
 Pour les objets de **paramètre** , la propriété de **type** est en lecture/écriture. Pour les nouveaux objets de **champ** qui ont été ajoutés à la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), le **type** est lecture/écriture uniquement lorsque la propriété [valeur](../../../ado/reference/ado-api/value-property-ado.md) du **champ** a été spécifiée et que le fournisseur de données a correctement ajouté le nouveau **champ** en appelant la méthode [Update](../../../ado/reference/ado-api/update-method.md) de la collection **Fields** .  
  
 Pour tous les autres objets, la propriété **type** est en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Objet Field](../../../ado/reference/ado-api/field-object.md)  
    :::column-end:::
    :::column:::
        [Parameter (objet)](../../../ado/reference/ado-api/parameter-object.md)  
    :::column-end:::
    :::column:::
        [Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [Type, exemple de propriété (Field) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Type, exemple de propriété (propriété) (VC + +)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [RecordType, propriété (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type, propriété (objet Stream ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)
