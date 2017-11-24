---
title: "STDimension (Type de données geography) | Documents Microsoft"
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
- STDimension (geography Data Type)
- STDimension_TSQL
dev_langs: TSQL
helpviewer_keywords: STDimension method
ms.assetid: 4368b0f6-0678-4ade-87dc-b43d8b2e8d92
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9dc58b450f753aa67caf2a375d589ad96b1c500c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="stdimension-geography-data-type"></a>STDimension (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la dimension maximale d’un **geography** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **int**  
  
 Type de retour CLR : **SqlInt32**  
  
## <a name="remarks"></a>Notes  
 STDimension() retourne -1 si le **geography** instance est vide.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STDimension()` pour créer une variable de table pour contenir `geography` les instances et insère un `Point`, un `LineString`et un `Polygon`.  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geography);  
  
INSERT INTO @temp values ('Point', geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326));  
INSERT INTO @temp values ('LineString', geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
INSERT INTO @temp values ('Polygon', geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 L’exemple retourne ensuite les dimensions de chaque `geography`instance.  
  
|name|dim|  
|----------|---------|  
|Point|0|  
|LineString|1|  
|Polygone|2|  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
