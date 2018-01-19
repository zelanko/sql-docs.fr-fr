---
title: "STCentroid (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STCentroid_TSQL
- STCentroid (geometry Data Type)
dev_langs: TSQL
helpviewer_keywords: STCentroid (geometry Data Type)
ms.assetid: 4dc5a004-7a53-4cce-81dd-9f5e1dd0db78
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 3f84ca957df8b9a98a05a29619a0a5cccfb4b22d
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="stcentroid-geometry-data-type"></a>STCentroid (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne le centre géométrique d’une **geometry** instance se compose d’un ou plusieurs polygones.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STCentroid ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type Open Geospatial Consortium (OGC) : **Point**  
  
## <a name="remarks"></a>Notes  
 `STCentroid()`Retourne null si le **geometry** instance n’est pas un **Polygon, CurvePolygon**, ou **MultiPolygon** type.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-computing-the-centroid-of-a-polygon-instance"></a>A. Calcul du centroïde d'une instance Polygon  
 L’exemple suivant utilise `STCentroid()` pour calculer le centroïde d’une `polygon``geometry` instance :  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STCentroid().ToString();  
```  
  
### <a name="b-computing-the-centroid-of-a-curvepolygon-instance"></a>B. Calcul du centroïde d'une instance CurvePolygon  
 L'exemple suivant calcule le centroïde d'une instance `CurvePolygon` :  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))';  
 SELECT @g.STCentroid().ToString() AS Centroid
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

