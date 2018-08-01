---
title: Ajouter des paramètres à un rapport mobile | Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: mobile-reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 113cb057-deec-40eb-abc8-f35d3900eaa6
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1a854a49884c6a2f1bd93794a7854d30dc1e2d3d
ms.sourcegitcommit: d4392c68eb5f15b175165cf03ef8253565323d68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39359606"
---
# <a name="add-parameters-to-a-mobile-report--reporting-services"></a>Ajouter des paramètres à un rapport mobile | Reporting Services
Vous pouvez créer un rapport mobile [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] avec des paramètres, afin que vous et les lecteurs de vos rapports puissiez filtrer vos rapports. Un rapport avec des paramètres peut également être la cible d’une [extraction dans un rapport source](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md). 

Pour créer un rapport mobile avec des paramètres, vous commencez avec un dataset partagé comportant au moins un paramètre. Découvrez comment [créer des paramètres dans un dataset partagé](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md). Les rapports mobiles ne prennent pas en charge les valeurs de type Null pour les paramètres par défaut, alors assurez-vous que vos paramètres ont des valeurs par défaut différentes de Null.

Une fois que vous avez ajouté les paramètres à un rapport mobile, vous créez une URL afin d’ [ouvrir le rapport avec des paramètres de chaîne de requête](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md). 

1. Dans la barre située en haut du portail web de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] , sélectionnez **Nouveau** > **Rapport mobile**.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. Sélectionnez l’onglet **Données** dans le coin en haut à gauche de [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)].   
  
3. Dans le coin en haut à droite, sélectionnez **Ajouter des données**.  
  
4. Sélectionnez **Serveur de rapports**, puis sélectionnez un serveur.  
  
5. Accédez aux datasets partagés sur le serveur, puis sélectionnez-en un qui possède des paramètres.  
  
   Dans la grille, vous voyez les données contenues dans le dataset. Le cercle vert avec des accolades **{ }** marque un ensemble de données avec un paramètre.  
     
   ![SSMRP_PforParam](../../reporting-services/mobile-reports/media/ssmrp-pforparam.png)  
  
6. Sélectionnez l’icône de rouage sous l’onglet, puis sélectionnez **Param {}**.  
  
   ![SSMRP_ParamWheel](../../reporting-services/mobile-reports/media/ssmrp-paramwheel.png)  
  
7. Sélectionnez l’élément de rapport qui transmettra des valeurs au paramètre.  
  
   ![SSMRP_SetParam](../../reporting-services/mobile-reports/media/ssmrp-setparam.png)  
     
8. Sélectionnez **Aperçu** afin de découvrir l’apparence du rapport. Dans ce rapport, la liste des sélections utilise le paramètre de catégorie.

   ![sql-server-mobile-report-publisher-Selection-List-View-No-Selection](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-view-no-selection.png) 
   
9. Quand vous sélectionnez une valeur dans la liste de sélections, le rapport est filtré sur cette valeur, dans le cas présent Accessories.

   ![sql-server-mobile-report-publisher-Selection-List-Category-Selected](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-category-selected.png)   
  
### <a name="see-also"></a>Voir aussi  
-  [Ouvrir un rapport mobile avec des paramètres spécifiques de chaîne de requête](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters-reporting-services.md)
-  [Ajouter l’extraction à partir d’un rapport mobile à d’autres rapports mobiles ou des URL](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)
-  [Créer un dataset partagé ou incorporé](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)
- [Créer et publier des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
  
  

