---
title: STY (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STY_TSQL
- STY (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STY (geometry Data Type)
ms.assetid: f72e0eaa-7d1d-4052-88fd-a172d8cb0d71
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: a6744060b9ef3a6500c68d772645f12ecf8f2909
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65935589"
---
# <a name="sty-geometry-data-type"></a>STY (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Propriété de coordonnée Y d’une instance **Point**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STY  
```  
  
## <a name="return-types"></a>Types de retour  
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 La valeur de cette propriété est Null si l’instance **geometry** est un point. Cette propriété est en lecture seule.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Point` et utilise `STY` pour extraire la coordonnée Y de l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 8)', 0);  
SELECT @g.STY;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STX &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stx-geometry-data-type.md)   
 [STSrid &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stsrid-geometry-data-type.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

