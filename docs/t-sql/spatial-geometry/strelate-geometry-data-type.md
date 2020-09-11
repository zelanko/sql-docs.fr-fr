---
description: STRelate (type de données geometry)
title: STRelate (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STRelate (geometry Data Type)
- STRelate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRelate (geometry Data Type)
ms.assetid: 9dcb5f58-35ab-4bb3-86ee-2d29eefba6d3
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: e427ca859bf6e1e861ed58bb7fdc4ab2dc869fc1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444977"
---
# <a name="strelate-geometry-data-type"></a>STRelate (type de données geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Retourne 1 si une instance **geometry** est associée à une autre instance **geometry**, où la relation est définie par une valeur de matrice de modèle DE-9IM (Dimensionally Extended 9 Intersection Model) ; sinon, retourne 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STRelate ( other_geometry, intersection_pattern_matrix )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *other_geometry*  
 Autre instance **geometry** à comparer à l’instance sur laquelle `STRelate()` est appelé.  
  
 *intersection_pattern_matrix*  
 Chaîne de type **nchar (9)** qui code des valeurs acceptables pour l’appareil de matrice de modèle DE-9IM entre les deux instances **geometry**.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne toujours une valeur Null si les SRID (ID de référence spatiale) des instances **geometry** ne correspondent pas. Cette méthode lève **ArgumentException** si la matrice n’est pas bien formée.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STRelate()` pour tester la disjointure spatiale de deux instances **geometry** à l’aide d’un modèle DE-9IM explicite.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(5 5)', 0);  
SELECT @g.STRelate(@h, 'FF*FF****');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
