---
title: STX (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STX (geometry Data Type)
- STX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STX (geometry Data Type)
ms.assetid: 2aef77e8-0460-43f9-bad6-2aae6d8c36f9
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: f22b505e0fbb49790b855b0839530d9208477071
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65935581"
---
# <a name="stx-geometry-data-type"></a>STX (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Propriété de coordonnée X d’une instance **Point**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STX  
```  
  
## <a name="return-types"></a>Types de retour  
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 La valeur de cette propriété est Null si l’instance **geometry** n’est pas un point.  
  
 Cette propriété est en lecture seule.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Point` et utilise `STX` pour extraire la coordonnée X de l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STX;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STY &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/sty-geometry-data-type.md)   
 [STSrid &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

