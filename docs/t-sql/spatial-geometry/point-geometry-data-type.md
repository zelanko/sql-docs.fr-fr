---
title: "Point (type de données geometry) | Microsoft Docs"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
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
- Point (geometry Data Type)
ms.assetid: 7a2e593a-4d4c-4214-b0c5-02d1ac46bc66
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 89f1a91310ea7ccbc6d4ab8724022c3463e4ea8d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="point-geometry-data-type"></a>Point (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Construit une instance **geometry** qui représente une instance **Point** à partir de ses valeurs X et Y, et d’un SRID.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Point ( X, Y, SRID )  
```  
  
## <a name="arguments"></a>Arguments  
 *X*  
 Expression **float** qui représente la coordonnée X du **Point** généré.  
  
 *O*  
 Expression **float** qui représente la coordonnée Y du **Point** généré.  
  
 *SRID*  
 Expression **int** qui représente le SRID (ID de référence spatiale) de l’instance **geometry** à retourner.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes   
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `Point()` pour créer une instance `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Point(1, 10, 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes geometry statiques étendues](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

