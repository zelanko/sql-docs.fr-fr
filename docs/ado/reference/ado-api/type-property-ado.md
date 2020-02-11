---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ee1058299becb4a7a4234debc097516cb02dd41
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937866"
---
# <a name="type-property-ado"></a>Type, propriété (ADO)
Indique le type opérationnel ou le type de données d’un [paramètre](../../../ado/reference/ado-api/parameter-object.md), d’un [champ](../../../ado/reference/ado-api/field-object.md)ou d’un objet de [propriété](../../../ado/reference/ado-api/property-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) .  
  
## <a name="remarks"></a>Notes  
 Pour les objets de **paramètre** , la propriété de **type** est en lecture/écriture. Pour les nouveaux objets de **champ** qui ont été ajoutés à la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), le **type** est lecture/écriture uniquement lorsque la propriété [valeur](../../../ado/reference/ado-api/value-property-ado.md) du **champ** a été spécifiée et que le fournisseur de données a correctement ajouté le nouveau **champ** en appelant la méthode [Update](../../../ado/reference/ado-api/update-method.md) de la collection **Fields** .  
  
 Pour tous les autres objets, la propriété **type** est en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Objet Field](../../../ado/reference/ado-api/field-object.md)|[Objet Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Type, exemple de propriété (Field) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Type, exemple de propriété (propriété) (VC + +)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [RecordType, propriété (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type, propriété (objet Stream ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)
