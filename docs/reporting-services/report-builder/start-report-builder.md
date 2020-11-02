---
title: Démarrer le Générateur de rapports | Microsoft Docs
description: Le Générateur de rapports est un environnement de création de rapports autonome. La première fois que vous le lancer, le Centre de téléchargement Microsoft vous invite à le télécharger.
ms.date: 01/03/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 00a954a23cf9b17a58c3272a03222019400ae891
ms.sourcegitcommit: ea0bf89617e11afe85ad85309e0ec731ed265583
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907037"
---
# <a name="start-report-builder"></a>Démarrer le Générateur de rapports

[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] est un environnement de création de rapports autonome. Il vous permet de créer des rapports paginés et de les publier dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé en mode natif ou en mode intégré SharePoint.  

> [!NOTE]
> L’intégration de Reporting Services à SharePoint n’est plus disponible après SQL Server 2016.
  
 La première fois que vous démarrez [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir du portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode intégré SharePoint, vous êtes invité à le télécharger à partir du Centre de téléchargement Microsoft. 
 
![Capture d’écran du message « Nous ouvrons le Générateur de rapports... »](../../reporting-services/report-builder/media/report-builder-get-report-builder.png) 
 
 Le Générateur de rapports peut également être [installé sur votre ordinateur par un administrateur ou par vous-même à partir du Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/?LinkID=219138). Pour plus d’informations, consultez « Installer le Générateur de rapports avec Systems Manager Server » dans [Installer le Générateur de rapports](../../reporting-services/install-windows/install-report-builder.md) .
 
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] n’est pas installé lorsque vous installez SQL Server Reporting Services ; vous devez le télécharger et l’installer séparément.  
  
 Lorsque vous démarrez le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir du portail web ou d’un site SharePoint et qu’une version antérieure du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] s’ouvre, contactez votre administrateur, qui pourra mettre à jour la version sur le portail web ou sur le site SharePoint.  
  
## <a name="to-start-ssrbnoversion-from-the-ssrsnoversion-web-portal"></a>Pour démarrer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] à partir du portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
1.  Dans le navigateur Web, tapez l'URL du serveur de rapports dans la barre d'adresses. Par défaut, l’URL est https://\<*servername*>/reports.  
  
2.  Dans la barre supérieure du portail web, sélectionnez **Nouveau** > **Rapport paginé** .  
  
     ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png "PBI_SSMRP_NewMenu")  
  
     La première fois, vous êtes invité à [installer le Générateur de rapports](../../reporting-services/install-windows/install-report-builder.md). 
  
     Ensuite, [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] s’ouvre, et vous pouvez alors créer un rapport paginé ou ouvrir un rapport à partir du serveur de rapports.  
  
## <a name="to-start-ssrbnoversion-in-sharepoint-integrated-mode"></a>Pour démarrer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] en mode intégré SharePoint  
  
1.  Naviguez jusqu'au site SharePoint qui contient la bibliothèque souhaitée.  
  
2.  Ouvrez la bibliothèque.  
  
3.  Cliquez sur **Documents** .  
  
4.  Dans le menu **Nouveau document** , cliquez sur **Rapport du Générateur de rapports** .  
  
     Lorsque vous l’effectuez pour la première fois, cette opération lance l’Assistant [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] SQL Server. Pour plus d'informations, consultez [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md) .  
  
     Le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion.md)] s’ouvre, et vous permet de créer un rapport paginé ou d’ouvrir un rapport sur le serveur de rapports.  
  
     **Remarque** Si le menu **Nouveau document** n’inclut pas **Rapport du Générateur de rapports** , **Modèle du générateur de rapports** ni **Source de données du rapport** , il convient d’ajouter les types de contenus correspondants à la bibliothèque SharePoint. Pour plus d’informations, consultez [Ajouter des types de contenus Reporting Services à une bibliothèque SharePoint](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  

## <a name="next-steps"></a>Étapes suivantes

[Générateur de rapports dans SQL Server](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
[Définir les options par défaut du Générateur de rapports](../../reporting-services/report-builder/set-default-options-for-report-builder.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
