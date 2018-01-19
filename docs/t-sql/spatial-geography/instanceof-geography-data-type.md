---
title: "InstanceOf (Type de données geography) | Documents Microsoft"
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
- InstanceOf
- InstanceOf_TSQL
dev_langs: TSQL
helpviewer_keywords: InstanceOf method
ms.assetid: 1eaed0e4-1c72-45a9-9926-5b513335cf33
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 64fd27cc723257f7b64b826e6b64fc2294728248
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="instanceof-geography-data-type"></a>InstanceOf (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Teste si le **geography** instance est le même que le type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.InstanceOf ( 'geography_type')  
```  
  
## <a name="arguments"></a>Arguments  
 *geography_type*  
 Est un **nvarchar (4000)** chaîne spécifiant l’une des 16 types exposés dans le **geography** hiérarchie de type.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Retourne 1 si le type d’un **geography** instance est le même que le type spécifié, ou si le type spécifié est un ancêtre du type d’instance ; sinon, retourne 0.  
  
 Cela **geography** prend en charge de la méthode de type de données **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
 L’entrée de la méthode doit être une des valeurs suivantes : Geometry, Point, courbe, LineString, CircularString, Surface, Polygon, CurvePolygon, **GeometryCollection**, **MultiSurface**, **MultiPolygon, MultiCurve, MultiLineString**, **MultiPoint**, ou **FullGlobe**.  
  
 Cette méthode lève un `ArgumentException` si d'autres chaînes sont utilisées pour l'entrée.  
  
 Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `MultiPoint` et utilise `InstanceOf()` pour voir si l'instance est de type `GeometryCollection`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
