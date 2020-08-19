---
description: CubeDef, objet (ADO MD)
title: CubeDef, objet (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
author: rothja
ms.author: jroth
ms.openlocfilehash: cf8de68674ee1cc33f0ba16c9a0b3604418d0332
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441151"
---
# <a name="cubedef-object-ado-md"></a>CubeDef, objet (ADO MD)
Représente un cube à partir d’un schéma multidimensionnel, contenant un ensemble de dimensions associées.  
  
## <a name="remarks"></a>Notes  
 Avec les collections et les propriétés d’un objet **CubeDef** , vous pouvez effectuer les opérations suivantes :  
  
-   Identifiez un **CubeDef** avec la propriété [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) .  
  
-   Retourne une chaîne qui décrit le cube avec la propriété [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Retourne les dimensions qui composent le cube à l’aide de la collection de [dimensions](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md) .  
  
-   Obtenez des informations supplémentaires sur l’objet **CubeDef** avec la collection de [Propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) ADO standard.  
  
 La collection **Properties** contient des propriétés fournies par le fournisseur. Le tableau suivant répertorie les propriétés qui peuvent être disponibles. La liste de propriétés réelle peut varier en fonction de l’implémentation du fournisseur. Pour obtenir une liste plus complète des propriétés disponibles, consultez la documentation de votre fournisseur.  
  
|Nom|Description|  
|----------|-----------------|  
|CatalogName|Nom du catalogue auquel appartient ce cube.|  
|Created|Date et heure de création du cube.|  
|CubeGUID|GUID du cube.|  
|CubeName|Nom du cube.|  
|CubeType|Type du cube.|  
|DataUpdatedBy|ID d’utilisateur de la personne qui procède à la dernière mise à jour des données.|  
|Description|Description significative du cube.|  
|LastSchemaUpdate|Date et heure de la dernière mise à jour du schéma.|  
|SchemaName|Nom du schéma auquel appartient ce cube.|  
|SchemaUpdatedBy|ID d’utilisateur de la personne qui procède à la dernière mise à jour du schéma.|  
  
 Cette section contient la rubrique suivante.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CubeDef, exemple (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Objet Catalogue (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [CubeDefs, collection (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Dimensions, collection (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
