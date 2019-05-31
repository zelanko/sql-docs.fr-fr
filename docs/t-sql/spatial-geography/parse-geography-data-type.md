---
title: Parse (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Parse method
- Parse (geography Data Type)
ms.assetid: 21c402fa-fd0f-4d09-a097-49cee0316d4e
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 023af0279bdb848e299ec1dbe31ff82305ad109a
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65935906"
---
# <a name="parse-geography-data-type"></a>Parse (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une instance **geography** à partir d’une représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text). Parse() équivaut à [STGeomFromText](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md). Toutefois, cela suppose un SRID (ID de référence spatiale) ayant la valeur 4326 en tant que paramètre. L'entrée peut contenir des valeurs Z (élévation) et M (mesure) facultatives.
  
Cette méthode de type de données **geography** prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Parse ( 'geography_tagged_text' )  
```  
  
## <a name="arguments"></a>Arguments  
 *geography_tagged_text*  
 Représentation WKT de l’instance **geography** à retourner. *geography_tagged_text* est une expression **nvarchar**.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Le type OGC de l’instance **geography** retournée par `Parse()` a comme valeur l’entrée WKT correspondante.  
  
 La chaîne « Null » est interprétée en tant qu’instance **geography** ayant une valeur Null.  
  
 Cette méthode lève **ArgumentException** si l’entrée contient une arête antipodale.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise la méthode `Parse()` pour créer une instance `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Parse('LINESTRING(-122.360 47.656, -122.343 47.656)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geography statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)   
 [STGeomFromText &#40;type de données geography&#41;](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
  
  
