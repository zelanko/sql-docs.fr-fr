---
title: "STDistance (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance method
ms.assetid: 063d8722-e019-4d3d-8fcf-dbf5325823e7
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f79891d789938a6f4615c0e4be9cc3ba5d361f1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stdistance-geography-data-type"></a>STDistance (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne la distance la plus courte entre un point dans un **geography** instance et un point dans un autre **geography** instance.  
  
> [!NOTE]  
>  `STDistance()`Retourne le plus court **LineString** entre deux types geography. Il s'agit d'une approximation proche de la distance géodésique. L’écart de `STDistance()` sur les modèles à partir de la distance géodésique exacte n’est pas plus de. 25 %. Cela évite toute confusion quant aux subtiles différences entre longueur et distance dans les types géodésiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geography*  
 Une autre **geography** instance à partir de laquelle mesurer la distance entre l’instance sur laquelle STDistance() est appelée. Si *other_geography* STDistance() vide est défini, retourne null.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 STDistance() renvoie toujours la valeur null si l’ID de référence spatiale (SRID) de la **geography** instances ne correspondent pas.  
  
> [!NOTE]  
>  Les méthodes sur le **geography** type de données qui calculent une zone ou une distance retournent des résultats différents selon le SRID de l’instance utilisée dans la méthode.   Pour plus d’informations sur les SRID, consultez [des identificateurs de référence spatiale &#40; SRID &#41; ](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant recherche la distance entre deux **geography** instances.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur les Instances géographiques](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

