---
title: Cartes et régions de données (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data regions
ms.assetid: 3afb8874-b36c-4e44-a0d8-80d2f7135fb1
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: a130b04ab18fc22bf1a028cea38d093e4b48f24c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206639"
---
# <a name="data-regions-and-maps-report-builder-and-ssrs"></a>Cartes et régions de données (Générateur de rapports et SSRS)
  Une région de données est un objet d'un rapport, affichant des données à partir du dataset d'un rapport. Les données de rapport peuvent s'afficher sous forme de nombres et de texte dans une table, une matrice ou une liste ; graphiquement dans un graphique ou une jauge ; et par rapport à l'arrière-plan géographique d'un plan. Les tables, matrices et listes sont toutes basées sur la région de données du *tableau matriciel* , lequel peut se développer autant que nécessaire pour afficher toutes les données du dataset. Une région de données de tableau matriciel prend en charge plusieurs groupes de lignes et de colonnes statiques et dynamiques. Un graphique affiche plusieurs séries et catégories de groupes sous divers formats graphiques. Une jauge affiche une valeur unique ou une valeur agrégée pour un dataset. Une carte affiche les données spatiales en tant qu'éléments cartographiques dont l'apparence peut varier selon les données agrégées d'un dataset.  
  
 Vous pouvez enregistrer une région de données ou la mapper en tant que partie du rapport. [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="table"></a>Table de charge de travail  
 Une table est une région de données qui présente les données ligne par ligne. Les colonnes de table sont statiques : vous déterminez le nombre de colonnes lorsque vous concevez votre rapport. Les lignes de table sont dynamiques : elles s'étendent vers le bas pour contenir les données. Vous pouvez ajouter aux tables des groupes, qui organisent les données par champs ou expressions sélectionnés. Pour plus d’informations sur l’ajout d’une table à un rapport, consultez [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md).  
  
## <a name="matrix"></a>Matrice  
 Une matrice est également connue sous le nom d'analyse croisée. Une région de données de type matrice contient à la fois des colonnes et des lignes dynamiques : elles s'étendent pour contenir les données. Une matrice peut posséder des lignes et des colonnes dynamiques, ainsi que des lignes et des colonnes statiques. Les colonnes ou les lignes peuvent contenir d'autres colonnes ou lignes ; en outre, elles peuvent être utilisées pour regrouper des données. Pour plus d’informations sur l’ajout d’une matrice à un rapport, consultez [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)  
  
## <a name="list"></a>Liste  
 Une liste est une région de données qui présente les données selon une disposition libre. Vous pouvez organiser les éléments de rapport de façon à créer un formulaire avec des zones de texte, des images et d'autres régions de données placées aux emplacements de votre choix dans la liste. Pour plus d’informations sur l’ajout d’une liste à un rapport, consultez [répertorie &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
## <a name="chart"></a>Graphique  
 Un graphique présente les données graphiquement. Les exemples de graphiques courants sont les graphiques à barres, à secteurs et en courbes, mais de nombreux autres styles de graphiques sont pris en charge. Pour plus d’informations sur l’ajout d’un graphique à un rapport, consultez [graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
## <a name="gauge"></a>Jauge  
 Une jauge présente les données sous forme de plage dans laquelle figure un indicateur qui pointe vers une valeur spécifique. Les jauges sont utilisées pour afficher des indicateurs de performance clés (KPI) et d'autres mesures. Les jauges linéaires et circulaires sont des exemples de jauges. Pour plus d’informations sur l’ajout d’une jauge à un rapport, consultez [jauges &#40;Générateur de rapports et SSRS&#41;](gauges-report-builder-and-ssrs.md).  
  
## <a name="map"></a>Carte  
 Une carte vous permet de présenter des données avec un arrière-plan géographique. Les données cartographiques peuvent être des données spatiales d'une requête [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un fichier de forme ESRI ou des mosaïques Bing [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Les données spatiales sont des jeux des coordonnées qui définissent des polygones représentant des formes ou des zones, des lignes représentant des itinéraires ou des chemins d'accès, et des points représentés par des marqueurs. Vous pouvez associer des données agrégées aux éléments cartographiques pour varier automatiquement leur couleur et taille. Par exemple, vous pouvez faire varier le type de marqueur pour un magasin selon le chiffre d'affaires réalisé ou la couleur pour une route en fonction de la limite de vitesse. Pour plus d’informations, consultez [Cartes &#40;Générateur de rapports et SSRS&#41;](maps-report-builder-and-ssrs.md).  
  
## <a name="data-regions-in-the-report-layout"></a>Régions de données dans la Disposition du rapport  
 Vous pouvez ajouter plusieurs régions de données à un rapport. Les régions de données grandissent de façon à héberger les données du dataset du rapport auquel elles sont liées. Par exemple, une matrice qui affiche les ventes de chaque produit par année compte un groupe de lignes correspondant aux noms de produits et un groupe de colonnes correspondant aux années. Lorsque vous exécutez le rapport, la matrice se développe vers le bas de la page pour chaque produit et à travers la page pour chaque année. Un graphique placé en regard de la matrice sur l'aire de conception du rapport s'affiche en regard de la matrice développée dans le rapport rendu. La façon dont les régions de données sont restituées sur une page obéit à un jeu de règles basées sur le format de sortie du rapport. Par exemple, pour mieux contrôler la façon dont un graphique et une matrice sont restitués sur une page, vous pouvez utiliser un rectangle comme conteneur ou imbriquer les deux régions de données sur une liste. Pour plus d’informations, consultez [mise en Page et rendu &#40;Générateur de rapports et SSRS&#41;](page-layout-and-rendering-report-builder-and-ssrs.md).  
  
## <a name="nested-data-regions"></a>Régions de données imbriquées  
 Vous pouvez imbriquer des régions de données dans d'autres régions de données. Par exemple, si vous souhaitez créer un rapport des ventes pour chaque commercial existant dans une base de données, vous pouvez créer une liste contenant des zones de texte et une image pour afficher des informations sur un employé. Vous pouvez ensuite ajouter des régions de données de type table et graphique à la liste pour afficher les ventes accomplies par cet employé. Pour plus d’informations, consultez [Régions de données imbriquées &#40;Générateur de rapports et SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md).  
  
## <a name="multiple-data-regions-linked-to-the-same-dataset"></a>Plusieurs régions de données liées à un même dataset  
 Vous pouvez lier plusieurs régions de données à un même dataset pour fournir différentes vues des mêmes données. Par exemple, vous pouvez afficher les mêmes données dans une table et dans un graphique. Vous pouvez créer un rapport avec des boutons de tri interactifs sur la table, de sorte que lorsque vous triez la table, le graphique est également trié automatiquement. Pour plus d’informations, consultez [liaison de plusieurs régions de données à un même Dataset &#40;Générateur de rapports et SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md).  
  
## <a name="data-for-a-data-region"></a>Données d'une région de données  
 Chaque tableau matriciel, graphique et jauge est conçu pour afficher des données à partir d'un dataset unique. Une carte affiche des données spatiales et des données analytiques à partir d'un même dataset ou de datasets différents. Vous pouvez également inclure des valeurs provenant de datasets non liés à la région de données selon les méthodes suivantes :  
  
-   Valeurs agrégées qui ne dépendent pas de l'ordre de tri ou du regroupement et étendues à un dataset différent.  
  
-   Valeurs de recherche à partir de paires nom/valeur d'un dataset différent.  
  
 Pour plus d’informations, consultez [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de création de rapports &#40;Générateur de rapports et SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Rapports, parties de rapports et définitions de rapport &#40;Générateur de rapports et SSRS&#41;](reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Mise en page et rendu &#40;Générateur de rapports et SSRS&#41;](page-layout-and-rendering-report-builder-and-ssrs.md)   
 [Didacticiels &#40;Générateur de rapports&#41;](../report-builder-tutorials.md)   
 [Didacticiels sur Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  
