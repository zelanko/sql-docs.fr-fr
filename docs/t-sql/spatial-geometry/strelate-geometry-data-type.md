---
title: "STRelate (Type de données geometry) | Documents Microsoft"
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
- STRelate (geometry Data Type)
- STRelate_TSQL
dev_langs: TSQL
helpviewer_keywords: STRelate (geometry Data Type)
ms.assetid: 9dcb5f58-35ab-4bb3-86ee-2d29eefba6d3
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 192156b32a4190479515ade197b57f638c14ca62
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="strelate-geometry-data-type"></a>STRelate (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne 1 si une **geometry** instance est liée à un autre **geometry** instance, où la relation est définie par une valeur de matrice de modèle Dimensionally Extended 9 Intersection Model (DE-9IM) ; sinon, retourne 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STRelate ( other_geometry, intersection_pattern_matrix )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geometry*  
 Une autre **geometry** instance à comparer à l’instance sur laquelle `STRelate()` est appelé.  
  
 *intersection_pattern_matrix*  
 Est une chaîne de type **nchar(9)** codage des valeurs acceptables pour le périphérique de matrice de modèle de-9IM entre les deux **geometry** instances.  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne toujours null si l’ID de référence spatiale (SRID) de la **geometry** instances ne correspondent pas. Cette méthode lève un **ArgumentException** si la matrice n’est pas bien formée.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STRelate()` pour tester deux **geometry** instances spatiales disjoint à l’aide un modèle DE-9IM explicit.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(5 5)', 0);  
SELECT @g.STRelate(@h, 'FF*FF****');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
