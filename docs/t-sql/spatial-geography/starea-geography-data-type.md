---
title: "STArea (Type de données geography) | Documents Microsoft"
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
- STArea (geography Data Type)
- STArea_TSQL
dev_langs: TSQL
helpviewer_keywords: STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d183c65aaaa21a36d6b157e230c79d7c38f2aecf
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="starea-geography-data-type"></a>STArea (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la surface d’exposition totale d’un **geography** instance. Les résultats de STArea() sont renvoyés dans le carré de l’unité de mesure utilisée par l’identificateur de référence spatiale de la **geography** instance ; par exemple, si le SRID de l’instance est 4326, STArea() retourne des résultats en mètres carrés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 STArea() retourne 0 si une **geography** instance contient uniquement des figures à 0 et 1-dimension, ou si elle est vide.  
  
> [!NOTE]  
>  Les méthodes sur le **geography** qui produisent une mesure de retourner la valeur aura des résultats différents selon le SRID de l’instance utilisée dans la méthode de type de données. Pour plus d’informations sur les SRID, consultez [des identificateurs de référence spatiale &#40; SRID &#41; ](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STArea()` pour créer un `Polygon``geography` de l’instance et calcule la surface du polygone.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
