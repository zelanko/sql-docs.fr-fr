---
title: "Points de donn&#233;es vides et Null dans les graphiques (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
caps.latest.revision: 10
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 10
---
# Points de donn&#233;es vides et Null dans les graphiques (G&#233;n&#233;rateur de rapports et SSRS)
  Si vous affichez des champs avec des valeurs vides ou null dans un graphique de votre rapport paginé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], l’aspect du graphique peut ne pas correspondre à vos attentes. Les graphiques traitent les valeurs vides différemment en fonction du type de graphique spécifié :  
  
-   Si le type de graphique est un type de graphique linéaire (graphique à barres, histogramme, graphique en nuage de points, graphique en courbes, graphique en aires, graphique d'étendue), les valeurs vides sont affichées sous forme d'espaces vides, ou « vides », dans le graphique. Si vous souhaitez spécifier des points vides, vous devez ajouter des espaces réservés à ces points. Pour plus d’informations, consultez [Ajouter des points vides à un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md).  
  
-   Si le graphique utilisé est un graphique linéaire contigu (graphique à aires, graphique à barres, histogramme, graphique en courbes, graphique à nuages de points), des points de données vides y sont ajoutés pour maintenir la continuité dans les séries.  
  
-   Si le graphique utilisé est un graphique non linéaire (polaire, à secteurs, en anneau, en entonnoir ou en pyramide), les valeurs vides n'y sont pas affichées.  
  
-   Dans les types de graphiques à base de formes, les valeurs Null sont omises.  
  
 Un exemple de graphique avec des points de données vides est disponible sous forme d'exemple de rapport. Pour plus d'informations sur le téléchargement de cet exemple de rapport et d'autres rapports, consultez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Exemples de rapports du Générateur de rapports et du Concepteur de rapports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Suppression de valeurs vides ou Null  
 Pour éviter de masquer des données importantes, envisagez la suppression des valeurs vides de votre dataset. Pour filtrer les valeurs Null, vous pouvez utiliser la clause NOT IS NULL dans votre requête. Vous pouvez également ajouter une expression de filtrage qui spécifie que vous ne voulez afficher que les valeurs différentes de zéro. Pour plus d’informations, consultez [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add dataset filters, data region filters, and group filters.md).  
  
## Champs sans valeurs dans un graphique  
 Si un champ ne contient aucune valeur dans le dataset retourné, le graphique affiche un graphique vide sans point de données, mais le nom de la série (en général, le nom du champ) est ajouté en tant qu'élément de légende.  
  
 Ce comportement est différent du cas où il n'y a aucune ligne de données dans le dataset retourné, ce qui peut se produire lorsque le rapport est paramétré et que la valeur sélectionnée retourne un jeu de résultats vide. Si votre requête de dataset retourne zéro ligne de données, un message s'affiche au moment de l'exécution pour indiquer qu'aucune donnée ne peut être présentée. Vous pouvez personnaliser ce message en modifiant la légende NoDataMessage pour le rapport dans le volet **Propriétés**. Pour plus d’informations, consultez [Datasets incorporés dans les rapports et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Ajouter un graphique à un rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)   
 [Résoudre les problèmes liés aux graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/troubleshoot-charts-report-builder-and-ssrs.md)  
  
  