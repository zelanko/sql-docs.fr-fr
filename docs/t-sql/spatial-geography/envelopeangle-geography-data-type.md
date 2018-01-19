---
title: "EnvelopeAngle (Type de données geography) | Documents Microsoft"
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
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs: TSQL
helpviewer_keywords: EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b7eaef8384500d63acee0d5fae1183d4928bcca
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne l’angle maximal entre le point retourné par `EnvelopeCenter()` et un point dans le **geography** instance en degrés.  
  
 Cela **geography** prend en charge de la méthode de type de données **FullGlobe** instances ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un point dans le **geography** instance en degrés. Lorsqu’il est utilisé avec EnvelopeCenter(), `EnvelopeAngle()` retourne un cercle englobant d’un **geography** instance.  
  
 Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], cette méthode a été étendue aux **FullGlobe** instances.  
  
 La limitation d’hémisphère appliquée à `EnvelopeAngle()` dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a été supprimé. Toutefois, pour les instances avec des angles supérieurs à 90 degrés, 180 degrés sont retournés. `EnvelopeAngle()`n’est pas précis pour **geography** instances qui couvrent plusieurs hémisphères.  
  
## <a name="examples"></a>Exemples  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40; Type de données geography &#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  
