---
title: Mapper la boîte de dialogue Propriétés de la fenêtre d’affichage, général | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 33849743e47ad910fad44938e7537d7b4be8624a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018181"
---
# <a name="map-viewport-properties-dialog-box-general"></a>Boîte de dialogue Propriétés du point de vue de la carte, Général
  Sélectionnez **Général** dans la boîte de dialogue **Propriétés de la fenêtre d'affichage de la carte** pour modifier le système de coordonnées, la projection et les options de limite.  
  
## <a name="options"></a>Options  
 **Système de coordonnées**  
 Indiquez le type de système de coordonnées utilisé par les données de la carte.  
  
-   **Planaire** Choisissez cette option lorsque les données cartographiques sont des coordonnées X et Y, par exemple pour des plans de bâtiment.  
  
-   **Géographique** Choisissez cette option lorsque les données cartographiques sont des coordonnées de longitude et de latitude, par exemple pour l'emplacement des villes.  
  
 **Projection**  
 Spécifiez la méthode à utiliser pour projeter des coordonnées géographiques sur une surface à deux dimensions. Choisissez une projection compatible avec les données que vous visualisez. Les quatre propriétés spatiales affectées par la projection sont la zone, la forme, la distance et la direction. Pour des vues du monde, le choix de projection approprié dépend du centre d'affichage, des limites de la carte et du facteur de zoom.  
  
 Chacune des projections suivantes conserve une ou plusieurs de ces propriétés spatiales :  
  
-   **Équirectangulaire** Choisissez cette option pour utiliser la longitude et la latitude comme coordonnées rectangulaires.  
  
-   **Mercator** Choisissez cette projection couramment utilisée pour les zones peu étendues, pour réduire la distorsion autour de l'équateur ou lorsque vous souhaitez ajouter une couche à une couche de mosaïques existante utilisant la projection Mercator.  
  
-   **Robinson** Choisissez cette option pour réduire la distorsion de zones étendues allant de l'équateur jusqu'aux pôles. Développée par Arthur H. Robinson en 1963.  
  
-   **Fahey** Choisissez cette option pour réduire la distorsion des zones étendues allant de l'équateur jusqu'aux pôles. Développée par Lawrence Fahey en 1975.  
  
-   **Eckert1** Choisissez cette option pour utiliser des parallèles à intervalles réguliers en latitude et des lignes droites pour les méridiens en longitude.  
  
-   **Eckert3** Choisissez cette option pour utiliser des parallèles à intervalles réguliers en latitude et des lignes courbes pour les méridiens en longitude.  
  
-   **HammerAitoff** Choisissez cette option pour les cartes polaires ou mondiales.  
  
-   **Wagner3** Choisissez cette option pour les cartes mondiales.  
  
-   **Bonne** Choisissez cette option pour afficher le monde tel qu'il est présenté dans un atlas.  
  
 **Options de saut de page**  
 Sélectionnez des options pour indiquer comment le contenu sera ajusté à une page du rapport.  
  
 **Options de limite**  
 Spécifiez les limites inférieure et supérieure des coordonnées pour contrôler quelle partie de la carte s'affiche dans le rapport.  
  
 **X minimal**  
 Valeur X la plus basse. Disponible uniquement pour l'option **Planaire** .  
  
 **X maximal**  
 Valeur X la plus élevée. Disponible uniquement pour l'option **Planaire** .  
  
 **Y minimal**  
 Valeur Y la plus basse. Disponible uniquement pour l'option **Planaire** .  
  
 **Y maximal**  
 Valeur Y la plus élevée. Disponible uniquement pour l'option **Planaire** .  
  
 **Longitude minimale**  
 Valeur de longitude la plus basse. Disponible uniquement pour l'option **Géographique** .  
  
 **Longitude maximale**  
 Valeur de longitude la plus élevée. Disponible uniquement pour l'option **Géographique** .  
  
 **Latitude minimale**  
 Valeur de latitude la plus basse. Disponible uniquement pour l'option **Géographique** .  
  
 **Latitude maximale**  
 Valeur de latitude la plus élevée. Disponible uniquement pour l'option **Géographique** .  
  
## <a name="see-also"></a>Voir aussi  
 [Cartes &#40;Générateur de rapports et SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)  
  
  
