---
title: "STTouches (Type de données geometry) | Documents Microsoft"
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
- STTouches (geometry Data Type)
- STTouches_TSQL
dev_langs: TSQL
helpviewer_keywords: STTouches (geometry Data Type)
ms.assetid: af3650b4-26da-4600-9cc2-1be71dd76a14
caps.latest.revision: "24"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46f877bba6e70110f34662bf3110dcd7128d468e
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="sttouches-geometry-data-type"></a>STTouches (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne 1 si une **geometry** instance touche spatialement une autre **geometry** instance. Retourne 0 dans le cas contraire.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STTouches ( other_geometry )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geometry*  
 Une autre **geometry** instance à comparer à l’instance sur laquelle `STTouches()` est appelé.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Deux **geometry** instances se touchent si leurs ensembles de points se croisent, mais leurs intérieurs ne se croisent pas.  
  
 Cette méthode retourne toujours null si l’ID de référence spatiale (SRID) de la **geometry** instances ne correspondent pas.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `STTouches()` pour tester deux instances `geometry` afin de savoir si elles se touchent.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(1 1)', 0);  
SELECT @g.STTouches(@h);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

