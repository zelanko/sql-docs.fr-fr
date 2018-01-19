---
title: "Parse (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 07/30/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- Parse method
- Parse (geography Data Type)
ms.assetid: 21c402fa-fd0f-4d09-a097-49cee0316d4e
caps.latest.revision: "18"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 32d8925fdf53a1d0bcac33719348138b354376c2
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="parse-geography-data-type"></a>Parse (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un **geography** instance à partir d’une représentation de la réplication continue en cluster (WKT, Open Geospatial Consortium (OGC) Well-Known Text). Parse() équivaut à [STGeomFromText](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md), sauf qu’il suppose une référence spatiale (SRID ID) de 4326 comme paramètre. L'entrée peut contenir des valeurs Z (élévation) et M (mesure) facultatives.
  
Cela **geography** prend en charge de la méthode de type de données **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Parse ( 'geography_tagged_text' )  
```  
  
## <a name="arguments"></a>Arguments  
 *geography_tagged_text*  
 Est la représentation WKT de le **geography** instance à retourner. *geography_tagged_text* est un **nvarchar** expression.  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Le type OGC de le **geography** instance retournée par `Parse()` est définie sur l’entrée WKT correspondante.  
  
 La chaîne « Null » est interprétée comme une valeur null **geography** instance.  
  
 Cette méthode lève **ArgumentException** si l’entrée contient un contour antipode.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `Parse()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Parse('LINESTRING(-122.360 47.656, -122.343 47.656)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes géographiques statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)   
 [STGeomFromText &#40;type de données geography&#41;](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
  
  
