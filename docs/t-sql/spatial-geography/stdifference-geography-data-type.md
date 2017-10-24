---
title: "STDifference (Type de données geography) | Documents Microsoft"
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
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5afb37eb29e63d8cf08e9c158b94385a66d4c41f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stdifference-geography-data-type"></a>STDifference (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un objet qui représente le jeu de points d’une **geography** instance se trouve en dehors d’un autre **geography** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geography*  
 Une autre **geography** instance qui indique quels points pour supprimer de l’instance sur laquelle STDifference() est appelé.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="exceptions"></a>Exceptions  
 Cette méthode lève un **ArgumentException** si l’instance contient un contour antipode.  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne toujours null si les identificateurs de référence spatiale (SRID) de la **geography** instances ne correspondent pas.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le jeu de résultats possibles retourné sur le serveur a été étendu aux **FullGlobe** instances. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge des instances spatiales qui sont plus grandes qu'un hémisphère. Le résultat peut contenir des segments d'arc de cercle uniquement si les instances d'entrée contiennent des segments d'arc de cercle. Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Calcul de la différence entre deux instances géographiques  
 L’exemple suivant utilise `STDifference()` pour calculer la différence entre deux **geography** instances.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-using-a-fullglobe-with-stdifference"></a>B. Utilisation d'un FullGlobe avec STDifference()  
 L'exemple suivant utilise l'instance `FullGlobe`. Le premier résultat est une `GeometryCollection` vide et le second est une instance `Polygon`. `STDifference()` retourne une `GeometryCollection` vide lorsqu'une instance `FullGlobe` est le paramètre. Chaque point dans une instance `geography` appelante est contenu dans une instance `FullGlobe`.  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 DECLARE @h geography = 'FULLGLOBE';  
 SELECT @g.STDifference(@h).ToString(),  
 @h.STDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur les Instances géographiques](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

