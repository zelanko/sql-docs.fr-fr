---
title: Ajouter des jauges aux rapports mobiles | Reporting Services| Microsoft Docs
description: Vous pouvez ajouter des jauges à un rapport mobile Reporting Services. Les jauges affichent une valeur dans un jeu de données, par elle-même ou par rapport à un objectif.
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 76d8fc8f-c37f-44d3-ab44-45fbeed4e064
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 456c50650afc01fc18465b0d96f3cfeb715ddecb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79448282"
---
# <a name="add-gauges-to-mobile-reports--reporting-services"></a>Ajouter des jauges aux rapports mobiles | Reporting Services
Les jauges sont les éléments visuels les plus simples et les plus utilisés dans les rapports mobiles. Elles affichent une seule valeur dans un dataset (la valeur seule ou la valeur comparée à un objectif).

![PBI_SSMRP_Gauges](../../reporting-services/mobile-reports/media/pbi-ssmrp-gauges.png)  
  
*Visualisation des jauges sous l’onglet Disposition*  
  
Dans l’Éditeur de rapports mobiles SQL Server, toutes les jauges ont au moins une propriété en commun : une valeur principale définie dans un champ numérique d’une des tables de données d’un rapport mobile.  

Toutes les jauges, à l’exception de la jauge Nombre , peuvent aussi présenter une comparaison, c’est-à-dire une valeur *d’écart*(rapport entre la valeur principale et une valeur de comparaison). La valeur de comparaison correspond souvent à l’objectif, et la jauge est un indicateur visuel de la progression vers cet objectif, ou l’écart entre la valeur réelle et l’objectif.

Les jauges ne peuvent représenter qu’une seule valeur agrégée pour leur valeur principale et qu’une seule valeur agrégée pour leur valeur de comparaison. Les agrégations de jauge sont de type standard : somme, moyenne, minimum, maximum, etc. Par défaut, la valeur d’une jauge est une somme. Celle-ci représente le total de l’ensemble des valeurs contenues dans les données filtrées actuelles accessibles au contrôle de la jauge. 

Vous pouvez filtrer les valeurs de jauge en les connectant aux navigateurs du rapport mobile. 

## <a name="set-the-main-and-comparison-values-for-a-gauge"></a>Définir les valeurs principale et de comparaison d’une jauge

1. Faites glisser une jauge de l’onglet **Disposition** vers la grille de création et ajustez sa taille à votre convenance.

2. Obtenez des [données à partir d’Excel ou d’un dataset partagé](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md).

3. Sélectionnez l’onglet **Données** puis, dans le volet **Propriétés des données** , sous **Valeur principale** , sélectionnez une table de données et un champ numérique.

3. Dans n’importe quelle jauge à l’exception de la jauge Nombre, dans le volet **Propriétés des données** , sous **Valeur de comparaison** , sélectionnez une table de données et un champ numérique.

4. [facultatif] Pour modifier l’agrégation, sélectionnez **Options** et choisissez une autre agrégation.
   
   >**Remarque** : si vous modifiez l’agrégation de la valeur principale, vous changerez probablement aussi celle de la valeur de comparaison, sauf si vous voulez mélanger les méthodes d’agrégation.  

## <a name="filter-a-gauge"></a>Filtrer une jauge
  
Si le rapport mobile comporte des navigateurs, vous pouvez lier une jauge à un ou plusieurs d’entre eux de façon à opérer un filtrage. Vous pouvez lier la valeur principale et la valeur de comparaison d’une jauge à un ou plusieurs navigateurs différents, ce qui offre des options presque illimitées en ce qui concerne les jauges.  

1. Après avoir sélectionné une jauge, sous l’onglet **Données** du volet **Propriétés des données** , sélectionnez **Options** en regard de **Valeur principale** ou de **Valeur de comparaison**.

2. Sous Filtré par, sélectionnez le navigateur avec lequel vous voulez filtrer la jauge.

   ![mobile-report-gauge-navigator](../../reporting-services/mobile-reports/media/mobile-report-gauge-navigator.png)
 
## <a name="set-visual-properties-for-a-gauge"></a>Définir les propriétés visuelles d’une jauge
  
Outre les propriétés des données qui permettent de connecter les éléments de jauge à des champs de données, vous pouvez aussi personnaliser un certain nombre de propriétés fonctionnelles et visuelles. 

### <a name="set-value-direction-high-or-low-is-better"></a>Définir le sens des valeurs : Les valeurs hautes/basses sont préférables
* Après avoir sélectionné une jauge, sous l’onglet **Disposition** du volet **Propriétés visuelles** , définissez le **Sens des valeurs** en choisissant **Les valeurs hautes sont préférables** ou **Les valeurs basses sont préférables**. 

**Les valeurs hautes sont préférables** affiche les valeurs positives en vert, indiquant un changement favorable, et affiche les valeurs faibles en rouge, indiquant un changement défavorable. 

Les couleurs pour l’option **Les valeurs basses sont préférables** sont inversées.

La propriété Sens des valeurs concerne uniquement les éléments de jauge qui prennent en charge une valeur de comparaison. La couleur de la jauge est déterminée par le signe de l’entier d’écart et par la définition de la propriété Sens des valeurs.  
  
### <a name="set-range-stops-for-a-gauge"></a>Définir les arrêts de plage d’une jauge
La deuxième propriété propre aux jauges non relative aux données est Arrêts de plage. 

* Après avoir sélectionné une jauge, sous l’onglet **Disposition** du volet **Propriétés visuelles** , sélectionnez **Arrêts de plage**.

Les arrêts de plage vous permettent de définir à quel pourcentage de la valeur de comparaison une visualisation doit être présentée comme étant dans la cible (vert), neutre (orange) et hors cible (rouge), la valeur de comparaison d’une jauge étant la cible. Encore une fois, seules les jauges ayant des valeurs de comparaison prennent en charge les arrêts de plage.  

### <a name="format-the-numbers-in-the-gauge"></a>Mettre en forme les nombres dans la jauge  
Une autre propriété d’élément de jauge non relative aux données, partagée par de nombreux autres éléments, est Format de nombre. 

* Après avoir sélectionné une jauge, sous l’onglet **Disposition** du volet **Propriétés visuelles** , sélectionnez **Arrêts de plage**.

Ce paramètre détermine la façon dont les nombres de la jauge sont mis en forme (par exemple, devise, pourcentage, heure ou général). Vous devez définir la mise en forme pour chaque élément du rapport mobile.
  
### <a name="see-also"></a>Voir aussi 

* [Créer des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)
* [Cartes dans les rapports pour mobiles Reporting Services](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)
* [Navigateurs dans les rapports mobiles Reporting Services](../../reporting-services/mobile-reports/add-navigators-to-reporting-services-mobile-reports.md)
* [Visualisations dans les rapports mobiles Reporting Services](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
* [Grilles de données dans les rapports mobiles Reporting Services](../../reporting-services/mobile-reports/add-data-grids-to-mobile-reports-reporting-services.md) 
