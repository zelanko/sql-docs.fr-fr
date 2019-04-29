---
title: Valeur de propriété (ADO) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 8c7e4d42bc58321c5b650df5e8e842290094fcf4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043694"
---
# <a name="value-property-ado"></a>Value, propriété (ADO)

Indique la valeur assignée à un [champ](../../../ado/reference/ado-api/field-object.md), [paramètre](../../../ado/reference/ado-api/parameter-object.md), ou [propriété](../../../ado/reference/ado-api/property-object-ado.md) objet.
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour

Définit ou retourne un **Variant** valeur qui indique la valeur de l’objet. Valeur par défaut varie selon le [Type](../../../ado/reference/ado-api/type-property-ado.md) propriété.
  
## <a name="remarks"></a>Notes

Utilisez le **valeur** propriété pour définir ou retourner des données à partir de **champ** objets, pour définir ou retourner des valeurs de paramètre avec **paramètre** objets, ou pour définir ou retourner les paramètres de propriété avec **Propriété** objets. Si le **valeur** propriété est en lecture/écriture ou en lecture seule dépend de nombreux facteurs. Consultez les rubriques de l’objet respectifs pour plus d’informations.

ADO permet de définir et retourner des données binaires longues avec le **valeur** propriété.
  
> [!NOTE]
> Pour **paramètre** objets, les lectures ADO le **valeur** propriété qu’une seule fois à partir du fournisseur. Si une commande contient un **paramètre** dont **valeur** propriété est vide et que vous créez un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) à partir de la commande, vérifiez tout d’abord fermer le  **Jeu d’enregistrements** avant d’extraire le **valeur** propriété. Sinon, pour certains fournisseurs, le **valeur** propriété peut être vide et ne contient pas la valeur correcte.
> 
> Pour les nouveaux **champ** les objets qui ont été ajoutées à la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet, le **valeur** propriété doit être définie avant toute autre **champ** propriétés peuvent être spécifiées. Tout d’abord, une valeur spécifique pour le **valeur** propriété doit avoir été affectée et [mise à jour](../../../ado/reference/ado-api/update-method.md) sur le **champs** collection appelée. Ensuite, d’autres propriétés, telles que [Type](../../../ado/reference/ado-api/type-property-ado.md) ou [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) sont accessibles.
  
## <a name="applies-to"></a>S'applique à
  
||||  
|-|-|-|  
|[Field, objet](../../../ado/reference/ado-api/field-object.md)|[Parameter, objet](../../../ado/reference/ado-api/parameter-object.md)|[Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|
  
## <a name="see-also"></a>Voir aussi

[Valeur de propriété, exemple (VB)](../../../ado/reference/ado-api/value-property-example-vb.md)
[valeur exemple de propriété (VC ++)](../../../ado/reference/ado-api/value-property-example-vc.md) 
