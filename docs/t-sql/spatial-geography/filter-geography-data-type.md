---
title: "Filtre (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- Filter
- Filter_TSQL
- Filter (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: Filter method
ms.assetid: 82a8f54a-3a47-4e20-b13a-b148029c5448
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5d85017831deaef0a0aa0a57b96fb40618520d3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="filter-geography-data-type"></a>Filter (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Une méthode qui offre une méthode rapide index uniquement d’intersection pour déterminer si un **geography** instance croise une autre **geography** instance, en supposant un index est disponible.  
  
 Retourne 1 si une **geography** instance potentiellement entre en intersection avec une autre **geography** instance. Cette méthode peut produire un retour de faux positif, et le résultat exact peut dépendre du plan. Retourne une valeur 0 exacte (retour négatif vrai) s’il n’existe aucune intersection de **geography** instance a été trouvée.  
  
 Dans le cas où un index n’est pas disponible ou n’est pas utilisé, la méthode retourne les mêmes valeurs que **STIntersects()** lorsqu’elle est appelée avec les mêmes paramètres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.Filter ( other_geography )  
```  
  
## <a name="arguments"></a>Arguments  
 *other_geography*  
 Une autre **geography** instance à comparer à l’instance sur laquelle Filter() est appelée.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Cette méthode n'est pas déterministe et n'est pas précise.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `Filter()` pour déterminer si deux instances `geography` entrent en intersection.  
  
```  
CREATE TABLE sample (id int primary key, g geography);  
INSERT INTO sample VALUES  
   (0, geography::Point(45, -120, 4326)),  
   (1, geography::Point(45, -120.1, 4326)),  
   (2, geography::Point(45, -120.2, 4326)),  
   (3, geography::Point(45, -120.3, 4326)),  
   (4, geography::Point(45, -120.4, 4326));  
  
CREATE SPATIAL INDEX sample_idx on sample(g);  
SELECT id  
FROM sample   
WHERE g.Filter(geography::Parse(  
   'POLYGON((-120.1 44.9, -119.9 44.9, -119.9 45.1, -120.1 45.1, -120.1 44.9))')) = 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [STIntersects &#40; Type de données geography &#41;](../../t-sql/spatial-geography/stintersects-geography-data-type.md)  
  
  
