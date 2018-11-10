---
title: Identificateurs de référence spatiale (SRID) | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0cba308c746bd3cec33742cbdf8231371d18aab3
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018994"
---
# <a name="spatial-reference-identifiers-srids"></a>Identificateurs de référence spatiale (SRID)
  Chaque instance spatiale a un identificateur de référence spatiale (SRID). Le SRID correspond à un système de référence spatial basé sur l'ellipsoïde spécifique utilisée pour le mappage de monde en deux dimensions ou le mappage de monde sphérique.  
  
> [!IMPORTANT]  
>  Pour obtenir une description détaillée et des exemples des fonctionnalités spatiales introduites dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], notamment le nouveau SRID, téléchargez le livre blanc [New Spatial Features in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407)(Nouvelles fonctionnalités spatiales dans SQL Server 2012).  
  
 Une colonne spatiale peut contenir des objets avec des SRID différents. Toutefois, seules des instances spatiales avec le même SRID peuvent être utilisées lors de l'exécution d'opérations avec des méthodes de données spatiales [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur vos données. Le résultat de toute méthode spatiale dérivée de deux instances de données spatiales est valide uniquement si ces instances ont le même SRID basé sur la même unité de mesure, donnée et projection utilisée pour déterminer les coordonnées des instances. Les unités de mesure les plus courantes d'un SRID sont le mètre ou le mètre carré.  
  
 Si deux instances spatiales n'ont pas le même SRID, les résultats d'une méthode de type de données `geometry` ou `geography` utilisée sur les instances retournent NULL. Par exemple, pour que le terme de prédicat suivant retourne un résultat non NULL, les deux instances `geometry`, `geometry1` et `geometry2`, doivent avoir le même SRID :  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  Le système d’identification de référence spatiale est défini par la [norme EPSG (European Petroleum Survey Group)](http://go.microsoft.com/fwlink/?LinkId=99349) , qui regroupe un ensemble de normes développées pour la cartographie, l’arpentage et le stockage de données géodésiques. Cette norme est détenue par l'OGP (Oil and Gas Producers) Surveying and Positioning Committee.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données spatiales](spatial-data-types-overview.md)  
  
  
