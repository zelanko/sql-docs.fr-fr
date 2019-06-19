---
title: STDifference (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: c5d32ef391dee55f0b651c6729ccd5e2924e9f3c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937079"
---
# <a name="stdifference-geography-data-type"></a>STDifference (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un objet qui représente l’ensemble de points d’une instance **geography** située en dehors d’une autre instance **geography**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geography*  
 Autre instance **geography** qui indique les points à supprimer de l’instance sur laquelle STDifference() est appelé.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="exceptions"></a>Exceptions  
 Cette méthode lève **ArgumentException** si l’instance contient une arête antipodale.  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne toujours une valeur Null si les SRID (identificateurs de référence spatiale) des instances **geography** ne correspondent pas.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le jeu de résultats possibles retourné sur le serveur a été étendu aux instances **FullGlobe**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge des instances spatiales qui sont plus grandes qu'un hémisphère. Le résultat peut contenir des segments d'arc de cercle uniquement si les instances d'entrée contiennent des segments d'arc de cercle. Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Calcul de la différence entre deux instances géographiques  
 L’exemple suivant utilise `STDifference()` pour calculer la différence entre deux instances **geography**.  
  
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
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
