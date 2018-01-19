---
title: "Long (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 06/02/2016
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
- Long_TSQL
- Long
dev_langs: TSQL
helpviewer_keywords: Long method
ms.assetid: bedbeced-70b8-4569-84f3-f86bfb04ce50
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d88f9cdf318296b48a47efdd6b9e9b13c1ac2e43
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="long-geography-data-type"></a>Long (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  La propriété de longitude de le **geography** instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.Long  
```  
  
## <a name="return-value"></a>Valeur retournée  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 Dans le modèle OpenGIS, durée pendant laquelle est défini uniquement sur **geography** instances composé d’un point unique. Cette propriété retourne NULL si **geography** instances contiennent plus d’un point unique. Cette propriété est précise et en lecture seule.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée un **Point** de l’instance et extrait la longitude du point.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Long;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
