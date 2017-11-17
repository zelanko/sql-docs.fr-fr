---
title: "M (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- M (geometry Data Type)
- M_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- M (geometry Data Type)
ms.assetid: 443ae2ea-739b-41ef-96cc-ac5dfd65e10b
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0946bc24abaee28973f8afd409ac68d04a428c8d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="m-geometry-data-type"></a>M (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Le **M** valeur (mesure) de le **geometry** instance. La sémantique de la valeur de mesure est définie par l'utilisateur.  

## <a name="syntax"></a>Syntaxe  
  
```  
  
.M  
```  
  
## <a name="arguments"></a>Arguments  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 La valeur de cette propriété a la valeur null si le **geometry** instance n’est pas un **Point**, ainsi que pour les **Point** de l’instance pour laquelle il n’est pas définie.  
  
 Cette propriété est en lecture seule.  
  
 **M** valeurs ne sont pas utilisées dans aucun calcul effectué par la bibliothèque et ne sont reportées dans aucun calcul de bibliothèque.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Point` avec des valeurs Z (élévation) et M (mesure) et utilise `M` pour extraire la valeur M de l'instance.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(1 2 3 4)', 0);  
SELECT @g.M;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances géométriques](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [Z &#40; Type de données geometry &#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)   
 [AsTextZM &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/astextzm-geometry-data-type.md)  
  
  


