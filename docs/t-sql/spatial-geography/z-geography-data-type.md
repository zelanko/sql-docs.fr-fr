---
title: "Z (Type de données geography) | Documents Microsoft"
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
- Z (geography Data Type)
- Z_(geography_Data_Type)_TSQL
dev_langs: TSQL
helpviewer_keywords: Z method
ms.assetid: 9abc79c5-43c9-4cc2-b37f-d2ecdec7c234
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bca07144b67a65160019d402e819ebed1636abf1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="z-geography-data-type"></a>Z (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Valeur Z (élévation) de l'instance. La sémantique de la valeur d'élévation est définie par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.Z  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 La valeur de cette propriété est null si la **geography** instance n’est pas un point, ainsi que pour toute **Point** de l’instance pour laquelle il n’est pas définie.  
  
 Cette propriété est en lecture seule.  
  
 Les coordonnées Z ne sont utilisées dans aucun calcul effectué par la bibliothèque et ne sont reportées dans aucun calcul de bibliothèque.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Point` avec des valeurs Z (élévation) et M (mesure) et utilise `Z` pour extraire la valeur Z de l'instance.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.Z;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40; Type de données geography &#41;](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [AsTextZM &#40;type de données geography&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
