---
title: "&#201;l&#233;ments requis pour les didacticiels (G&#233;n&#233;rateur de rapports) | Microsoft Docs"
ms.custom: ""
ms.date: "06/15/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 11
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# &#201;l&#233;ments requis pour les didacticiels (G&#233;n&#233;rateur de rapports)
L’utilisation des didacticiels du Générateur de rapports suppose que vous pouvez afficher et enregistrer des rapports paginés [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] sur un serveur de rapports ou un site SharePoint intégré à un serveur de rapports. Pour les données, tous les didacticiels utilisent des requêtes littérales qui doivent être traitées par une instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
Si vous n'avez pas accès à un serveur de rapports, un site de serveur de rapports ou une source de données, vous pouvez en apprendre plus sur le Générateur de rapports en générant un rapport hors connexion. Consultez [Didacticiel : créer un rapport de graphique rapide en mode hors connexion &#40;Générateur de rapports&#41;](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
## Spécifications  
Pour exécuter les didacticiels du Générateur de rapports, vous devez réunir les conditions suivantes :  
  
-   Accédez au Générateur de rapports [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Vous pouvez exécuter le Générateur de rapports depuis un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] ou un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] en mode intégré SharePoint. Seule la première étape, l’ouverture du Générateur de rapports, varie selon les différents serveurs.  
  
    Sur un serveur de rapports, sélectionnez **Nouveau** > **Rapport paginé**.
  
    Sur un serveur de rapports en mode intégré SharePoint, sous l’onglet **Documents**, sélectionnez **Nouveau Document** et, dans la liste déroulante, sélectionnez **Rapport du Générateur de rapports**. Par exemple, `http://<servername>/sites/mySite/reports`. L'administrateur SharePoint doit activer la fonctionnalité Rapport du Générateur de rapports pour chaque bibliothèque de documents.  
  
-   URL pointant vers un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)]ou un site SharePoint intégré à un serveur de rapports [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)]. Vous devez être autorisé à enregistrer et consulter des rapports, des sources de données partagées, des datasets partagés, des parties de rapports et des modèles. Par défaut, l’URL d’un serveur de rapports est `http://<servername>/reportserver`. Par défaut, l’URL d’un site SharePoint est `http://<sitename>` ou `http://<server>/site`.  
  
-   Nom d’une instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et des informations d’identification suffisantes pour l’accès en lecture seule à n’importe quelle base de données. Les requêtes de dataset des didacticiels utilisent des données littérales, mais chaque requête doit être traitée par une instance de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] pour retourner les métadonnées nécessaires à un dataset de rapport. Par exemple, la chaîne de connexion suivante spécifie uniquement un serveur : `data source=<servername>`. Vous devez avoir un accès en lecture à la base de données par défaut qui vous est affectée par l'administrateur système qui vous accorde l'autorisation d'accès au serveur. Vous pouvez également spécifier une base de données, comme indiqué dans la chaîne de connexion suivante : `data source=<servername>;initial catalog=<database>`.  
  
-   Pour le didacticiel [Rapport cartographique](Tutorial:%20Map%20Report%20\(Report%20Builder\).md), le serveur de rapports doit être configuré pour prendre en charge les cartes Bing comme arrière-plan. Pour plus d’informations, consultez [Planifier la prise en charge de rapport cartographique](http://msdn.microsoft.com/fr-fr/5ddc97a7-7ee5-475d-bc49-3b814dce7e19).   

-   Le didacticiel [Création d’un rapport principal et d’un rapport d’extraction](Tutorial:%20Creating%20Drillthrough%20and%20Main%20Reports%20\(Report%20Builder\).md) nécessite l’accès au cube Contoso Sales. Pour plus d’informations, consultez le didacticiel. 
  
L’administrateur du serveur de rapports doit vous accorder les autorisations nécessaires sur le serveur de rapports, configurer les emplacements des dossiers [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] et configurer les options par défaut du Générateur de rapports. Pour plus d’informations, consultez [Installer et désinstaller le Générateur de rapports](../Topic/Install%20and%20Uninstall%20Report%20Builder.md).  
  
## Voir aussi  
[Didacticiels du Générateur de rapports](../reporting-services/report-builder-tutorials.md)  
  
