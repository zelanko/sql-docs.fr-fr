---
title: "STNumGeometries (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
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
- STNumGeometries (geometry Data Type)
- STNumGeometries_TSQL
dev_langs: TSQL
helpviewer_keywords: STNumGeometries (geometry Data Type)
ms.assetid: 9402b03d-3039-42ca-ac59-f96b7f1a48de
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f1909f0d094ce1cfe170389de6ccd9c57f5503a8
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="stnumgeometries-geometry-data-type"></a>STNumGeometries (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne le nombre de géométries qui composent un **geometry** instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STNumGeometries ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **int**  
  
 Type de retour CLR : **SqlInt32**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne 1 si le **geometry** instance n’est pas un **MultiPoint**, **MultiLineString**, **MultiPolygon**, ou **GeometryCollection** instance et 0 si le **geometry** instance est vide.  
  
> [!NOTE]  
>  Si un **GeometryCollection** a imbriqué des éléments vides, `STNumGeometries()` ne retournera pas 0. Bien que les éléments dans le **GeometryCollection** instance sont vides, l’instance elle-même n’est pas un ensemble vide.  
  
  

