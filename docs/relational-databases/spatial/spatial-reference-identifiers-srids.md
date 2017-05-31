---
title: "Identificateurs de référence spatiale (SRID) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 57420f270daa88e61add4810a7792ed6fdea8278
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="spatial-reference-identifiers-srids"></a>Identificateurs de référence spatiale (SRID)
  Chaque instance spatiale a un identificateur de référence spatiale (SRID). Le SRID correspond à un système de référence spatial basé sur l'ellipsoïde spécifique utilisée pour le mappage de monde en deux dimensions ou le mappage de monde sphérique.  
  
> [!IMPORTANT]  
>  Pour obtenir une description détaillée et des exemples des fonctionnalités spatiales introduites dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], notamment le nouveau SRID, téléchargez le livre blanc [New Spatial Features in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407)(Nouvelles fonctionnalités spatiales dans SQL Server 2012).  
  
 Une colonne spatiale peut contenir des objets avec des SRID différents. Toutefois, seules des instances spatiales avec le même SRID peuvent être utilisées lors de l'exécution d'opérations avec des méthodes de données spatiales [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur vos données. Le résultat de toute méthode spatiale dérivée de deux instances de données spatiales est valide uniquement si ces instances ont le même SRID basé sur la même unité de mesure, donnée et projection utilisée pour déterminer les coordonnées des instances. Les unités de mesure les plus courantes d'un SRID sont le mètre ou le mètre carré.  
  
 Si deux instances spatiales n’ont pas le même SRID, les résultats d’une méthode de type de données **geometry** ou **geography** utilisée sur les instances retournent NULL. Par exemple, pour que le terme de prédicat suivant retourne un résultat non NULL, les deux instances **geometry** , `geometry1` et `geometry2`, doivent avoir le même SRID :  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  Le système d’identification de référence spatiale est défini par la [norme EPSG (European Petroleum Survey Group)](http://go.microsoft.com/fwlink/?LinkId=99349) , qui regroupe un ensemble de normes développées pour la cartographie, l’arpentage et le stockage de données géodésiques. Cette norme est détenue par l'OGP (Oil and Gas Producers) Surveying and Positioning Committee.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
