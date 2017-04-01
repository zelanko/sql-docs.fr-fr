---
title: "Portail web (SSRS en mode natif) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/24/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 7349e626-6ed5-4d21-b05f-cf042ad9ad70
caps.latest.revision: 15
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 13
---
# Portail web (SSRS en mode natif)
Le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] Reporting Services est une expérience web qui vous permet d'afficher des rapports, rapports mobiles et indicateurs de performance clés et de naviguer parmi les éléments qui se trouvent dans votre instance de serveur de rapports. Vous pouvez également utiliser le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] pour administrer une instance unique de serveur de rapports.  
  
![Portail SSRS](../reporting-services/media/ssrsportal.png)  
  
Dans cette rubrique :  
  
-   [Qu'est-ce que le portail web ?](#whatisportal)  
  
-   [Prise en main du portail web](#startanduse)  
  
-   [Regroupement par catégories](#categories)  
  
-   [Recherche d’éléments](#search)  
  
-   [Tâches du portail web](#tasks)  
  
<a name="whatisportal"/>  
## Qu’est-ce que le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] ?  
  
Vous pouvez utiliser le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] pour effectuer les tâches suivantes :  
  
-   afficher, rechercher, imprimer et s'abonner à des rapports,  
  
-   créer, sécuriser et gérer l'arborescence des dossiers pour organiser les éléments sur le serveur,  
  
-   configurer la sécurité basée sur les rôles qui définit l'accès aux éléments et aux opérations,  
  
-   configurer l'historique, les paramètres et les propriétés d'exécution des rapports,  
  
-   créer des planifications partagées et des sources de données partagées pour faciliter la gestion des planifications et des connexions aux sources de données,  
  
-   créer des abonnements pilotés par les données qui déploient les rapports à un nombre important de destinataires,  
  
-   créer des rapports liés pour réutiliser de différentes manières ou adapter à d'autres fins un rapport existant,  
  
-   télécharger les outils courants, notamment le Générateur de rapports et l'Éditeur de rapports mobiles,  
  
-   [créer des indicateurs de performance clés](../reporting-services/working-with-kpis-in-reporting-services.md),  
  
-   envoyer des commentaires ou effectuer des demandes de fonctionnalités.  
  
Vous pouvez utiliser le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] pour parcourir l'arborescence des dossiers du serveur de rapports ou rechercher des rapports spécifiques. Vous pouvez afficher des rapports, consulter leurs propriétés générales et leurs anciennes copies capturées dans l'historique de rapport. Selon vos autorisations, vous pouvez aussi vous abonner à ces rapports pour les recevoir dans votre boîte de réception de messagerie électronique ou dans un dossier partagé sur votre système de fichiers.  
  
> [!NOTE] Pour plus d'informations sur les versions et les navigateurs pris en charge, consultez [Planification de la prise en charge des navigateurs par Reporting Services](../reporting-services/browser-support-for-reporting-services-and-power-view.md).  
  
Le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] est uniquement utilisé pour les serveurs de rapports qui s'exécutent en mode natif. Il n'est pas pris en charge sur un serveur de rapports que vous configurez en mode intégré SharePoint.  
  
Certaines fonctionnalités [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] sont disponibles uniquement dans les éditions spécifiées de [!INCLUDE[ssNoVersion](../includes/ssnoversion.md)]. Pour plus d'informations, consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.xml).  
  
Dans le cas d'une nouvelle installation, seuls les administrateurs locaux possèdent les autorisations suffisantes pour travailler avec le contenu et les paramètres. Pour octroyer des autorisations à d'autres utilisateurs, un administrateur local doit créer des attributions de rôles permettant d'accéder au serveur de rapports. Les pages et les tâches auxquelles un utilisateur pourra ensuite accéder dépendent des attributions de rôles qui ont été définies pour cet utilisateur. Pour plus d'informations, consultez Ajout d’un utilisateur au serveur de rapports.  
  
> [!NOTE] Si vous accédez au portail web sur l'ordinateur local sur lequel le serveur est en cours d’exécution, il est possible qu’un message indiquant que vous n'êtes pas autorisé à afficher ce dossier s’affiche. Cela est dû au contrôle d'accès universel (UAC) et au fait que vous n'exécutez pas le navigateur en tant qu'administrateur. Vous n'êtes pas en mesure d'exécuter la session en tant qu'administrateur. Vous devez utiliser Internet Explorer. Vous pouvez soit accéder au serveur à distance, soit lancer Internet Explorer en tant qu'administrateur et accéder au portail web. Si vous souhaitez utiliser le portail web à distance, vous devez accorder les droits de gestionnaire du contenu de votre compte sur le dossier.  
  
<a name="startanduse"/>  
## Prise en main du [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]  
  
Le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] est une application web que vous ouvrez en tapant l'URL du [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] dans la barre d'adresses de la fenêtre du navigateur. Lorsque vous démarrez le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], les pages, liens et options que vous voyez varient en fonction des autorisations dont vous disposez sur le serveur de rapports. Pour effectuer une tâche, vous devez être titulaire d'un rôle qui inclut la tâche.  Un utilisateur doté d'un rôle disposant d'autorisations complètes peut accéder à l'ensemble des menus et des pages de l'application qui sont disponibles pour gérer un serveur de rapports. Un utilisateur doté d'un rôle limité aux autorisations d'affichage et d'exécution des rapports ne peut voir que les menus et les pages concernées par ces activités. Chaque utilisateur peut disposer de rôles divers pour les différents serveurs de rapports qu'il utilise, voire pour les divers rapports et dossiers stockés sur un serveur de rapports unique.  
  
Pour plus d'informations, consultez [Attribution d'autorisations sur un serveur de rapports en mode natif](../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md).  
  
### Lancement du [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]  
Pour lancer le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] à partir d'un navigateur, procédez comme suit :  
  
1.  Ouvrez votre navigateur web. Pour obtenir la liste des navigateurs web pris en charge, consultez la page [Planification de la prise en charge des navigateurs pour Reporting Services](../reporting-services/browser-support-for-reporting-services-and-power-view.md).  
  
2.  Dans la barre d'adresses du navigateur web, tapez l'URL du [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)].  
  
    Par défaut, l’URL est *http://[ComputerName]/reports*.  
  
    Le serveur de rapports peut être configuré pour utiliser un port spécifique. Par exemple, *http://[ComputerName]:80/reports* ou *http://[ComputerName]:8080/reports*  
  
<a name="categories">  
## Regroupement par catégories  
  
Le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] regroupe les éléments en différentes catégories. Les catégories disponibles sont les suivantes.  
  
-   Indicateurs de performance clés  
-   Rapports mobiles  
-   Rapports paginés  
-   Rapports Power BI Desktop  
-   Classeurs Excel  
-   Datasets  
-   Sources de données  
-   Ressources  
  
Vous pouvez contrôler ce qui est affiché en sélectionnant **Affichage** dans le coin supérieur droit. Les éléments cochés s’afficheront si des éléments sont disponibles dans ce dossier. Pour masquer des éléments, vous pouvez les décocher.  
  
![ssRSWebPortal-view](../reporting-services/media/ssrswebportal-view.png)  
   
Si vous sélectionnez Afficher les éléments masqués, ces éléments s’afficheront dans une couleur plus claire.  
  
![ssRSWebPortal-hidden](../reporting-services/media/ssrswebportal-hidden.png)  
   
### Rapports Power BI Desktop et classeurs Excel  
  
Vous pouvez télécharger, organiser et gérer les autorisations pour les rapports Power BI Desktop et les classeurs Excel. Ils sont regroupés au sein du portail web.  
  
![ssRSWebPortal-view-pbi-and-excel](../reporting-services/media/ssrswebportal-view-pbi-and-excel.png)  
   
Les fichiers sont stockés dans Reporting Services, de la même façon que les autres fichiers de ressources. Sélectionner un de ces éléments permet de le télécharger localement sur votre bureau. Vous pouvez enregistrer les modifications apportées en les téléchargeant à nouveau sur le serveur de rapports.  
  
<a name="search">  
## Recherche d’éléments  
  
Vous pouvez entrer une équipe de recherche pour voir tout ce à quoi vous pouvez accéder. Les résultats sont classés ainsi : indicateurs de performance clés, rapports, jeux de données et autres éléments. Vous pouvez ensuite interagir avec les résultats et les ajouter à vos favoris.  
  
![ssRSWebPortal-Search](../reporting-services/media/ssrswebportal-search.png)  
  
<a name="tasks">  
## Tâches du portail web  
  
[Personnalisation du portail web](../reporting-services/branding-the-web-portal.md)  

[Utilisation d’indicateurs de performance clés](../reporting-services/working-with-kpis-in-reporting-services.md)
  
[Utilisation de jeux de données partagés](../reporting-services/working-with-shared-datasets-web-portal.md)  
  
## Voir aussi

[Créer des rapports mobiles avec l’Éditeur de rapports mobiles SQL Server](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)
  
[Configurer une URL (Gestionnaire de configuration de SSRS)](../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)  
  
[Outils de Reporting Services](../reporting-services/tools/reporting-services-tools.md)  
  
[Planification de la prise en charge du navigateur dans Reporting Services](../reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
[Fonctionnalités prises en charge par les éditions de SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.xml)  
  
  
