---
title: "Valeur de propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Field20::Value
- _Parameter::Value
helpviewer_keywords:
- Value property [ADO]
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 17e3c9f28e42dbd70118bb29a330514a9c29e013
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="value-property-ado"></a>Value (propriété) (ADO)
Indique la valeur assignée à un [champ](../../../ado/reference/ado-api/field-object.md), [paramètre](../../../ado/reference/ado-api/parameter-object.md), ou [propriété](../../../ado/reference/ado-api/property-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Variant** valeur qui indique la valeur de l’objet. Valeur par défaut varie selon le [Type](../../../ado/reference/ado-api/type-property-ado.md) propriété.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **valeur** propriété pour définir ou retourner les données à partir de **champ** pour définir ou retourner les valeurs de paramètres avec les objets **paramètre** objets, ou pour définir ou retourner les paramètres de propriété avec **Propriété** objets. Si le **valeur** propriété est en lecture/écriture ou en lecture seule dépend de nombreux facteurs ??? consultez les rubriques de l’objet respectifs pour plus d’informations.  
  
 ADO permet de définir et retourner des données binaires longues avec la **valeur** propriété.  
  
> [!NOTE]
>  Pour **paramètre** objets, ADO lit la **valeur** propriété qu’une seule fois à partir du fournisseur. Si une commande contient un **paramètre** dont **valeur** propriété est vide, et vous créez un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) à partir de la commande, vérifiez tout d’abord fermer le ** Jeu d’enregistrements** avant de récupérer le **valeur** propriété. Sinon, pour certains fournisseurs, le **valeur** propriété peut être vide et ne contient pas la valeur correcte.  
>   
>  Pour les nouveaux **champ** les objets qui ont été ajoutées à la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet, le **valeur** propriété doit être définie avant toute autre **champ** propriétés peuvent être spécifiées. Tout d’abord, une valeur spécifique pour le **valeur** propriété doit avoir été affectée et [mise à jour](../../../ado/reference/ado-api/update-method.md) sur la **champs** collection appelée. Ensuite, d’autres propriétés, telles que [Type](../../../ado/reference/ado-api/type-property-ado.md) ou [attributs](../../../ado/reference/ado-api/attributes-property-ado.md) est accessible.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Objet Field](../../../ado/reference/ado-api/field-object.md)|[Objet de paramètre](../../../ado/reference/ado-api/parameter-object.md)|[Objet de propriété (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de valeur de propriété (VB)](../../../ado/reference/ado-api/value-property-example-vb.md)   
 [Exemple de valeur de propriété (VC ++)](../../../ado/reference/ado-api/value-property-example-vc.md)   

