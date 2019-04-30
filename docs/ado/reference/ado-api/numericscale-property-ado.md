---
title: NumericScale, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99d27ff0348a22324ad99c515617a6831fa9f9f3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301309"
---
# <a name="numericscale-property-ado"></a>NumericScale, propriété (ADO)
Indique l’échelle des valeurs numériques dans un [paramètre](../../../ado/reference/ado-api/parameter-object.md) ou [champ](../../../ado/reference/ado-api/field-object.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **octets** valeur qui indique le nombre de décimales utilisées pour les valeurs numériques qui sera résolu.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **NumericScale** propriété afin de déterminer le nombre de chiffres à droite de la virgule décimale permet de représenter les valeurs d’une valeur numérique **paramètre** ou **champ** objet.  
  
 Pour **paramètre** objets, le **NumericScale** propriété est en lecture/écriture.  
  
 Pour un **champ**objet, **NumericScale** est généralement en lecture seule. Toutefois, pour les nouveaux **champ** les objets qui ont été ajoutées à la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection d’un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md), **NumericScale** est en lecture/écriture uniquement après la [valeur](../../../ado/reference/ado-api/value-property-ado.md) propriété pour le **champ** a été spécifié et le fournisseur de données a correctement ajouté le nouveau **champ** en appelant le [ Mise à jour](../../../ado/reference/ado-api/update-method.md) méthode de la [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Parameter, objet](../../../ado/reference/ado-api/parameter-object.md)|[Field, objet](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [NumericScale et Precision, propriétés, exemple (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale et Precision, propriétés, exemple (VC ++)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Precision, propriété (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
