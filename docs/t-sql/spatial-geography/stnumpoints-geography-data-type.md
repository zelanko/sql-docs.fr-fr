---
title: "STNumPoints (Type de données geography) | Documents Microsoft"
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
- STNumPoints (geography Data Type)
- STNumPoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumPoints method
ms.assetid: 25ff7ad1-ba5f-4cfb-816a-59255ac1591d
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 803e631cb1e0250ebedd28a97afe4e20476396cf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stnumpoints-geography-data-type"></a>STNumPoints (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le nombre total de points dans chacune des figures dans une **geography** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STNumPoints ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **int**  
  
 Type de retour CLR : **SqlInt32**  
  
## <a name="remarks"></a>Notes  
 Cette méthode compte les points dans la description d’un **geography** instance. Les points en double sont comptés ; toutefois, les points de connexion entre les segments ne sont comptés qu'une seule fois. Si cette instance est une collection, cette méthode retourne le nombre total de points dans la collection.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-retrieving-the-total-number-of-points-in-a-linestring"></a>A. Récupération du nombre total de points dans un LineString  
 L'exemple suivant crée une instance `LineString` et utilise `STNumPoints()` pour déterminer combien de points ont été utilisés dans la description de l'instance.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STNumPoints();  
```  
  
### <a name="b-retrieving-the-total-number-of-points-in-a-geometrycollection"></a>B. Récupération du nombre total de points dans un GeometryCollection  
 L'exemple suivant retourne une somme des points pour tous les éléments dans `GeometryCollection`.  
  
```  
DECLARE @g geography = 'GEOMETRYCOLLECTION(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)  
    ,CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
SELECT @g.STNumPoints();  
```  
  
### <a name="c-returning-the-number-of-points-in-a-compoundcurve"></a>C. Retour du nombre de points dans un CompoundCurve  
 L'exemple suivant retourne le nombre de points dans une instance CompoundCurve. La requête retourne 5 au lieu de 6 car STNumPoints() compte le point de connexion entre les segments une fois seulement.  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658),( -122.348 47.658, -121.56 48.12, -122.358 47.653))'  
 SELECT @g.STNumPoints();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur les Instances géographiques](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
