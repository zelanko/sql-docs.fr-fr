---
title: "STSymDifference (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STSymDifference_TSQL
- STSymDifference (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STSymDifference (geometry Data Type)
ms.assetid: 1d4cf35a-ca89-4aa4-ae30-e61a0ff18b53
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b83e2ef917f76f615588327c8a3c2721f30e347a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stsymdifference-geometry-data-type"></a>STSymDifference (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne un objet qui représente tous les points qui sont dans une **geometry** instance ou un autre **geometry** instance, mais pas ceux qui se trouvent dans les deux instances.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STSymDifference ( other_geometry )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geometry*  
 Une autre **geometry** instance en plus de l’instance sur laquelle `STSymDistance()` est appelé.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne toujours null si l’ID de référence spatiale (SRID) de la **geometry** instances ne correspondent pas. Le résultat peut contenir des segments d'arc de cercle uniquement si les instances d'entrée contiennent des segments d'arc de cercle.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-computing-the-symmetric-difference-of-two-polygon-instances"></a>A. Calcul de la différence symétrique de deux instances Polygon  
 L'exemple suivant utilise `STSymDifference()` pour calculer la différence symétrique entre deux instances `Polygon`.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 0 2, 2 2, 2 0, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STSymDifference(@h).ToString();  
```  
  
### <a name="b-computing-the-symmetric-difference-between-a-curvepolygon-and-a-polygon-instance"></a>B. Calcul de la différence symétrique entre une instance CurvePolygon et une instance Polygon  
 L'exemple suivant retourne un `GeometryCollection` qui représente la différence symétrique entre un `CurvePolygon` et un `Polygon`.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 5 -1, 5 3, 1 3, 1 -1))';  
 SELECT @h.STSymDifference(@g).ToString();
 ```  
  
## <a name="c-using-stsymdifference-on-curvepolygon-instance-with-an-inscribed-polygon-instance"></a>C. Utilisation de STSymDifference() sur une instance CurvePolygon avec une instance Polygon inscrite  
 L'exemple suivant retourne une instance `CurvePolygon` avec un anneau `Polygon` intérieur qui représente la différence symétrique entre les deux instances comparées.  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON (CIRCULARSTRING (0 -4, 4 0, 0 4, -4 0, 0 -4))';  
 DECLARE @h geometry = 'POLYGON ((1 -1, 2 -1, 2 1, 1 1, 1 -1))';  
 SELECT @h.STSymDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur les Instances géométriques](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

