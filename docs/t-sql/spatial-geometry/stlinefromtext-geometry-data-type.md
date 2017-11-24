---
title: "STLineFromText (Type de données geometry) | Documents Microsoft"
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
- STLineFromText (geometry Data Type)
- STLineFromText_TSQL
dev_langs: TSQL
helpviewer_keywords: STLineFromText (geometry Data Type)
ms.assetid: 430508ad-207b-4dee-a4d1-4ddf25e6b4a9
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 40fbc8cc01601c3c7a3893be7aa61eb50f8952ab
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="stlinefromtext-geometry-data-type"></a>STLineFromText (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un **geometry** instance à partir d’une représentation de la réplication continue en cluster (WKT, Open Geospatial Consortium (OGC) Well-Known Text) augmentée des Z (élévation) et les valeurs M (mesure) apportées par l’instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STLineFromText ( 'linestring_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *linestring_tagged_text*  
 Est la représentation WKT de le **geometryLineString** instance à retourner. *linestring_tagged_text* est un **nvarchar (max)** expression.  
  
 *SRID*  
 Est un **int** expression représentant les données spatiales ID de référence (SRID) de la **geometryLineString** instance à retourner.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type OGC : **LineString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode lève un **FormatException** si l’entrée n’est pas correctement mise en forme.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `STLineFromText()` pour créer une instance `geometry`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100, 200 200)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geometry statiques de l’OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

