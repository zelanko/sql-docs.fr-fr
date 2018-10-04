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
manager: craigg
ms.openlocfilehash: 02c5b9193b89c131095ccfec6ef185d5ff39f4d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47820787"
---
# <a name="type-property-ado"></a>Type, propriété (ADO)
Indique le type de données ou de type opérationnel d’un [paramètre](../../../ado/reference/ado-api/parameter-object.md), [champ](../../../ado/reference/ado-api/field-object.md), ou [propriété](../../../ado/reference/ado-api/property-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valeur.  
  
## <a name="remarks"></a>Notes  
 Pour **paramètre** objets, le **Type** propriété est en lecture/écriture. Pour les nouveaux **champ** les objets qui ont été ajoutées à la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), **Type** est en lecture/écriture uniquement après le [ Valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété pour le **champ** a été spécifié et le fournisseur de données a correctement ajouté le nouveau **champ** en appelant le [mettre à jour](../../../ado/reference/ado-api/update-method.md)(méthode) de la **champs** collection.  
  
 Pour tous les autres objets, la **Type** propriété est en lecture seule.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Field, objet](../../../ado/reference/ado-api/field-object.md)|[Parameter, objet](../../../ado/reference/ado-api/parameter-object.md)|[Property, objet (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété de type (objet Field) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Exemple de propriété de type (propriété) (VC ++)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [RecordType, propriété (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type, propriété (objet Stream ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)
