---
title: "Precision, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords:
- Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f100cf54a8090e7f84ee6a4310c7110c110c69fb
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="precision-property-ado"></a>Precision, propriété (ADO)
Indique le degré de précision des valeurs numériques dans un [paramètre](../../../ado/reference/ado-api/parameter-object.md) objet ou de numeric [champ](../../../ado/reference/ado-api/field-object.md) objets.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **octets** valeur qui indique le nombre maximal de chiffres utilisés pour représenter les valeurs.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **précision** propriété pour déterminer le nombre maximal de chiffres utilisés pour représenter les valeurs d’une valeur numérique **paramètre** ou **champ** objet.  
  
 La valeur est en lecture/écriture sur un **paramètre** objet.  
  
 Pour un **champ**objet, **précision** est généralement en lecture seule. Toutefois, pour les nouveaux **champ** les objets qui ont été ajoutées à la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), **précision** est en lecture/écriture une fois la [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété pour le **champ** a été spécifié et le fournisseur de données a ajouté le nouveau **champ** en appelant le [Mise à jour](../../../ado/reference/ado-api/update-method.md) méthode de la **champs** collection.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Field, objet](../../../ado/reference/ado-api/field-object.md)|[Parameter, objet](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [NumericScale et Precision, propriétés, exemple (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale et Precision, propriétés, exemple (VC ++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [NumericScale, propriété (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
