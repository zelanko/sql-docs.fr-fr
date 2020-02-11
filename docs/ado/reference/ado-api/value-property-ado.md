---
title: Value, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::Value
- _Parameter::Value
helpviewer_keywords:
- Value property [ADO]
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e35dd93e6d90a81934d8f272ea79c5eb7c8a97c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67913922"
---
# <a name="value-property-ado"></a>Value, propriété (ADO)

Indique la valeur assignée à un [champ](../../../ado/reference/ado-api/field-object.md), un [paramètre](../../../ado/reference/ado-api/parameter-object.md)ou un objet de [propriété](../../../ado/reference/ado-api/property-object-ado.md) .
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour

Définit ou retourne une valeur de **type Variant** qui indique la valeur de l’objet. La valeur par défaut dépend de la propriété [type](../../../ado/reference/ado-api/type-property-ado.md) .
  
## <a name="remarks"></a>Notes

Utilisez la propriété **valeur** pour définir ou retourner des données à partir d’objets de **champ** , pour définir ou retourner des valeurs de paramètre avec des objets de **paramètre** , ou pour définir ou retourner des paramètres de propriété avec des objets de **propriété** . Le fait que la propriété de **valeur** soit en lecture/écriture ou en lecture seule dépend de nombreux facteurs. Pour plus d’informations, consultez les rubriques respectives relatives aux objets.

ADO permet de définir et de renvoyer des données binaires longues avec la propriété **value** .
  
> [!NOTE]
> Pour les objets **Parameter** , ADO lit la propriété **value** une seule fois à partir du fournisseur. Si une commande contient un **paramètre** dont la propriété **value** est vide et que vous créez un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md) à partir de la commande, assurez-vous d’abord de fermer le **Recordset** avant de récupérer la propriété **value** . Dans le cas contraire, pour certains fournisseurs, la propriété **value** peut être vide et ne doit pas contenir la valeur correcte.
> 
> Pour les nouveaux objets **Field** qui ont été ajoutés à la collection [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) d’un objet [Record](../../../ado/reference/ado-api/record-object-ado.md) , la propriété **value** doit être définie avant que toutes les autres propriétés de **champ** puissent être spécifiées. Tout d’abord, une valeur spécifique pour la propriété **value** doit avoir été assignée et [mise à jour](../../../ado/reference/ado-api/update-method.md) sur la collection **Fields** appelée. Ensuite, d’autres propriétés telles que le [type](../../../ado/reference/ado-api/type-property-ado.md) ou les [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) sont accessibles.
  
## <a name="applies-to"></a>S'applique à
  
||||  
|-|-|-|  
|[Objet Field](../../../ado/reference/ado-api/field-object.md)|[Objet Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|
  
## <a name="see-also"></a>Voir aussi

[Value, exemple de propriété (VB) value,](../../../ado/reference/ado-api/value-property-example-vb.md)
[exemple de propriété (VC + +)](../../../ado/reference/ado-api/value-property-example-vc.md) 
