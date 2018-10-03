---
title: STIntersection (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIntersection_TSQL
- STIntersection (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection (geometry Data Type)
ms.assetid: 354843f5-cc14-478c-974a-04f363f9530f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f556697457ba8baa649458f7a7c46b02e4682d4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759667"
---
# <a name="stintersection-geometry-data-type"></a>STIntersection (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un objet qui représente les points où une instance **geometry** entre en intersection avec une autre instance **geometry**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIntersection ( other_geometry )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geometry*  
 Autre instance **geometry** à comparer à l’instance sur laquelle `STIntersection()` est appelé, pour déterminer leur intersection.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes   
 `STIntersection()` retourne toujours une valeur Null si les SRID (ID de référence spatiale) des instances **geometry** ne correspondent pas. Le résultat peut contenir des segments d'arc de cercle uniquement si les instances d'entrée les contiennent.  
  
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
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

