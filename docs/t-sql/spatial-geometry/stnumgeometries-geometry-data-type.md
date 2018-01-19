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
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0feeee76b0d8da2f3636f6f66e49c350bee1c243
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
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
  
  

