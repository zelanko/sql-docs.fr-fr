---
title: Long (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Long_TSQL
- Long
dev_langs:
- TSQL
helpviewer_keywords:
- Long method
ms.assetid: bedbeced-70b8-4569-84f3-f86bfb04ce50
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: dd2424bff6322ad388ef6980c0055b098433cf40
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731127"
---
# <a name="long-geography-data-type"></a>Long (type de données geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Propriété de longitude de l’instance **geography**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.Long  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes  
 Dans le modèle OpenGIS, Long est défini uniquement sur les instances **geography** composées d’un seul point. Cette propriété retourne NULL si les instances **geography** contiennent plusieurs points. Cette propriété est précise et en lecture seule.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée une instance **Point** et récupère la longitude du point.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.Long;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
