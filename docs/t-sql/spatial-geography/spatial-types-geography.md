---
title: "géographie (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- geography
dev_langs:
- TSQL
helpviewer_keywords:
- geography data type [SQL Server], Transact-SQL
- spatial data types [SQL Server]
ms.assetid: d9e4952a-1841-4465-a64b-11e9288dba1d
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3525cc718e5e0efddd6cef2e3f2cff57247058c2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="spatial-types---geography"></a>Types de données spatiales - geography
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Le type de données spatiales géographiques, **geography**, est implémenté comme un common language runtime (CLR) type de données .NET dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ce type représente des données dans un système de coordonnées de monde sphérique. Le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** stocke des données ellipsoïdes, telles que des coordonnées de latitude et de longitude GPS.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]prend en charge un ensemble de méthodes pour la **geography** type de données spatiales. Cela inclut des méthodes sur **geography** qui sont définies par la norme Open Geospatial Consortium (OGC) et un ensemble de [!INCLUDE[msCoName](../../includes/msconame-md.md)] extensions de cette norme.  
 
 La tolérance d’erreur pour le **geography** méthodes peuvent être aussi volumineux que 1.0E-7 * étendues. Les extensions de faire référence à la distance maximale approximative entre les points de la **geography**objet.
  

## <a name="registering-the-geography-type"></a>Inscription du type geography  
 Le type **geography** est prédéfini et disponible dans chaque base de données. Vous pouvez créer des colonnes de table de type **geography** et opérer sur les données **geography** comme vous le feriez avec d’autres types fournis par le système. Peut être utilisé dans les colonnes calculées persistantes et non persistantes.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-showing-how-to-add-and-query-geography-data"></a>A. Illustration de l'ajout et de l'interrogation de données géographiques  
 Les exemples suivants montrent comment ajouter et interroger des données géographiques. Le premier exemple crée une table avec une colonne d’identité et une `geography` colonne, `GeogCol1`. Une troisième colonne restitue la colonne `geography` dans sa représentation OGC (Open Geospatial Consortium) WKT (Well-Known Text) et utilise la méthode `STAsText()` . Deux lignes sont ensuite insérées : une ligne contient une instance `LineString` de `geography`et une ligne contient une instance `Polygon` .  
  
```  
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable   
    ( id int IDENTITY (1,1),  
    GeogCol1 geography,   
    GeogCol2 AS GeogCol1.STAsText() );  
GO  
  
INSERT INTO SpatialTable (GeogCol1)  
VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656 )', 4326));  
  
INSERT INTO SpatialTable (GeogCol1)  
VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653 , -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
GO  
```  
  
### <a name="b-returning-the-intersection-of-two-geography-instances"></a>B. Retour de l'intersection de deux instances géographiques  
 L'exemple suivant utilise la méthode `STIntersection()` pour retourner les points où les deux instances `geography` précédemment insérées se croisent.  
  
```  
DECLARE @geog1 geography;  
DECLARE @geog2 geography;  
DECLARE @result geography;  
  
SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
SELECT @result = @geog1.STIntersection(@geog2);  
SELECT @result.STAsText();  
```  
  
### <a name="c-using-geography-in-a-computed-column"></a>C. Utilisation du type géographique dans une colonne calculée  
 L’exemple suivant crée une table avec une colonne calculée persistante à l’aide un **geography** type.  
  
```  
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable  
(  
    locationId int IDENTITY(1,1),  
    location geography,  
    deliveryArea as location.STBuffer(10) persisted  
)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Données spatiales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   

  
  

