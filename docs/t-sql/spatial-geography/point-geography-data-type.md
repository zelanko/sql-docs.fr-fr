---
title: "Point (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point method
- Point (geography Data Type)
ms.assetid: 0dc6f422-7aae-4016-b7f4-3289fa8f989c
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cefb6e199bbd4617b1fc2f6f71d9bb3997445dc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="point-geography-data-type"></a>Point (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Construit un **geography** instance représentant un **Point** instance à partir d’une référence spatiale (SRID) ID et de ses valeurs de latitude et longitude.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *Table d’adresses locales*  
 Est un **float** expression qui représente la coordonnée x de la **Point** en cours de génération.  
  
 *Long*  
 Est un **float** expression qui représente la coordonnée y de la **Point** en cours de génération. Pour plus d’informations sur les valeurs de longitude et de latitude valide, consultez [Point](../../relational-databases/spatial/point.md).  
  
 *SRID*  
 Est un **int** expression qui représente le SRID de le **geography** instance à retourner.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
> [!NOTE]  
>  Les arguments de la méthode Point (geography Data Type) ont des coordonnées inversées, comparées à WKT.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `Point()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Point(47.65100, -122.34900, 4326)  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes géographiques statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

