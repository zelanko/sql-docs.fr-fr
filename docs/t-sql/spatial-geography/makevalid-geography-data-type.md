---
title: "MakeValid (Type de données geography) | Documents Microsoft"
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
dev_langs: TSQL
helpviewer_keywords: MakeValid method (geography)
ms.assetid: f67038e3-4f62-4465-994e-e95ac27d8ada
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 796b06fb230cffbfe813d204017dc58c24d8c5b2
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="makevalid-geography-data-type"></a>MakeValid (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Convertit un **geography** instance qui n’est pas valide dans une commande valide **geography** instance avec un type Open Geospatial Consortium (OGC) valide.  
  
 Si un objet d’entrée retourne False pour STIsValid(), `MakeValid()` convertit l’instance qui n’est pas valide pour une instance valide.  
  
 Ces données geography type prend en charge de la méthode **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **geography**  
  
 Type de retour CLR : **SqlGeography**  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut modifier le type de la **geography** instance. En outre, les points d’un **geography** instance peut-être bouger légèrement. Résultats de certaines méthodes, telles que NumPoint() peuvent changer.  
  
 Dans les cas où l’instance spatiale non valide croise l’Équateur et a une EnvelopeAngle() = 180, une **FullGlobe** instance sera retournée. Le `MakeValid()` **geography** méthode de type de données rendent la meilleure tentative à retourner des instances valides, mais les résultats ne sont pas garantis pour être précis ou précise.  
  
> [!NOTE]  
>  Les objets qui ne sont pas valides peuvent être stockés dans la base de données. Les méthodes qui peuvent être exécutés sur des instances non valides (ces instances pour les STIsValid() retournent False) sont des méthodes qui vérifient la validité ou permettent l’exportation : STIsValid(), MakeValid(), STAsText(), STAsBinary(), ToString(), AsTextZM() et AsGml().  
  
 Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
 Le premier exemple crée une instance `LineString` non valide qui se chevauche elle-même et utilise `STIsValid()` pour confirmer qu'il s'agit d'une instance non valide. `STIsValid()` retourne la valeur 0 pour une instance non valide.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 4326);  
SELECT @g.STIsValid();  
```  
  
 Le deuxième exemple utilise `MakeValid()` pour rendre l'instance valide et tester que l'instance est effectivement valide. `STIsValid()` retourne la valeur 1 pour une instance valide.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 Le troisième exemple vérifie comment l'instance a été modifiée pour en faire une instance valide.  
  
```  
SELECT @g.ToString();  
```  
  
 Dans cet exemple, lorsque l'instance `LineString` est sélectionnée, les valeurs sont retournées en tant qu'instance `MultiLineString` valide.  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STIsValid &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
