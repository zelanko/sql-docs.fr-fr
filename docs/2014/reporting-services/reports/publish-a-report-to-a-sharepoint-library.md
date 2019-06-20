---
title: Publier un rapport dans une bibliothèque SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1cc957af5596acbf2478d55645b1386283970e33
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66102531"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a>publier un rapport dans une bibliothèque SharePoint
  Pour publier un rapport sur un site SharePoint configuré pour l'intégration SharePoint, vous devez définir les propriétés du projet dans le Concepteur de rapports. Dans les propriétés du projet, toutes les références aux serveurs, aux rapports et aux sources de données partagées doivent être des URL complètes. Dans la définition de rapport, toutes les références aux sous-rapports, aux rapports d'extraction et aux ressources, telles que des images Web, doivent être des URL complètes.  
  
 Vous devez avoir l’autorisation de **Membre** ou de **Propriétaire** sur le site SharePoint pour définir les propriétés du projet. Pour plus d’informations, consultez [Exemples d’URL pour les éléments de rapport publiés sur un serveur de rapports en mode SharePoint &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a>Pour publier un rapport sur un site SharePoint  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez un projet Report Server nouveau ou existant.  
  
2.  Dans le menu **Projet** , cliquez sur **Propriétés**. La boîte de dialogue **Pages de propriétés** de _\<projet_ s’affiche.  
  
3.  Dans la liste **Configuration** , sélectionnez le nom d’une configuration de build de solution à utiliser pour générer et publier votre rapport. La configuration actuelle est répertoriée comme **Active**( *\<configuration>* ).  
  
4.  Si vous voulez publier les sources de données partagées dans votre projet et remplacer celles précédemment publiées, attribuez à **OverwriteDataSources** la valeur **True**.  
  
5.  (Facultatif) Pour **TargetDataSourceFolder**, tapez une URL vers une bibliothèque SharePoint ou un dossier de bibliothèque (par exemple, *http://TestServer/TestSite/Documents/DataSources)* .  
  
     Si vous ne spécifiez pas de valeur, la valeur **TargetReportFolder** est utilisée.  
  
6.  Pour **TargetReportFolder**, tapez une URL vers une bibliothèque ou un dossier de bibliothèque (par exemple, *http://TestServer/TestSite/Documents/Reports)* .  
  
7.  Pour **TargetServerURL**, tapez l’URL d’un sous-site ou d’un site SharePoint de niveau supérieur. Si vous ne spécifiez pas un site, le site de niveau supérieur par défaut est utilisé (par exemple, *http://servername* , *http://servername/site* , ou *http://servername/site/subsite* ).  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le rapport à publier, puis cliquez sur **Déployer**. Le rapport est publié à l’emplacement spécifié dans **TargetReportFolder**. Les erreurs de déploiement apparaissent dans la fenêtre Sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Pages de propriétés du projet, boîte de dialogue](../tools/project-property-pages-dialog-box.md)   
 [Définir des propriétés de déploiement &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md)   
 [Publication de rapports sur un serveur de rapports](publishing-reports-to-a-report-server.md)   
 [Exemples d’URL pour les éléments de rapport publiés sur un serveur de rapports en mode SharePoint &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Utiliser une connexion de données Office &#40;.odc&#41; avec les rapports &#40;Reporting Services en mode intégré SharePoint&#41;](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
