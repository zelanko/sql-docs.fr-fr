---
title: Objet Level (ADO MD) | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e1ee7ad05f05d2eb77d7d705200c52ddf3f01146
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82753845"
---
# <a name="level-object-ado-md"></a>Level, objet (ADO MD)
Contient un ensemble de membres, chacun ayant le même rang dans une hiérarchie.  
  
## <a name="remarks"></a>Remarques  
 Avec les collections et les propriétés d’un objet **Level** , vous pouvez effectuer les opérations suivantes :  
  
-   Identifiez le **niveau** avec les propriétés [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) et [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) .  
  
-   Retourne une chaîne à utiliser lors de l’affichage du **niveau** avec la propriété [Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md) .  
  
-   Retourne une chaîne significative qui décrit le **niveau** avec la propriété [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Retourne les objets [membres](../../../ado/reference/ado-md-api/member-object-ado-md.md) qui composent le **niveau** avec la collection de [membres](../../../ado/reference/ado-md-api/members-collection-ado-md.md) .  
  
-   Retourne le nombre de niveaux à partir de la racine du **niveau** avec la propriété [Depth](../../../ado/reference/ado-md-api/depth-property-ado-md.md) .  
  
-   Utilisez la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) ADO standard pour obtenir des informations supplémentaires sur l’objet **Level** .  
  
 La collection **Properties** contient des propriétés fournies par le fournisseur. Le tableau suivant répertorie les propriétés qui peuvent être disponibles. La liste de propriétés réelle peut varier en fonction de l’implémentation du fournisseur. Pour obtenir une liste plus complète des propriétés disponibles, consultez la documentation de votre fournisseur.  
  
|Nom|Description|  
|----------|-----------------|  
|CatalogName|Nom du catalogue auquel appartient ce cube.|  
|CubeName|Nom du cube.|  
|Description|Description explicite du niveau.|  
|DimensionUniqueName|Nom non ambigu de la [dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Nom non ambigu de la hiérarchie.|  
|LevelCaption|Étiquette ou légende associée au niveau.|  
|LevelCardinality|Nombre de membres du niveau.|  
|LevelGUID|GUID du niveau.|  
|LevelName|Nom du niveau.|  
|LevelNumber|Distance entre le niveau et la racine de la hiérarchie.|  
|LevelType|Type de niveau.|  
|LevelUniqueName|Nom non ambigu du niveau.|  
|SchemaName|Nom du schéma auquel appartient ce cube.|  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CubeDef, exemple (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Objet Hierarchy (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Collection Levels (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Collection Members (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
