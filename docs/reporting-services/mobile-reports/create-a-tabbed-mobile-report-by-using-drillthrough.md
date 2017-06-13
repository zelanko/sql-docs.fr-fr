---
title: "Créer un rapport mobile à onglets à l’aide de l’extraction | Rapports Reporting Services mobiles | Documents Microsoft"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4d5d80d-370a-4a6d-8b76-698bd5ba5ba6
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6554f808c19540d2a3b7cbe3fdf4e86c5fe7a357
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="create-a-tabbed-mobile-report-by-using-drillthrough"></a>Créer un rapport mobile à onglets à l’aide de l’extraction
Découvrez comment créer un rapport mobile [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] qui apparaît et fonctionne comme un rapport tabulé à l’aide de l’extraction et des paramètres.

Par exemple, dans ce rapport, les jauges de la partie supérieure fonctionnent comme des onglets. Quand vous cliquez sur la jauge des transports, les données qui se trouvent dans le reste du graphique sont filtrées sur les données relatives aux transports.

![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/tabbed-mobile-report-web-viewer-transportation-complete.png)

En réalité, il s’agit d’un ensemble de cinq rapports, ayant chacun un paramètre différent qui permet de filtrer les données en fonction de la jauge sélectionnée en haut du rapport. Vous créez d’abord toutes les cinq rapports, puis pour chacun des cinq rapports, apportez les quatre autres jauges dans drillthroughs pour les quatre autres rapports.

Voici les étapes de cet exemple.

## <a name="create-the-basic-report"></a>Créer le rapport de base

1. Créez un rapport appelé « Ventes » comportant cinq jauges :

    * Ventes
    * Transport
    * Carburant
    * Stockage
    * Dépenses diverses

   ![01-ventes-Mobile--éditeur de rapports](../../reporting-services/mobile-reports/media/01-sales-mobile-report-publisher.png)
    
2. Définir **Accent** à **sur** de la jauge de ventes, par conséquent, il sera contraste avec le le reste du rapport--dans ce cas, blanc sur noir.

    ![01a-Sales-accent-mobile-report-Publisher](../../reporting-services/mobile-reports/media/01a-sales-accent-mobile-report-publisher.png)
    
3. Pour enregistrer un [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] serveur de rapports.

## <a name="make-copies-of-the-report"></a>Effectuer des copies du rapport

1. Effectuer des quatre copies du rapport de ventes et les nommer : 

    * Transport
    * Carburant
    * Stockage
    * Dépenses diverses

3. Pour enregistrer le [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] serveur de rapports.

## <a name="set-the-gauge-as-a-drillthrough"></a>Définir la jauge en tant qu’une extraction

Dans cette section, vous définissez chaque jauge (autre que la jauge Sales) comme une extraction à son rapport respectif.

1. Dans le rapport des ventes, sélectionnez l’indicateur de transport.

    ![02-Sales-Create-Drillthrough-mobile-report-Publisher](../../reporting-services/mobile-reports/media/02-sales-create-drillthrough-mobile-report-publisher.png)

2. Avec le **disposition** onglet sélectionné, dans le **propriétés visuelles** panneau, sélectionnez **d’extraction cible**.

3. Sélectionnez **rapport Mobile**.

4. Accédez à et sélectionnez le rapport à la destination pour l’extraction--dans ce cas, « Finances - transport ».

    ![03-Sales-Select-Dashboard-mobile-report-Publisher](../../reporting-services/mobile-reports/media/03-sales-select-dashboard-mobile-report-publisher.png)

5. Dans **configurer le rapport cible**, sélectionnez le paramètre pour filtrer le rapport, puis sélectionnez **appliquer**.

   ![04-Sales-Apply-Parameters-mobile-report-Publisher](../../reporting-services/mobile-reports/media/04-sales-apply-parameters-mobile-report-publisher.png)
   
6. Répétez ces étapes pour chacun des autres les jauges dans le rapport des ventes. 

## <a name="set-the-gauges-for-the-other-reports"></a>Définir les jauges pour les autres rapports

1.  Ouvrez le rapport de transport, définir l’indicateur de ventes comme une extraction dans le rapport des ventes et les trois autres jauges comme drillthroughs à leurs rapports respectifs.

2. Toujours dans le rapport de transport, définissez **Accent** pour l’indicateur de transport pour **sur**, par contraste avec le le reste du rapport.

3. Répétez ces étapes pour les rapports de carburant, de stockage et les frais divers. 

## <a name="view-the-report-in-the-web-portal"></a>Afficher le rapport dans le portail web

1. Accédez à la [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] le serveur de rapports et ouvrez un des rapports. 

2. Notez que chacun de jauge une icône d’extraction dans le coin supérieur droit.

    ![Web-Viewer-drillthrough-icon-mobile-report-builder](../../reporting-services/mobile-reports/media/web-viewer-drillthrough-icon-mobile-report-builder.png)

3. Vous avez le choix entre les jauges pour accéder à l’état filtré pour les données de cette jauge.

   ![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/06-mobile-report-web-viewer-transportation.png)

### <a name="see-also"></a>Voir aussi
    
* [Ajouter des paramètres à un rapport mobile](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)
* [Ajouter l’extraction à partir d’un rapport mobile à d’autres rapports mobiles ou des URL](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)




  


