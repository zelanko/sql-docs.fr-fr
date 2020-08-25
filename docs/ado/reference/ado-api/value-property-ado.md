---
description: Value, propriété (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1ab44fcbb8409cd866167d4fb58bebc1de906274
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776968"
---
# <a name="value-property-ado"></a>Value, propriété (ADO)

Indique la valeur assignée à un [champ](./field-object.md), un [paramètre](./parameter-object.md)ou un objet de [propriété](./property-object-ado.md) .
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour

Définit ou retourne une valeur de **type Variant** qui indique la valeur de l’objet. La valeur par défaut dépend de la propriété [type](./type-property-ado.md) .
  
## <a name="remarks"></a>Remarques

Utilisez la propriété **valeur** pour définir ou retourner des données à partir d’objets de **champ** , pour définir ou retourner des valeurs de paramètre avec des objets de **paramètre** , ou pour définir ou retourner des paramètres de propriété avec des objets de **propriété** . Le fait que la propriété de **valeur** soit en lecture/écriture ou en lecture seule dépend de nombreux facteurs. Pour plus d’informations, consultez les rubriques respectives relatives aux objets.

ADO permet de définir et de renvoyer des données binaires longues avec la propriété **value** .
  
> [!NOTE]
> Pour les objets **Parameter** , ADO lit la propriété **value** une seule fois à partir du fournisseur. Si une commande contient un **paramètre** dont la propriété **value** est vide et que vous créez un [jeu d’enregistrements](./recordset-object-ado.md) à partir de la commande, assurez-vous d’abord de fermer le **Recordset** avant de récupérer la propriété **value** . Dans le cas contraire, pour certains fournisseurs, la propriété **value** peut être vide et ne doit pas contenir la valeur correcte.
> 
> Pour les nouveaux objets **Field** qui ont été ajoutés à la collection [Fields](./fields-collection-ado.md) d’un objet [Record](./record-object-ado.md) , la propriété **value** doit être définie avant que toutes les autres propriétés de **champ** puissent être spécifiées. Tout d’abord, une valeur spécifique pour la propriété **value** doit avoir été assignée et [mise à jour](./update-method.md) sur la collection **Fields** appelée. Ensuite, d’autres propriétés telles que le [type](./type-property-ado.md) ou les [attributs](./attributes-property-ado.md) sont accessibles.
  
## <a name="applies-to"></a>S'applique à

:::row:::
    :::column:::
        [Objet Field](./field-object.md)  
    :::column-end:::
    :::column:::
        [Objet Parameter](./parameter-object.md)  
    :::column-end:::
    :::column:::
        [Property, objet (ADO)](./property-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi

[Value, exemple de propriété (VB)](./value-property-example-vb.md) 
 [Value, exemple de propriété (VC + +)](./value-property-example-vc.md)