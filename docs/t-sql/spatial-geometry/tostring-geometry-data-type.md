---
title: "ToString (Type de données geometry) | Documents Microsoft"
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
- ToString (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString (geometry Data Type)
ms.assetid: 2e55fa98-aa22-4baa-a516-7c233a33e212
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 614ecad2f669fed40ac5fd7ca30b994bedb0ac6e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="tostring-geometry-data-type"></a>ToString (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d'une instance geometry augmentée de valeurs Z (élévation) et M (mesure) apportées par l'instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **nvarchar (max)**  
  
 Type de retour CLR : **SqlString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne la chaîne « Null » lorsqu’elle est appelée sur les instances null.  
  
 Sur les instances non Null, cette méthode est équivalente à `AsTextZM().`  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée un `LineString` instance et utilise `ToString()` pour obtenir la description textuelle de l’instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STAsText &#40; Type de données geometry &#41;](../../t-sql/spatial-geometry/stastext-geometry-data-type.md)   
 [Méthodes étendues sur des instances geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

