---
title: Objets ADO MD | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, objects
- objects [ADO MD]
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
author: rothja
ms.author: jroth
ms.openlocfilehash: 01a35a38812d105a1e26454022321e57448efadd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765250"
---
# <a name="ado-md-objects"></a>Objets ADO MD

|||  
|-|-|  
|[Axe](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|Représente un axe positionnel ou de filtre d’un CellSet, contenant les membres sélectionnés d’une ou plusieurs dimensions.|  
|[Catalogue](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|Contient des informations sur les schémas multidimensionnels (c’est-à-dire les cubes et les dimensions sous-jacentes, les hiérarchies, les niveaux et les membres) spécifiques à un fournisseur de données multidimensionnelles (MDP).|  
|[Cellules](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|Représente les données à l’intersection des coordonnées d’axe, contenues dans un CellSet.|  
|[CellSet](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|Représente les résultats d’une requête multidimensionnelle. Il s’agit d’une collection de cellules sélectionnées à partir de cubes ou d’autres cellules.|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|Représente un cube à partir d’un schéma multidimensionnel, contenant un ensemble de dimensions associées.|  
|[Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|Représente l’une des dimensions d’un cube multidimensionnel, contenant une ou plusieurs hiérarchies de membres.|  
|[Hierarchy](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|Représente une façon dont les membres d’une dimension peuvent être agrégés ou « cumulés ». Une dimension peut être agrégée avec une ou plusieurs hiérarchies.|  
|[Niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md)|Contient un ensemble de membres, chacun ayant le même rang dans une hiérarchie.|  
|[Member](../../../ado/reference/ado-md-api/member-object-ado-md.md)|Représente un membre d’un niveau dans un cube, les enfants d’un membre d’un niveau ou un membre d’une position le long d’un axe d’un ensemble de cellules.|  
|[Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)|Représente un ensemble d’un ou plusieurs membres de dimensions différentes qui définissent un point le long d’un axe.|  
  
 En outre, l’objet **catalogue** est connecté à un objet de **connexion** ADO, qui est inclus dans la bibliothèque ADO standard :  
  
|Object|Description|  
|------------|-----------------|  
|[Connection](../../../ado/reference/ado-api/connection-object-ado.md)|Représente une connexion ouverte à une source de données.|  
  
 Les relations entre ces objets sont illustrées dans le [modèle objet ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md).  
  
 De nombreux objets ADO MD peuvent être contenus dans une collection correspondante. Par exemple, un objet [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) peut être contenu dans une collection [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) d’un **catalogue**. Pour plus d’informations, consultez [ADO MD collections](../../../ado/reference/ado-md-api/ado-md-collections.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADO MD](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [Exemples de code ADO MD](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [Collections de ADO MD](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [ADO MD les constantes énumérées](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [Méthodes ADO MD](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [Modèle objet ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Propriétés ADO MD](../../../ado/reference/ado-md-api/ado-md-properties.md)
