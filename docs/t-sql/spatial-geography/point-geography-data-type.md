---
title: Point (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: ddd506ca3e78dd4ad5a12cfb108ca539e094cb4e
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937999"
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
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geography statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
