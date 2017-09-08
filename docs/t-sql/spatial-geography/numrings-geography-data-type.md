---
title: "NumRings (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NumRings_TSQL
- NumRings
dev_langs:
- TSQL
helpviewer_keywords:
- NumRings method
ms.assetid: 0e4e4fa2-b608-4cc4-98ba-0845ddb4214c
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a27cb4953f8ca0ca51ec6d3fdef80ae27dd976a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="numrings-geography-data-type"></a>NumRings (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le nombre total d’anneaux dans une **polygone** instance. Dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** type, externe et internes anneaux ne sont pas distinguées, comme tout anneau peut être accepté comme étant l’anneau externe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.NumRings ()  
```  
  
## <a name="return-type"></a>Type de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **int**  
  
 Type de retour CLR : **SqlInt32**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne NULL si ce n’est pas un **polygone** d’instance et retourne 0 si l’instance est vide. Cette méthode est précise.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée une instance `Polygon` avec deux anneaux et confirme qu'elle a deux anneaux.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.NumRings();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
