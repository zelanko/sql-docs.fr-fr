---
title: Publier une source de données partagée sur une bibliothèque SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], publishing to a SharePoint library
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3159e4b64f19410222c6f2adbbce1a1d2c8782e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188255"
---
# <a name="publish-a-shared-data-source-to-a-sharepoint-library"></a>publier une source de données partagée sur une bibliothèque SharePoint
  Pour publier une source de données partagée sur un serveur de rapports s'exécutant en mode intégré SharePoint, vous devez définir les propriétés du projet de rapport dans le Concepteur de rapports. Dans les propriétés du projet, toutes les références aux serveurs, aux rapports et aux sources de données partagées doivent être des URL complètes.  
  
 Vous devez disposer de l’autorisation **Membre** ou **Propriétaire** sur le site SharePoint. Pour plus d’informations, consultez [Exemples d’URL pour les éléments de rapport publiés sur un serveur de rapports en mode SharePoint &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-shared-data-source-to-a-sharepoint-site"></a>Pour publier une source de données partagée sur un site SharePoint  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez un projet Report Server nouveau ou existant.  
  
2.  Dans le menu **Projet** , cliquez sur **Propriétés**. La boîte de dialogue **Pages de propriétés** de _\<projet_ s’affiche.  
  
3.  Choisissez la **Configuration** que vous utilisez pour publier sur un site SharePoint.  
  
4.  Si vous voulez publier les sources de données partagées dans votre projet et remplacer celles précédemment publiées, attribuez à **OverwriteDataSources** la valeur **True**.  
  
5.  (Facultatif) Pour **TargetDataSourceFolder**, tapez l’URL d’une bibliothèque SharePoint ou d’un dossier de bibliothèque. Par exemple, *http://TestServer/TestSite/Documents/DataSources*.  
  
     Si vous ne spécifiez pas de valeur, la valeur **TargetReportFolder** est utilisée.  
  
6.  Pour **TargetReportFolder**, tapez l’URL d’une bibliothèque ou d’un dossier de bibliothèque. Par exemple, http:*//ServeurTest/SiteTest/Documents/Rapports*.  
  
7.  Pour **TargetServerURL**, tapez l’URL d’un sous-site ou d’un site SharePoint de niveau supérieur. Si vous ne spécifiez aucun site, le site de premier niveau par défaut est utilisé. Par exemple, http://*nomserveur*, http://*nomserveur*/*site*ou http://*nomserveur*/*site*/*sous-site*.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur la source de données partagée à publier, puis cliquez sur **Déployer**. La source de données est publiée à l’emplacement spécifié dans **TargetDataSourceFolder**. Les erreurs de déploiement apparaissent dans la fenêtre Sortie.  
  
    > [!NOTE]  
    >  Une fois que vous avez publié une source de données partagée sur un site SharePoint, l'extension de nom de fichier devient .rsds. Vous pouvez modifier et gérer directement une source de données partagée sur le site SharePoint. Pour plus d’informations, consultez [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>Voir aussi  
 [publier un rapport dans une bibliothèque SharePoint](publish-a-report-to-a-sharepoint-library.md)   
 [Exemples d’URL pour les éléments de rapport publiés sur un serveur de rapports en mode SharePoint &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Pages de propriétés du projet, boîte de dialogue](../tools/project-property-pages-dialog-box.md)   
 [Définir des propriétés de déploiement &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md)   
 [Publication de rapports sur un serveur de rapports](publishing-reports-to-a-report-server.md)   
 [Utiliser une connexion de données Office &#40;.odc&#41; avec les rapports &#40;Reporting Services en mode intégré SharePoint&#41;](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
