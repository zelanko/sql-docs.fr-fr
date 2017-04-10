---
title: "D&#233;marrer le G&#233;n&#233;rateur de rapports | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Générateur de rapports, lancement"
  - "lancement du Générateur de rapports"
  - "intégration SharePoint [Reporting Services], démarrage du Générateur de rapports"
  - "démarrage du Générateur de rapports"
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 56
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 56
---
# D&#233;marrer le G&#233;n&#233;rateur de rapports
  Le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est un environnement de création de rapports autonome. Il vous permet de créer des rapports paginés et de les publier dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé en mode natif ou en mode intégré SharePoint.  
  
 La première fois que vous démarrez [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] à partir du portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode intégré SharePoint, vous êtes invité à le télécharger à partir du Centre de téléchargement Microsoft. 
 
![report-builder-get-report-builder](../../reporting-services/report-builder/media/report-builder-get-report-builder.png) 
 
 Le Générateur de rapports peut également être [installé sur votre ordinateur par un administrateur ou par vous-même à partir du Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=219138). Pour plus d’informations, consultez « Installer le Générateur de rapports avec Systems Manager Server » dans [Installer le Générateur de rapports](../../reporting-services/install-windows/install-report-builder.md).
 
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] n’est pas installé lorsque vous installez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]; vous devez le télécharger et l’installer séparément.  
  
 Lorsque vous démarrez le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] à partir du portail web ou d’un site SharePoint et qu’une version antérieure du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] s’ouvre, contactez votre administrateur, qui pourra mettre à jour la version sur le portail web ou sur le site SharePoint.  
  
## Pour démarrer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] à partir du portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
1.  Dans le navigateur Web, tapez l'URL du serveur de rapports dans la barre d'adresses. Par défaut, l’URL est http://\<*nom_serveur*>/reports.  
  
2.  Dans la barre supérieure du portail web, sélectionnez **Nouveau** > **Rapport paginé**.  
  
     ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png "PBI_SSMRP_NewMenu")  
  
     La première fois, vous êtes invité à [installer le Générateur de rapports](../../reporting-services/install-windows/install-report-builder.md). 
  
     Ensuite, [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] s’ouvre, et vous pouvez alors créer un rapport paginé ou ouvrir un rapport à partir du serveur de rapports.  
  
## Pour démarrer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] en mode intégré SharePoint  
  
1.  Naviguez jusqu'au site SharePoint qui contient la bibliothèque souhaitée.  
  
2.  Ouvrez la bibliothèque.  
  
3.  Cliquez sur **Documents**.  
  
4.  Dans le menu **Nouveau document** , cliquez sur **Rapport du Générateur de rapports**.  
  
     Lorsque vous l’effectuez pour la première fois, cette opération lance l’Assistant [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] SQL Server. Pour plus d'informations, consultez [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md) .  
  
     [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] s’ouvre, et vous pouvez alors créer un rapport paginé ou ouvrir un rapport sur le serveur de rapports.  
  
     **Remarque** Si le menu **Nouveau document** n’inclut pas **Rapport du Générateur de rapports**, **Modèle du générateur de rapports**ni **Source de données du rapport**, il convient d’ajouter les types de contenus correspondants à la bibliothèque SharePoint. Pour plus d’informations, consultez [Ajouter des types de contenus Reporting Services à une bibliothèque SharePoint](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
## Voir aussi  
 [Générateur de rapports dans SQL Server 2016](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [Définir les options par défaut du Générateur de rapports](../../reporting-services/report-builder/set-default-options-for-report-builder.md)  
  
  