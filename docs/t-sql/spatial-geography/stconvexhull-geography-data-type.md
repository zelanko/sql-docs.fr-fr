---
title: STConvexHull (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull method (geography)
ms.assetid: fb435db7-31bb-4243-9d8b-35379184cfb4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b3d06da6d6f972c64d4bf196699b55a611b0f992
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68042468"
---
# <a name="stconvexhull-geography-data-type"></a>STConvexHull (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne un objet qui représente l’enveloppe convexe d’une instance **geography**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Retourne un objet `FullGlobe` pour l’instance **geography** qui a un angle d’enveloppe supérieur à 90 degrés.  
  
 Retourne une collection **geography** vide pour une instance **geography** vide.  
  
 Retourne **null** pour une instance **geography** non initialisée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-stconvexhull-on-an-uninitialized-geography-instance"></a>R. Utilisation de STConvexHull() sur une instance géographique non initialisée  
 L’exemple suivant utilise `STConvexHull()` sur une instance **geography** non initialisée.  
  
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
 L’exemple suivant utilise `STConvexHull()` sur une instance **geography** avec un angle d’enveloppe supérieur à 90 degrés.  
  
```
 DECLARE @g geography = 'POLYGON((20.533 46.566, -18.283 46.1, -22.3 47.45, 20.533 46.566))';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
  
