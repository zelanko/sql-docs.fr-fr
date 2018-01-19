---
title: "STBoundary (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs: TSQL
helpviewer_keywords: STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9ab224de8f9b75be3737488abe885d4d8c69a32c
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="stboundary-geometry-data-type"></a>STBoundary (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la limite d’un **geometry** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STBoundary ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 `STBoundary()`Retourne une **GeometryCollection** lorsque les points de terminaison pour un **LineString**, **CircularString**, ou **CompoundCurve** de l’instance sont les mêmes.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>A. Utilisation de STBoundary() sur une instance LineString avec des points de terminaison différents  
 L’exemple suivant crée un `LineString``geometry` instance. `STBoundary()`Retourne la limite de la `LineString`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STBoundary().ToString();  
```  
  
### <a name="b-using-stboundary-on-a-linestring-instance-with-the-same-endpoints"></a>B. Utilisation de STBoundary() sur une instance LineString avec les mêmes points de terminaison  
 L'exemple suivant crée une instance `LineString` valide avec les mêmes points de terminaison. `STBoundary()` retourne une instance `GeometryCollection` vide.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, -2 2, 0 0)', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
### <a name="c-using-stboundary-on-a-curvepolygon-instance"></a>C. Utilisation de STBoundary() sur une instance CurvePolygon  
 L'exemple suivant utilise `STBoundary()` sur une instance `CurvePolygon`. `STBoundary()` retourne une instance `CircularString`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(0 0, 2 2, 0 2, -2 2, 0 0))', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
