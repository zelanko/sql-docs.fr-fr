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
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 182a0f4b7e74490f9600b7ef43cd2baa511080f6
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176639"
---
# <a name="multipolygon"></a>MultiPolygon
  Une instance `MultiPolygon` est une collection de zéro ou plusieurs instances `Polygon`.

## <a name="polygon-instances"></a>Instances Polygon
 L'illustration suivante montre des exemples d'instances `MultiPolygon`.

 ![Exemples d'instances MultiPolygon géométriques](../../database-engine/media/multipolygon.gif "Exemples d'instances MultiPolygon géométriques")

 Comme indiqué par l'illustration :

-   La Figure 1 est une instance `MultiPolygon` avec deux éléments `Polygon`. La limite est définie par les deux anneaux extérieurs et les trois anneaux intérieurs.

-   La Figure 2 est une instance `MultiPolygon` avec deux éléments `Polygon`. La limite est définie par les deux anneaux extérieurs et les trois anneaux intérieurs. Les deux éléments `Polygon` se croisent à un point tangent.

### <a name="accepted-instances"></a>Instances acceptées
 Les instances `MultiPolygon` sont acceptées si l'une des conditions suivantes est remplie.

-   Il s'agit d'une instance `MultiPolygon` vide.

-   Toutes les instances comprenant l'instance `MultiPolygon` sont des instances `Polygon` acceptées. Pour plus d’informations sur `Polygon` les instances acceptées, consultez [Polygon](../spatial/polygon.md).

 Les exemples suivants illustrent `MultiPolygon` des instances acceptées.

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

1.  Toutes les instances comprenant l'instance `MultiPolygon` sont des instances `Polygon` valides. Pour connaître `Polygon` les instances valides, consultez [Polygon](../spatial/polygon.md).

2.  Aucune des instances `Polygon` comprenant l'instance `MultiPolygon` n'en chevauche une autre.

 L'exemple suivant illustre deux instances `MultiPolygon` valides et une instance `MultiPolygon` non valide.

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 
  `@g2` n'est pas valide car les deux instances de `Polygon` se touchent uniquement sur un point tangent. 
  `@g3` n'est pas valide car les intérieurs des deux instances de `Polygon` se chevauchent.

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
 [Polygon](../spatial/polygon.md) [STArea &#40;Geometry type de données&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STCentroid &#40;geometry type de données&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;Geometry type de données](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)&#41;[spatial Data](../spatial/spatial-data-sql-server.md) &#40;SQL Server&#41;


