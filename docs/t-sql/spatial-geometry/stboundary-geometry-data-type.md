---
title: STBoundary (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 1a15d3bdc505c4406c1c5d09dbc9d6f007c34fe0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67930386"
---
# <a name="stboundary-geometry-data-type"></a>STBoundary (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la limite d’une instance **geometry**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STBoundary ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes  
 `STBoundary()` retourne un **GeometryCollection** vide quand les points de terminaison d’une instance **LineString**, **CircularString** ou **CompoundCurve** sont identiques.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>R. Utilisation de STBoundary() sur une instance LineString avec des points de terminaison différents  
 L’exemple suivant crée une instance `LineString``geometry`. `STBoundary()` retourne la limite de `LineString`.  
  
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
  
  
