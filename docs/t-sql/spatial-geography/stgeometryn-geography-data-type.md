---
title: "STGeometryN (Type de données geography) | Documents Microsoft"
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
- STGeometryN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d5d11dc77ce692543068cba6739ef982bc8264c8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un **geography** élément dans une **GeometryCollection** ou l’un de ses sous-types. Lorsque STGeometryN() est utilisé sur un sous-type d’un **GeometryCollection**, tel que **MultiPoint** ou **MultiLineString**, cette méthode retourne le **geography** instance si elle est appelée avec N = 1.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est un **int** expression comprise entre 1 et le nombre de **geography** instances dans le **GeometryCollection**.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne null si le paramètre est supérieur au résultat de [STNumGeometries()](../../t-sql/spatial-geography/stnumgeometries-geography-data-type.md) et lèvera une **ArgumentOutOfRangeException** si le *expression* paramètre est inférieur à 1.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée un `MultiPoint``geography` instance et utilise `STGeometryN()` pour rechercher la deuxième `geography` instance de la **GeometryCollection**.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur les Instances géographiques](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

