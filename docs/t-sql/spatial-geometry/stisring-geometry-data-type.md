---
title: STIsRing (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsRing_TSQL
- STIsRing (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsRing (geometry Data Type)
ms.assetid: ea0063be-1c74-4cc4-ac6f-b65321ddfa54
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a9aa9b1b8e97f78887710309019e80ff4276c732
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030886"
---
# <a name="stisring-geometry-data-type"></a>STIsRing (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne 1 si une instance **geometry** répond aux exigences suivantes :
-   Il s’agit d’une instance **LineString**.  
-   Elle est fermée.  
-   Elle est simple.  
-   Retourne 0 si l’instance **LineString** ne répond pas aux exigences.  

 Pour qu’une instance **geometry** soit fermée et simple, [STIsClosed()](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md) et [STIsSimple()](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md) doivent retourner 1 quand ils sont appelés sur l’instance. Pour déterminer le type d’instance de **geometry**, utilisez [STGeometryType()](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIsRing ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne une valeur Null si l’instance n’est pas **LineString**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `LineString` et utilise `STIsRing()` pour tester si l'instance est un anneau.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0, 0 0)', 0);  
SELECT @g.STIsRing();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [STIsClosed &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [STGeometryType &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)   
 [STIsSimple &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/stissimple-geometry-data-type.md)   
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

