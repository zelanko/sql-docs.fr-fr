---
description: Identificateurs de référence spatiale (SRID)
title: Identificateurs de référence spatiale (SRID) | Microsoft Docs
ms.date: 03/29/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 40c2a26425815d75ab000000e2639320769b01b9
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92006238"
---
# <a name="spatial-reference-identifiers-srids"></a>Identificateurs de référence spatiale (SRID)
[!INCLUDE [SQL Server Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/sql-asdb-asdbmi.md)]
  Chaque instance spatiale a un identificateur de référence spatiale (SRID). Le SRID correspond à un système de référence spatial basé sur l'ellipsoïde spécifique utilisée pour le mappage de monde en deux dimensions ou le mappage de monde sphérique.  
  
 Une colonne spatiale peut contenir des objets avec des SRID différents. Toutefois, seules des instances spatiales avec le même SRID peuvent être utilisées lors de l'exécution d'opérations avec des méthodes de données spatiales [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur vos données. Le résultat de toute méthode spatiale dérivée de deux instances de données spatiales est valide uniquement si ces instances ont le même SRID basé sur la même unité de mesure, donnée et projection utilisée pour déterminer les coordonnées des instances. Les unités de mesure les plus courantes d'un SRID sont le mètre ou le mètre carré.  
  
 Si deux instances spatiales n’ont pas le même SRID, les résultats d’une méthode de type de données **geometry** ou **geography** utilisée sur les instances retournent NULL. Par exemple, pour que le terme de prédicat suivant retourne un résultat non NULL, les deux instances **geometry** , `geometry1` et `geometry2`, doivent avoir le même SRID :  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  Le système d’identification de référence spatiale est défini par la [norme EPSG (European Petroleum Survey Group)](https://go.microsoft.com/fwlink/?LinkId=99349) , qui regroupe un ensemble de normes développées pour la cartographie, l’arpentage et le stockage de données géodésiques. Cette norme est détenue par l'OGP (Oil and Gas Producers) Surveying and Positioning Committee.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
