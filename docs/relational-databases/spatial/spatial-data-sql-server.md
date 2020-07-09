---
title: Données spatiales (SQL Server) | Microsoft Docs
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 32014323cf9921cdbff9db6235e6625b4dc431ec
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725869"
---
# <a name="spatial-data-sql-server"></a>Données spatiales (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Données spatiales représentent des informations sur l’emplacement physique et la forme d’objets géométriques. Ces objets peuvent être des emplacements précis ou des objets plus complexes, tels que des pays, des routes ou des lacs.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge deux types de données spatiales : le type de données **geometry** et le type de données **geography** .  
  
-   Le type **geometry** représente des données dans un système de coordonnées euclidien (plat).  
  
-   Le type **geography** représente des données dans un système de coordonnées de monde sphérique.  
  
 Ces deux types de données sont implémentés comme types de données CLR .NET dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> Tâches associées  
 [Créer, construire et interroger des instances géométriques](../../relational-databases/spatial/create-construct-and-query-geometry-instances.md)  
 Décrit les méthodes que vous pouvez utiliser avec des instances du type de données geometry.  
  
 [Créer, construire et interroger des instances géographiques](../../relational-databases/spatial/create-construct-and-query-geography-instances.md)  
 Décrit les méthodes que vous pouvez utiliser avec des instances du type de données geography.  
  
 [Interroger des données spatiales au sujet du plus proche voisin](../../relational-databases/spatial/query-spatial-data-for-nearest-neighbor.md)  
 Décrit le modèle de requête commun qui est utilisé pour rechercher les objets spatiaux les plus proches d'un objet spatial spécifique.  
  
 [Créer, modifier et supprimer des index spatiaux](../../relational-databases/spatial/create-modify-and-drop-spatial-indexes.md)  
 Fournit des informations sur la création, la modification et la suppression d'un index spatial.  
  
## <a name="related-content"></a>Contenu associé  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)  
 Présente les types de données spatiales.  
  
-   [Point](../../relational-databases/spatial/point.md)  
  
-   [LineString](../../relational-databases/spatial/linestring.md)  
  
-   [CircularString](../../relational-databases/spatial/circularstring.md)  
  
-   [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)  
  
-   [Polygon](../../relational-databases/spatial/polygon.md)  
  
-   [CurvePolygon](../../relational-databases/spatial/curvepolygon.md)  
  
-   [MultiPoint](../../relational-databases/spatial/multipoint.md)  
  
-   [MultiLineString](../../relational-databases/spatial/multilinestring.md)  
  
-   [MultiPolygon](../../relational-databases/spatial/multipolygon.md)  
  
-   [GeometryCollection](../../relational-databases/spatial/geometrycollection.md)  
  
 [Vue d’ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)  
 Présente les index spatiaux et décrit le pavage et les schémas de pavage.  
  
  
