---
title: "STSrid (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STSrid (geometry Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid (geometry Data Type)
ms.assetid: 5e0de983-a0fe-48b7-9e08-30588d7271e2
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9e8e29a1a5446713c94462bdcf4d0c252875d7c0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="stsrid-geometry-data-type"></a>STSrid (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** est un entier qui représente l’identificateur de référence spatiale de l’instance.  
  
Cette propriété peut être modifiée.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STSrid  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type : **int**  
  
 Type CLR : **SqlInt32**  
  
## <a name="examples"></a>Exemples  
 Le premier exemple crée un **geometry** de l’instance avec la valeur de SRID 13 et utilise `STSrid` pour confirmer le SRID.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0))', 13);  
SELECT @g.STSrid;  
```  
  
 Le deuxième exemple utilise `STSrid` pour modifier la valeur de SRID de l'instance à 23, puis confirme la valeur SRID modifiée.  
  
```  
SET @g.STSrid = 23;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STX &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STY &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [Méthodes OGC sur les Instances géométriques](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


