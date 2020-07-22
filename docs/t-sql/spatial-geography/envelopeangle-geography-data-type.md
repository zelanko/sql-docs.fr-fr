---
title: EnvelopeAngle (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 2066a2874094e3a6e4f7376809d26cbcbaba9e81
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555443"
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (type de données geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Retourne l’angle maximal entre le point retourné par `EnvelopeCenter()` et un point de l’instance **geography** en degrés.  
  
 Cette méthode de type de données **geography** prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EnvelopeAngle( )  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne un point de l’instance **geography** en degrés. En cas d’utilisation avec EnvelopeCenter(), `EnvelopeAngle()` retourne un cercle englobant d’une instance **geography**.  
  
 Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], cette méthode a été étendue aux instances **FullGlobe**.  
  
 La limitation d’hémisphère appliquée à `EnvelopeAngle()` dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a été supprimée. Toutefois, pour les instances avec des angles supérieurs à 90 degrés, 180 degrés sont retournés. `EnvelopeAngle()` n’est pas précis pour les instances **geography** qui couvrent plusieurs hémisphères.  
  
## <a name="examples"></a>Exemples  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40;type de données geography&#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  
