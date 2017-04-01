---
title: "Cr&#233;er un rapport mobile tabul&#233; &#224; l’aide de l’extraction | Rapports mobiles Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4d5d80d-370a-4a6d-8b76-698bd5ba5ba6
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Cr&#233;er un rapport mobile tabul&#233; &#224; l’aide de l’extraction | Rapports mobiles Reporting Services
Découvrez comment créer un rapport mobile [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] qui apparaît et fonctionne comme un rapport tabulé à l’aide de l’extraction et des paramètres.

Par exemple, dans ce rapport, les jauges de la partie supérieure fonctionnent comme des onglets. Quand vous cliquez sur la jauge des transports, les données qui se trouvent dans le reste du graphique sont filtrées sur les données relatives aux transports.

![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/06-mobile-report-web-viewer-transportation.png)

En réalité, il s’agit d’un ensemble de cinq rapports, ayant chacun un paramètre différent qui permet de filtrer les données en fonction de la jauge sélectionnée en haut du rapport. 

Pour cet exemple, vous commencez par créer cinq rapports. Ensuite, pour chacun des cinq rapports, vous faites des quatre autres jauges des extractions pour les quatre autres rapports. 

Voici un résumé de ces étapes.

1. Créez un rapport appelé « Ventes » comportant cinq jauges :
     - Ventes
     - Transport
     - Carburant
     - Stockage
     - Dépenses diverses
2. Créez quatre copies du rapport que vous nommerez : 
     - Transport
     - Carburant
     - Stockage
     - Dépenses diverses
3.  Dans le rapport Ventes, définissez chacune des quatre jauges (autres que la jauge Ventes) comme des extractions dans leurs rapports respectifs.

4. Toujours dans le rapport Ventes, définissez la propriété d’accentuation de la jauge Ventes de sorte qu’elle contraste avec le reste du rapport pour la faire ressortir.

5.  Maintenant, dans le rapport Transport, définissez la jauge Ventes comme une extraction dans le rapport Ventes, et les trois autres jauges comme des extractions dans leurs rapports respectifs.

6. Toujours dans le rapport Transport, définissez la propriété d’accentuation de la jauge Transport de sorte qu’elle contraste avec le reste du rapport.

5. Répétez la procédure pour les rapports Carburant, Stockage et Dépenses diverses. 







  
