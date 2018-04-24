---
title: Point (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ee7a291dbfc359e15d010484fd4c33dcf645adf0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="point-geography-data-type"></a>Point (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Construit une instance **geography** qui représente une instance **Point** à partir de ses valeurs de latitude et de longitude, et d’un SRID (ID de référence spatiale).
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *Lat*  
 Expression **float** qui représente la coordonnée x du **Point** généré.  
  
 *Long*  
 Expression **float** qui représente la coordonnée y du **Point** généré. Pour plus d’informations sur les valeurs de latitude et de longitude valides, consultez [Point](../../relational-databases/spatial/point.md).  
  
 *SRID*  
 Expression **int** qui représente le SRID de l’instance **geography** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
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
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes geography statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
