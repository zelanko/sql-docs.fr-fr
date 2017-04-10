---
title: "Donn&#233;es spatiales (SQL&#160;Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-non-specified"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "type de données geography [SQL Server], conception de stockage spatial"
  - "données spatiales planaires [SQL Server], conception"
  - "types de données spatiales [SQL Server]"
  - "données spatiales géodésiques [SQL Server]"
  - "type de données geometry [SQL Server], conception de stockage spatial"
  - "stockage spatial [SQL Server]"
  - "données spatiales geodésiques [SQL Server], conception"
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Donn&#233;es spatiales (SQL&#160;Server)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Les données spatiales représentent des informations relatives à l'emplacement physique et à la forme d'objets géométriques. Ces objets peuvent être des emplacements de points ou des objets plus complexes tels que des pays, des routes ou des lacs.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge deux types de données spatiales : le type de données **geometry** et le type de données **geography**.  
  
-   Le type **geometry** représente des données dans un système de coordonnées euclidien (plat).  
  
-   Le type **geography** représente des données dans un système de coordonnées de monde sphérique.  
  
 Ces deux types de données sont implémentés comme types de données CLR .NET dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Pour obtenir une description détaillée et des exemples des fonctionnalités spatiales introduites dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], téléchargez le livre blanc intitulé [New Spatial Features in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407) (Nouvelles fonctionnalités spatiales dans SQL Server 2012).  
  
##  <a name="reltasks"></a> Tâches associées  
 [Créer, construire et interroger des instances geometry](../../relational-databases/spatial/create-construct-and-query-geometry-instances.md)  
 Décrit les méthodes que vous pouvez utiliser avec des instances du type de données geometry.  
  
 [Créer, construire et interroger des instances geography](../../relational-databases/spatial/create-construct-and-query-geography-instances.md)  
 Décrit les méthodes que vous pouvez utiliser avec des instances du type de données geography.  
  
 [Interroger des données spatiales au sujet du plus proche voisin](../../relational-databases/spatial/query-spatial-data-for-nearest-neighbor.md)  
 Décrit le modèle de requête commun qui est utilisé pour rechercher les objets spatiaux les plus proches d'un objet spatial spécifique.  
  
 [Créer, modifier et supprimer les index spatiaux](../../relational-databases/spatial/create-modify-and-drop-spatial-indexes.md)  
 Fournit des informations sur la création, la modification et la suppression d'un index spatial.  
  
## Contenu connexe  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)  
 Présente les types de données spatiales.  
  
-   [Point](../../relational-databases/spatial/point.md)  
  
-   [LineString](../../relational-databases/spatial/linestring.md)  
  
-   [CircularString](../../relational-databases/spatial/circularstring.md)  
  
-   [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)  
  
-   [Polygone](../../relational-databases/spatial/polygon.md)  
  
-   [CurvePolygon](../../relational-databases/spatial/curvepolygon.md)  
  
-   [MultiPoint](../../relational-databases/spatial/multipoint.md)  
  
-   [MultiLineString](../../relational-databases/spatial/multilinestring.md)  
  
-   [MultiPolygon](../../relational-databases/spatial/multipolygon.md)  
  
-   [GeometryCollection](../../relational-databases/spatial/geometrycollection.md)  
  
 [Vue d'ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)  
 Présente les index spatiaux et décrit le pavage et les schémas de pavage.  
  
  