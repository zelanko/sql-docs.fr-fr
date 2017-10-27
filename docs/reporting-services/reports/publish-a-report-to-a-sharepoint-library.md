---
title: "Publier un rapport dans une bibliothèque SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 88caf60aea658972b79c49948d882ce5f96e1d07
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="publish-a-report-to-a-sharepoint-library"></a>publier un rapport dans une bibliothèque SharePoint
  Pour publier un rapport sur un site SharePoint configuré pour l'intégration SharePoint, vous devez définir les propriétés du projet dans le Concepteur de rapports. Dans les propriétés du projet, toutes les références aux serveurs, aux rapports et aux sources de données partagées doivent être des URL complètes. Dans la définition de rapport, toutes les références aux sous-rapports, aux rapports d'extraction et aux ressources, telles que des images Web, doivent être des URL complètes.  
  
 Vous devez avoir l’autorisation de **Membre** ou de **Propriétaire** sur le site SharePoint pour définir les propriétés du projet. Pour plus d’informations, consultez [Exemples d’URL pour les éléments de rapport publiés sur un serveur de rapports en mode SharePoint &#40;SSRS&#41;](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a>Pour publier un rapport sur un site SharePoint  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez un projet Report Server nouveau ou existant.  
  
2.  Dans le menu **Projet** , cliquez sur **Propriétés**. Le  *\<projet >***Pages de propriétés** boîte de dialogue s’ouvre.  
  
3.  Dans la liste **Configuration** , sélectionnez le nom d’une configuration de build de solution à utiliser pour générer et publier votre rapport. La configuration actuelle est répertoriée en tant que **Active**(*\<configuration >*).  
  
4.  Si vous voulez publier les sources de données partagées dans votre projet et remplacer celles précédemment publiées, attribuez à **OverwriteDataSources** la valeur **True**.  
  
5.  (Facultatif) Pour **TargetDataSourceFolder**, tapez une URL vers une bibliothèque SharePoint ou un dossier de bibliothèque (par exemple, `http://TestServer/TestSite/Documents/DataSources`).  
  
     Si vous ne spécifiez pas de valeur, la valeur **TargetReportFolder** est utilisée.  
  
6.  Pour **TargetReportFolder**, tapez une URL vers une bibliothèque ou un dossier de bibliothèque (par exemple, `http://TestServer/TestSite/Documents/Reports`).  
  
7.  Pour **TargetServerURL**, tapez une URL vers un sous-site ou un site SharePoint de niveau supérieur. Si vous ne spécifiez pas de site, le site de niveau supérieur par défaut est utilisé (par exemple, `http://servername`, `http://servername/site`ou `http://servername/site/subsite`).  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le rapport à publier, puis cliquez sur **Déployer**. Le rapport est publié à l’emplacement spécifié dans **TargetReportFolder**. Les erreurs de déploiement apparaissent dans la fenêtre Sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Pages de propriétés du projet, boîte de dialogue](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [Définir des propriétés de déploiement &#40;Reporting Services&#41;](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
 [Publier des rapports sur un serveur de rapports](../../reporting-services/reports/publishing-reports-to-a-report-server.md)   
 [Exemples d’URL pour les éléments de rapport publiés sur un serveur de rapports en mode SharePoint &#40;SSRS&#41;](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Utilisez une connexion de données Office &#40;. ODC &#41; les rapports &#40; Reporting Services dans SharePoint intégré en Mode &#41;](../../reporting-services/report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  

