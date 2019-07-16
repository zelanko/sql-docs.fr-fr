---
title: Hierarchy, objet (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 35e02e4823d0a3abf245e1885b95176d6350d712
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949692"
---
# <a name="hierarchy-object-ado-md"></a>Hierarchy, objet (ADO MD)
Représente une façon dans lequel les membres d’un [dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md) peuvent être agrégées ou « remontées ». Une dimension peut être agrégée avec une ou plusieurs hiérarchies.  
  
## <a name="remarks"></a>Notes  
 Les collections et les propriétés d’un **hiérarchie** de l’objet, vous pouvez procédez comme suit :  
  
-   Identifier le **hiérarchie** avec la [nom](../../../ado/reference/ado-md-api/name-property-ado-md.md) et [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) propriétés.  
  
-   Retourne une chaîne explicite qui décrit le **hiérarchie** avec la [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) propriété.  
  
-   Retourner le [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objets qui composent le **hiérarchie** avec la [niveaux](../../../ado/reference/ado-md-api/levels-collection-ado-md.md) collection.  
  
-   Utiliser le ADO standard [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection pour obtenir des informations supplémentaires sur le **hiérarchie** objet.  
  
 Le **propriétés** collection contient des propriétés fournies par le fournisseur. Le tableau suivant répertorie les propriétés qui peuvent être disponibles. La liste de propriétés réelle peut varier en fonction de l’implémentation du fournisseur. Consultez la documentation de votre fournisseur pour obtenir une liste plus complète des propriétés disponibles.  
  
|Nom|Description|  
|----------|-----------------|  
|AllMember|Le membre au niveau plus élevé de la hiérarchie.|  
|CatalogName|Le nom du catalogue auquel appartient ce cube.|  
|CubeName|Nom du cube.|  
|DefaultMember|Le nom unique du membre par défaut pour cette hiérarchie.|  
|Description|Description explicite de la hiérarchie.|  
|DimensionType|Le type de dimension à laquelle appartient cette hiérarchie.|  
|DimensionUniqueName|Le nom non ambigu de la dimension.|  
|HierarchyCaption|Étiquette ou légende associée à la hiérarchie.|  
|HierarchyCardinality|Nombre de membres de la hiérarchie.|  
|HierarchyGUID|Le GUID de la hiérarchie.|  
|HierarchyName|Nom de la hiérarchie.|  
|HierarchyUniqueName|Le nom non ambigu de la hiérarchie.|  
|SchemaName|Le nom du schéma auquel appartient ce cube.|  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple avec CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Dimension, objet (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Hierarchies, Collection (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Levels, Collection (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
