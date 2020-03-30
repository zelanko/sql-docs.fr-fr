---
title: Lat (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Lat
- Lat_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Lat method
ms.assetid: 051d66bc-04de-4c58-861c-760dc5b859b5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7da6aca6ccc5180d379ff853267d2de9f682cfb9
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68040093"
---
# <a name="lat-geography-data-type"></a>Lat (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Propriété de latitude de l’instance **geography**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.Lat  
```  
  
## <a name="return-types"></a>Types de retour  
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 Dans le modèle OpenGIS, Lat est défini uniquement sur les instances **geography** composées d’un seul point. Cette propriété retourne NULL si les instances **geography** contiennent plusieurs points. Cette propriété est précise et en lecture seule.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée un point et retourne la latitude du point.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Lat;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
