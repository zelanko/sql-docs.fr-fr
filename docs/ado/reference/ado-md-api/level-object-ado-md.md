---
title: Level, objet (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4a44060ae4ffd9399c34d4cd8133f5ad7404ed5a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949600"
---
# <a name="level-object-ado-md"></a>Level, objet (ADO MD)
Contient un jeu de membres, chacun d'entre eux ayant le même rang dans une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Les collections et les propriétés d’un **niveau** de l’objet, vous pouvez procédez comme suit :  
  
-   Identifier le **niveau** avec la [nom](../../../ado/reference/ado-md-api/name-property-ado-md.md) et [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) propriétés.  
  
-   Retourner une chaîne à utiliser lors de l’affichage le **niveau** avec la [légende](../../../ado/reference/ado-md-api/caption-property-ado-md.md) propriété.  
  
-   Retourne une chaîne explicite qui décrit le **niveau** avec la [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) propriété.  
  
-   Retourner le [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) objets qui composent le **niveau** avec la [membres](../../../ado/reference/ado-md-api/members-collection-ado-md.md) collection.  
  
-   Retourner le nombre de niveaux à partir de la racine de la **niveau** avec la [profondeur](../../../ado/reference/ado-md-api/depth-property-ado-md.md) propriété.  
  
-   Utiliser le ADO standard [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection pour obtenir des informations supplémentaires sur le **niveau** objet.  
  
 Le **propriétés** collection contient des propriétés fournies par le fournisseur. Le tableau suivant répertorie les propriétés qui peuvent être disponibles. La liste de propriétés réelle peut varier en fonction de l’implémentation du fournisseur. Consultez la documentation de votre fournisseur pour obtenir une liste plus complète des propriétés disponibles.  
  
|Name|Description|  
|----------|-----------------|  
|CatalogName|Le nom du catalogue auquel appartient ce cube.|  
|CubeName|Nom du cube.|  
|Description|Description explicite du niveau.|  
|DimensionUniqueName|Le nom non ambigu de la [dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Le nom non ambigu de la hiérarchie.|  
|LevelCaption|Étiquette ou légende associée au niveau.|  
|LevelCardinality|Nombre de membres du niveau.|  
|LevelGUID|Le GUID du niveau.|  
|LevelName|Nom du niveau.|  
|LevelNumber|La distance entre le niveau et la racine de la hiérarchie.|  
|LevelType|Le type de niveau.|  
|LevelUniqueName|Le nom non ambigu du niveau.|  
|SchemaName|Le nom du schéma auquel appartient ce cube.|  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple avec CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Hierarchy, objet (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Levels, Collection (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Members, Collection (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
