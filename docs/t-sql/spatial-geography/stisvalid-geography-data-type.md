---
title: STIsValid (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STIsValid method (geography)
ms.assetid: 1bfe787f-ddf0-4fc7-af6a-570a58faab23
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 62ba3dc8bc64b346ee0818bc4eb6a8b7bb6db088
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65936760"
---
# <a name="stisvalid-geography-data-type"></a>STIsValid (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne true si une instance **geography** est bien formée et reconnue en tant qu’objet geography valide, en fonction de son type OGC (Open Geospatial Consortium). Retourne false si une instance **geography** n’est pas bien formée. Cette méthode est précise.  
  
 Cette méthode de type de données geography prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Vous pouvez déterminer le type OGC d’une instance **geography** en appelant [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] produit uniquement des instances **geography** valides, mais permet le stockage et la récupération d’instances non valides. Une instance valide qui représente le même ensemble de points d'une instance non valide peut être récupérée à l'aide de la méthode `MakeValid()`.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `geography` et utilise `STIsValid()` pour tester si l'instance est valide.  
  
```  
DECLARE @g geography = geography::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 4326);  
SELECT @g.STIsValid();  
DECLARE @g geography  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STGeometryType &#40;type de données geography&#41;](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)   
 [MakeValid &#40;type de données geography&#41;](../../t-sql/spatial-geography/makevalid-geography-data-type.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
