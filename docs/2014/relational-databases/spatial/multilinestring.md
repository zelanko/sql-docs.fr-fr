---
title: MultiLineString | Microsoft Docs
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c755752aaa2e4cac795b277c0cdba070d7b2f6d5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62524179"
---
# <a name="multilinestring"></a>MultiLineString
  Un `MultiLineString` est une collection de zéro ou plusieurs `geometry` ou **geographyLineString** instances.  
  
## <a name="multilinestring-instances"></a>Instances MultiLineString  
 L'illustration suivante montre des exemples d'instances `MultiLineString`.  
  
 ![Exemples d’instances MultiLineString géométriques](../../database-engine/media/multilinestring.gif "Exemples d’instances MultiLineString géométriques")  
  
 Comme indiqué par l'illustration :  
  
-   Figure 1 est une simple `MultiLineString` instance dont la limite est de quatre points de terminaison de ses deux `LineString` éléments.  
  
-   La Figure 2 est une instance `MultiLineString` simple car seuls les points de terminaison des éléments `LineString` se croisent. La limite est constituée des deux points de terminaison non chevauchants.  
  
-   La Figure 3 est une instance `MultiLineString` non simple car l'intérieur de l'un de ses éléments `LineString` est croisé. La limite de cette instance `MultiLineString` est constituée des quatre points de terminaison.  
  
-   La Figure 4 est une instance `MultiLineString` non simple et non close.  
  
-   La Figure 5 est une `MultiLineString` simple et non fermée. Il n’est pas fermé, car son `LineStrings` éléments ne sont pas fermés. Elle est simple car aucun des intérieurs des instances `LineStrings` ne se croise.  
  
-   La Figure 6 est une instance `MultiLineString` simple et fermée. Elle est fermée car tous ses éléments sont fermés. Elle est simple car aucun de ses éléments ne se croise aux intérieurs.  
  
### <a name="accepted-instances"></a>Instances acceptées  
 Pour qu'une instance `MultiLineString` soit acceptée, elle doit être vide ou contenir uniquement les instances `LineString` acceptées. Pour plus d’informations sur accepté `LineString` instances, consultez [LineString](../spatial/linestring.md). Les exemples suivants illustrent des instances `MultiLineString` acceptées.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 L'exemple suivant lève une exception `System.FormatException` car la deuxième instance de `LineString` n'est pas valide.  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a>Instances valides  
 Pour un `MultiLineString` instance soit valide, il doit respecter les critères suivants :  
  
1.  Toutes les instances comprenant l'instance `MultiLineString` doivent être des instances `LineString` valides.  
  
2.  Deux instances `LineString` comprenant l'instance `MultiLineString` peuvent se chevaucher sur un intervalle. Les instances `LineString` peuvent uniquement se croiser, se toucher ou toucher d'autres instances `LineString` à un nombre fini de points.  
  
 L'exemple suivant illustre trois instances `MultiLineString` valides et une instance `MultiLineString` non valide.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` n'est pas valide car la deuxième instance `LineString` chevauche la première instance `LineString` à un intervalle. Elles se touchent à un nombre infini de points.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une instance `geometry``MultiLineString` simple qui contient deux éléments `LineString` avec le SRID 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 Pour instancier cette instance avec un SRID différent, utilisez `STGeomFromText()` ou `STMLineStringFromText()`. Vous pouvez également utiliser `Parse()` puis modifier le SRID, comme indiqué dans l'exemple suivant.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STLength &#40;Type de données geometry&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STIsClosed &#40;type de données geometry&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [LineString](../spatial/linestring.md)   
 [Données spatiales &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)  
  
  
