---
title: Publier des rapports | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
caps.latest.revision: 37
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: ff9106915fb683583b800688548703833c5ba0e9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140682"
---
# <a name="publish-reports"></a>Publier des rapports
  À partir de[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vous pouvez publier l’ensemble des rapports et sources de données partagées dans un projet de serveur de rapports sur un serveur de rapports en déployant le projet, ou vous pouvez publier un rapport unique. Avant de pouvoir publier un rapport, vous devez spécifier l'URL du serveur de rapports cible. Pour plus d’informations, consultez [Définir des propriétés de déploiement &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md).  
  
 Vous pouvez utiliser la [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] version de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour ouvrir, modifier, afficher un aperçu, enregistrer et publier les deux [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] et [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] des rapports. Pour plus d’informations, consultez [Déploiement et prise en charge des versions dans les outils de données SQL Server &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
### <a name="to-publish-all-reports-in-a-project"></a>Pour publier tous les rapports d'un projet  
  
-   Dans le menu **Générer**, cliquez sur **Déployer \<nom_projet_rapport>**. Vous pouvez également, dans l’Explorateur de solutions, cliquer avec le bouton droit sur le projet de rapport, puis cliquer sur **Déployer**. Vous pouvez consulter l'état du processus de publication dans la fenêtre Sortie.  
  
    > [!NOTE]  
    >  Lorsque vous déployez un projet Report Server, les sources de données partagées dans le projet de rapport sont également déployées.  
  
### <a name="to-publish-a-single-report"></a>Pour publier un seul rapport  
  
-   Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le rapport, puis cliquez sur **Déployer**. Vous pouvez consulter l'état du processus de publication dans la fenêtre Sortie.  
  
    > [!NOTE]  
    >  Lorsque vous publiez un rapport, vous devez également déployer les sources de données partagées que le rapport utilise.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication des sources de données et des rapports](reports/publishing-data-sources-and-reports.md)   
 [Aperçu des rapports](reports/previewing-reports.md)   
 [Publication de rapports sur un serveur de rapports](reports/publishing-reports-to-a-report-server.md)   
 [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportation de rapports &#40;rapport Générateur et SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  