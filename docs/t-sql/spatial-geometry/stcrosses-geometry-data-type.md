---
title: "STCrosses (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
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
- STCrosses (geometry Data Type)
- STCrosses_TSQL
dev_langs: TSQL
helpviewer_keywords: STCrosses (geometry Data Type)
ms.assetid: 3e3fc065-555a-4bee-8b71-e92f3dc62a4f
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1b1588649574e16f3bf46ae6d3fa06079f16a39
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="stcrosses-geometry-data-type"></a>STCrosses (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne 1 si une **geometry** instance croise une autre **geometry** instance. Retourne 0 dans le cas contraire.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STCrosses ( other_geometry )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geometry*  
 Une autre **geometry** instance à comparer à l’instance sur laquelle `STCrosses()` est appelé.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Deux **geometry** instances se croisent si les deux conditions suivantes sont remplies :  
  
-   L’intersection des deux **geometry** génère une géométrie dont les dimensions sont inférieures à la dimension maximale de la source des instances **geometry** instances.  
  
-   Le jeu d’intersection est intérieur aux deux sources **geometry** instances.  
  
 Cette méthode retourne toujours null si l’ID de référence spatiale (SRID) de la **geometry** instances ne correspondent pas.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `STCrosses()` pour tester deux instances `geometry` afin de savoir si elles se croisent.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0)', 0);  
SET @h = geometry::STGeomFromText('LINESTRING(0 0, 2 2)', 0);  
SELECT @g.STCrosses(@h);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

