---
title: "STConvexHull (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull method (geography)
ms.assetid: fb435db7-31bb-4243-9d8b-35379184cfb4
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a8376d12352994cd768b806f5ce47463196d4bfd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stconvexhull-geography-data-type"></a>STConvexHull (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un objet qui représente la forme convexe d’une **geography** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Retourne un `FullGlobe` pour l’objet **geography** instance qui a un angle d’enveloppe supérieur à 90 degrés.  
  
 Retourne une **geography** collection vide **geography** instance.  
  
 Retourne **null** pour non initialisé **geography** instance.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-stconvexhull-on-an-uninitialized-geography-instance"></a>A. Utilisation de STConvexHull() sur une instance géographique non initialisée  
 L’exemple suivant utilise `STConvexHull()` sur non initialisé **geography** instance.  
  
```
 DECLARE @g geography;  
 SELECT @g.STConvexHull();
 ```  
  
### <a name="b-using-stconvexhull-on-an-empty-geography-instance"></a>B. Utilisation de STConvexHull sur une instance géographique vide  
 L'exemple suivant utilise `STConvexHull()` sur une instance `Polygon` vide.  
  
```
 DECLARE @g geography = 'POLYGON EMPTY';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
### <a name="c-finding-the-convex-hull-of-a-non-convex-polygon-instance"></a>C. Recherche de la forme convexe d'une instance Polygon non convexe  
 L'exemple suivant utilise `STConvexHull()` pour rechercher la forme convexe d'une instance `Polygon` non convexe.  
  
```  
 DECLARE @g geography;  
 SET @g = geography::Parse('POLYGON((-120.533 46.566, -118.283 46.1, -122.3 47.45, -120.533 46.566))');  
 SELECT @g.STConvexHull().ToString();  
```  
  
### <a name="d-finding-the-convex-hull-on-a-geography-instance-with-an-envelope-angle-larger-than-90-degrees"></a>D. Recherche de la forme convexe sur une instance géographique avec un angle d'enveloppe supérieur à 90 degrés  
 L’exemple suivant utilise `STConvexHull()` sur un **geography** instance avec un angle d’enveloppe supérieur à 90 degrés.  
  
```
 DECLARE @g geography = 'POLYGON((20.533 46.566, -18.283 46.1, -22.3 47.45, 20.533 46.566))';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
  

