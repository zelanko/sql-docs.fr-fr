---
title: Attributes, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Attributes
- Field20::Attributes
- _Parameter::Attributes
helpviewer_keywords:
- Attributes property [ADO]
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
author: rothja
ms.author: jroth
ms.openlocfilehash: fe649e6636f33dfc73ee5aac949830b4175cd3ec
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242449"
---
# <a name="attributes-property-ado"></a>Attributes, propriété (ADO)
Indique une ou plusieurs caractéristiques d’un objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** .  
  
 Pour un objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) , la propriété **attributes** est en lecture/écriture, et sa valeur peut être la somme d’une ou plusieurs valeurs [XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md) . La valeur par défaut est zéro (0).  
  
 Pour un objet [Parameter](../../../ado/reference/ado-api/parameter-object.md) , la propriété **attributes** est en lecture/écriture, et sa valeur peut être la somme d’une ou plusieurs valeurs [ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md) . La valeur par défaut est **adParamSigned**.  
  
 Pour un objet [Field](../../../ado/reference/ado-api/field-object.md) , la propriété **attributes** peut être la somme d’une ou plusieurs valeurs [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) . Il est généralement en lecture seule. Toutefois, pour les nouveaux objets de **champ** qui ont été ajoutés à la collection de [champs](../../../ado/reference/ado-api/fields-collection-ado.md) d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), les **attributs** sont en lecture/écriture uniquement une fois que la propriété [value](../../../ado/reference/ado-api/value-property-ado.md) du **champ** a été spécifiée et que le nouveau **champ** a été ajouté avec succès par le fournisseur de données en appelant la méthode [Update](../../../ado/reference/ado-api/update-method.md) de la collection **Fields** .  
  
 Pour un objet de [propriété](../../../ado/reference/ado-api/property-object-ado.md) , la propriété **attributes** est en lecture seule et sa valeur peut être la somme d’une ou plusieurs valeurs [PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md) .  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **attributes** pour définir ou retourner des caractéristiques d’objets de **connexion** , d’objets de **paramètres** , d’objets de **champ** ou d’objets de **propriété** .  
  
 Lorsque vous définissez plusieurs attributs, vous pouvez additionner les constantes appropriées. Si vous définissez la valeur de la propriété sur une somme incluant des constantes non compatibles, une erreur se produit.  
  
> [!NOTE]
>  **Utilisation des services de données distants** Cette propriété n’est pas disponible sur un objet de **connexion** côté client.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
        [Objet Field](../../../ado/reference/ado-api/field-object.md)  
    :::column-end:::
    :::column:::
        [Objet Parameter](../../../ado/reference/ado-api/parameter-object.md)  
        [Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [Attributes et Name, exemple de propriétés (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Attributes et Name, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [AppendChunk, méthode (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [BeginTrans, CommitTrans et RollbackTrans, méthodes (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [GetChunk, méthode (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
