---
title: "STSymDifference (Type de données geography) | Documents Microsoft"
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
- STSymDifference (geography Data Type)
- STSymDifference_TSQL
dev_langs: TSQL
helpviewer_keywords: STSymDifference (geography Data Type)
ms.assetid: 82bbfa2c-a61b-4f41-9bf8-6f720f363bae
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 479d0badaced9808c5bd727b5f818dcab729605b
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="stsymdifference-geography-data-type"></a>STSymDifference (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un objet qui représente tous les points qui sont dans une **geography** instance ou un autre **geography** instance, mais pas ceux qui se trouvent dans les deux instances.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STSymDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geography*  
 Une autre **geography** instance en plus de l’instance sur laquelle STSymDistance() est appelé.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne toujours null si les identificateurs de référence spatiale (SRID) de la **geography** instances ne correspondent pas.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge des instances spatiales qui sont plus grandes qu'un hémisphère. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le jeu de résultats possibles sur le serveur a été étendu aux **FullGlobe** instances.  
  
 Le résultat peut contenir des segments d'arc de cercle uniquement si les instances d'entrée contiennent des segments d'arc de cercle.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-computing-the-symmetric-difference-of-two-polygons"></a>A. Calcul de la différence symétrique de deux polygones  
 L'exemple suivant utilise `STSymDifference()` pour calculer la différence symétrique entre deux instances `Polygon`.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('POLYGON((-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STSymDifference(@h).ToString();  
```  
  
### <a name="b-computing-the-symmetric-difference-with-fullglobe"></a>B. Calcul de la différence symétrique avec FullGlobe  
 L'exemple suivant compare la différence symétrique d'un `Polygon` avec `FullGlobe`.  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STSymDifference('FULLGLOBE').ToString();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
