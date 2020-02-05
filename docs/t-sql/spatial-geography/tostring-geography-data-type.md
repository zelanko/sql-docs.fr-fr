---
title: ToString (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ToString (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- ToString method
ms.assetid: 045c12fa-8fc6-441a-9500-7021cb4ff13e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3e4ca89d9fa8dccf2e819e76db188f84b25f0b59
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68120681"
---
# <a name="tostring-geography-data-type"></a>ToString (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d’une instance **geography**, à laquelle s’ajoutent les valeurs Z (élévation) et M (mesure) apportées par l’instance.  
  
 Cette méthode de type de données geography prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.ToString ()  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **nvarchar(max)**  
  
 Type de retour CLR : **SqlString**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne la chaîne « Null » lorsqu'elle est appelée sur des instances Null. Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le jeu de résultats possibles sur le serveur a été étendu aux instances **FullGlobe**. Cette méthode retourne la même valeur que `AsTextZM()`.  
  
 Cette méthode n'est pas précise.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une instance `LineString` et utilise `ToString()` pour retourner la description textuelle de l’instance.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [AsTextZM &#40;type de données geography&#41;](../../t-sql/spatial-geography/astextzm-geography-data-type.md)  
  
  
