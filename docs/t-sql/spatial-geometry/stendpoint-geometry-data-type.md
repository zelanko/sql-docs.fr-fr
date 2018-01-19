---
title: "STEndpoint (Type de données geometry) | Documents Microsoft"
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
- STEndpoint (geometry Data Type)
- STEndpoint_TSQL
dev_langs: TSQL
helpviewer_keywords: STEndpoint (geometry Data Type)
ms.assetid: 61773c45-b568-4e0c-94da-1310c42de7f5
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4a21e6df17ad412d692ddec777ac6ec11a6328e6
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="stendpoint-geometry-data-type"></a>STEndpoint (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne le point de terminaison d’un **geometry** instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STEndPoint ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geometry**  
  
 Type de retour CLR : **SqlGeometry**  
  
 Type Open Geospatial Consortium (OGC) : **Point**  
  
## <a name="remarks"></a>Notes  
 `STEndPoint()`est l’équivalent de [STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md) (x.NumPoints()).  
  
 Cette méthode retourne null si elle est appelée sur vide **geometry** instance.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `LineString` avec `STGeomFromText()` et utilise `STEndpoint()` pour extraire le point de terminaison du `LineString`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STEndPoint().ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

