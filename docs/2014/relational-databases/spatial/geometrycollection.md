---
title: GeometryCollection | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b882aad6557eb812ee44eeeb46ecbbbda86061c3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84996317"
---
# <a name="geometrycollection"></a>GeometryCollection
  Une `GeometryCollection` est une collection de zéro ou plusieurs instances `geometry` ou `geography`. Une `GeometryCollection` peut être vide.  
  
## <a name="geometrycollection-instances"></a>Instances GeometryCollection  
  
### <a name="accepted-instances"></a>Instances acceptées  
 Pour qu'une instance `GeometryCollection` soit acceptée, il doit s'agir d'une instance `GeometryCollection` vide ou toutes les instances comprenant l'instance `GeometryCollection` doivent être des instances acceptées. L'exemple suivant illustre des instances acceptées.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 L'exemple suivant lève une exception `System.FormatException`, car l'instance `LinesString` dans l'instance `GeometryCollection` n'est pas acceptée.  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a>Instances valides  
 Une instance `GeometryCollection` est valide lorsque toutes les instances qui comprennent l'instance `GeometryCollection` sont valides. L'exemple suivant illustre trois instances `GeometryCollection` valides et une instance non valide.  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` n'est pas valide car l'instance `Polygon` dans l'instance `GeometryCollection` n'est pas valide.  
  
 Pour plus d’informations sur les instances acceptées et valides, consultez [Point](point.md), [MultiPoint](multipoint.md), [LineString](linestring.md), [MultiLineString](multilinestring.md), [polygone](polygon.md)et [MultiPolygon](multipolygon.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant instancie un objet `geometry``GeometryCollection` avec les valeurs Z dans SRID 1 contenant une instance `Point` et une instance `Polygon` .  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Données spatiales &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
