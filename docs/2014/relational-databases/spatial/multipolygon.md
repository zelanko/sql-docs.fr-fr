---
title: MultiPolygon | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d941425b1faa2fcbc23b48555dce12846a7fd52e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62524199"
---
# <a name="multipolygon"></a>MultiPolygon
  Une instance `MultiPolygon` est une collection de zéro ou plusieurs instances `Polygon`.  
  
## <a name="polygon-instances"></a>Instances Polygon  
 L'illustration suivante montre des exemples d'instances `MultiPolygon`.  
  
 ![Exemples d’instances MultiPolygon géométriques](../../database-engine/media/multipolygon.gif "Exemples d’instances MultiPolygon géométriques")  
  
 Comme indiqué par l'illustration :  
  
-   La Figure 1 est une instance `MultiPolygon` avec deux éléments `Polygon`. La limite est définie par les deux anneaux extérieurs et les trois anneaux intérieurs.  
  
-   La Figure 2 est une instance `MultiPolygon` avec deux éléments `Polygon`. La limite est définie par les deux anneaux extérieurs et les trois anneaux intérieurs. Les deux éléments `Polygon` se croisent à un point tangent.  
  
### <a name="accepted-instances"></a>Instances acceptées  
 Les instances `MultiPolygon` sont acceptées si l'une des conditions suivantes est remplie.  
  
-   Il s'agit d'une instance `MultiPolygon` vide.  
  
-   Toutes les instances comprenant l'instance `MultiPolygon` sont des instances `Polygon` acceptées. Pour plus d’informations sur accepté `Polygon` instances, consultez [polygone](../spatial/polygon.md).  
  
 Les exemples suivants montrent acceptés `MultiPolygon` instances.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
```  
  
 L'exemple suivant illustre une instance MultiPolygon qui lève une exception `System.FormatException`.  
  
```  
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';  
```  
  
 La deuxième instance du MultiPolygon est une instance LineString et non une instance Polygon acceptée.  
  
### <a name="valid-instances"></a>Instances valides  
 Les instances `MultiPolygon` sont valides s'il s'agit d'instances `MultiPolygon` vides ou si elles respectent les critères suivants.  
  
1.  Toutes les instances comprenant l'instance `MultiPolygon` sont des instances `Polygon` valides. Pour valide `Polygon` instances, consultez [polygone](../spatial/polygon.md).  
  
2.  Aucune des instances `Polygon` comprenant l'instance `MultiPolygon` n'en chevauche une autre.  
  
 L'exemple suivant illustre deux instances `MultiPolygon` valides et une instance `MultiPolygon` non valide.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g2` n'est pas valide car les deux instances de `Polygon` se touchent uniquement sur un point tangent. `@g3` n'est pas valide car les intérieurs des deux instances de `Polygon` se chevauchent.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant illustre la création d’une instance `geometry``MultiPolygon` et retourne l’entrée WKT (well-known text) du deuxième composant.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');  
SELECT @g.STGeometryN(2).STAsText();  
```  
  
 Cet exemple instancie une instance `MultiPolygon` vide.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Polygon](../spatial/polygon.md)   
 [STArea &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type)   
 [STCentroid &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)   
 [STPointOnSurface &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [Données spatiales &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)  
  
  
