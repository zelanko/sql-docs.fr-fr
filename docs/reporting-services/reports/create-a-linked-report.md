---
title: "Cr&#233;er un rapport li&#233; | Microsoft Docs"
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
  - "rapports liés [Reporting Services], création"
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
caps.latest.revision: 44
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 44
---
# Cr&#233;er un rapport li&#233;
  Un rapport lié est un élément de serveur de rapports qui fournit un point d'accès à un rapport existant. Au niveau conceptuel, il est assimilable au raccourci d'un programme que vous utilisez pour exécuter une application ou ouvrir un fichier.  
  
 Un rapport lié est issu d'un rapport existant et il reste fidèle à la définition de rapport d'origine. Il hérite toujours des propriétés de la source de données et de la mise en page du rapport d'origine. Toutes les autres propriétés et toutes les autres valeurs peuvent différer, notamment la sécurité, les paramètres, l'emplacement, les abonnements et les planifications.  
  
 Vous créez un rapport lié lorsque vous voulez créer des versions supplémentaires d'un rapport existant. Ainsi, vous pouvez trouver pratique d'utiliser un rapport de ventes régional unique pour créer des rapports spécifiques aux régions pour tous vos secteurs de ventes.  
  
 Bien que les rapports liés soient généralement basés sur des rapports paramétrés, il n'est pas obligatoire de recourir à des rapports paramétrés. Vous pouvez créer des rapports liés dès lors que vous souhaitez déployer un rapport existant avec des paramètres différents.  
  
### Pour créer un rapport lié  
  
1.  Dans le Gestionnaire de rapports, accédez au dossier qui contient le rapport à lier, puis ouvrez le menu d’options et cliquez sur **Créer un rapport lié**.  
  
2.  Indiquez un nom pour le nouveau rapport lié. Tapez éventuellement une description.  
  
3.  Pour sélectionner un autre dossier pour le rapport, cliquez sur **Modifier l’emplacement**. Cliquez ensuite sur le dossier à utiliser ou tapez son nom dans la zone **Emplacement**. [!INCLUDE[clickOK](../../includes/clickok-md.md)] Si vous ne sélectionnez aucun dossier, le rapport lié est créé dans le dossier actif (où est stocké le rapport sur lequel il est basé).  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Le rapport lié s’ouvre.  
  
     L'icône d'un rapport lié est différente des autres éléments gérés par un serveur de rapports. L'icône ci-après indique un rapport lié :  
  
     ![Icône Rapport lié](../../reporting-services/report-server/media/hlp-16linked.png "Icône Rapport lié")  
  
## Voir aussi  
 [Ouvrir et fermer un rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)   
 [Page Nouveau rapport lié &#40;Gestionnaire de rapports&#41;](../Topic/New%20Linked%20Report%20Page%20\(Report%20Manager\).md)   
 [Page Choisir l’emplacement de l’élément &#40;Gestionnaire de rapports&#41;](../Topic/Choose%20Item%20Location%20Page%20\(Report%20Manager\).md)   
 [Page Propriétés générales, Rapports &#40;Gestionnaire de rapports&#41;](../Topic/General%20Properties%20Page,%20Reports%20\(Report%20Manager\).md)   
 [Concepts de Reporting Services &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  