---
title: "STIntersection (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STIntersection_TSQL
- STIntersection (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection (geometry Data Type)
ms.assetid: 354843f5-cc14-478c-974a-04f363f9530f
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: accdd0fe059521ec45beeb386db6bfa34e66ccc0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stintersection-geometry-data-type"></a>STIntersection (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un objet qui représente les points où une **geometry** instance croise une autre **geometry** instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIntersection ( other_geometry )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geometry*  
 Une autre **geometry** instance à comparer avec l’instance sur laquelle `STIntersection()` est appelée, afin de déterminer où elles se croisent.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 `STIntersection()`Retourne toujours null si l’ID de référence spatiale (SRID) de la **geometry** instances ne correspondent pas. Le résultat peut contenir des segments d'arc de cercle uniquement si les instances d'entrée les contiennent.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-stintersection-on-polygon-instances"></a>A. Utilisation de STIntersection() sur les instances Polygon  
 L'exemple suivant utilise `STIntersection()` pour calculer l'intersection de deux polygones.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="b-using-stintersection-with-curvepolygon-instance"></a>B. Utilisation de STIntersection() avec une instance CurvePolygon  
 L'exemple suivant retourne une instance qui contient un segment d'arc de cercle.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 SELECT @h.STIntersection(@g).ToString();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur les Instances géométriques](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


