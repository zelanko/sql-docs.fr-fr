---
title: STIntersection (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIntersection_TSQL
- STIntersection (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection method
ms.assetid: 7e09468f-499f-4a38-ba4b-bb30b8821e3b
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: e1ee84ab21082193c50486f775a22caec4e0dbb4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936823"
---
# <a name="stintersection-geography-data-type"></a>STIntersection (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne un objet qui représente les points où une instance **geography** entre en intersection avec une autre instance **geography**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIntersection ( other_geography )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geography*  
 Autre instance **geography** à comparer à l’instance sur laquelle STIntersection() est appelé.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 L'intersection de deux instances géographiques est retournée.  
  
 STIntersection() retourne toujours une valeur Null si les SRID (identificateurs de référence spatiale) des instances **geography** ne correspondent pas.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge des instances spatiales qui sont plus grandes qu'un hémisphère. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut inclure des instances **FullGlobe** dans le jeu de résultats possibles retournés sur le serveur.  
  
 Le résultat peut contenir des segments d'arc de cercle uniquement si les instances d'entrée contiennent des segments d'arc de cercle.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-computing-the-intersection-of-a-polygon-and-a-linestring"></a>A. Calcul de l'intersection d'une instance Polygon et LineString  
 L'exemple suivant utilise `STIntersection()` pour calculer l'intersection d'un `Polygon` et d'un `LineString`.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="b-computing-the-intersection-of-a-polygon-and-a-curvepolygon"></a>B. Calcul de l'intersection d'une instance Polygon et CurvePolygon  
 L'exemple suivant retourne une instance qui contient un segment d'arc de cercle.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="c-computing-the-symmetric-difference-with-fullglobe"></a>C. Calcul de la différence symétrique avec FullGlobe  
 L'exemple suivant compare la différence symétrique d'un `Polygon` avec `FullGlobe`.  
  
```  
DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
SELECT @g.STIntersection('FULLGLOBE').ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
