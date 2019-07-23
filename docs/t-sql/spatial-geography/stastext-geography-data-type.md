---
title: STAsText (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STAsText (geography Data Type)
- STAsText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STAsText method
ms.assetid: d3d2635d-ca6c-4205-9d6c-eb939ee314fd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 9050e529cd851d5b6785e3e167c1c081a2079dd5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042502"
---
# <a name="stastext-geography-data-type"></a>STAsText (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) d’une instance **geography**. Ce texte ne contiendra aucune valeur Z (élévation) ou M (mesure) apportée par l'instance.  
  
 Cette méthode de type de données **geography** prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **nvarchar(max)**  
  
 Type de retour CLR : **SqlChars**  
  
## <a name="remarks"></a>Notes  
 Vous pouvez déterminer le type OGC d’une instance **geography** en appelant [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md).  
  
 Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le jeu de résultats possibles retourné sur le serveur a été étendu aux instances **FullGlobe**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STAsText()` pour créer une instance `LineString``geography` de (-122.360, 47.656) à (-122.343, 47.656) à partir d’un texte. Il retourne alors le résultat sous forme textuelle.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
