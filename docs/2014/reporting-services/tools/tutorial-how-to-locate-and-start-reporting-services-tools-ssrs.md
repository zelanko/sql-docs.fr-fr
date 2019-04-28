---
title: 'Tutoriel : Comment localiser et démarrer les outils Reporting Services (SSRS) | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder 1.0, locating and starting tool
- Reporting Services, tutorials
- Reporting Services, tools
- Reporting Services Configuration tool
- Business Intelligence Development Studio, locating and starting tool
- Model Designer [Reporting Services], locating and starting tool
- Report Designer [Reporting Services], tutorials
- tools [Reporting Services]
- tutorials [Reporting Services]
- Report Manager [Reporting Services]
ms.assetid: 51ad69d8-fe92-4662-a7cd-d235692f0c03
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03fb1d70046fe784fecafd8d9b3092ce21962498
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62657996"
---
# <a name="tutorial-how-to-locate-and-start-reporting-services-tools-ssrs"></a>Tutoriel : Comment localiser et démarrer les outils Reporting Services (SSRS)
  Ce didacticiel présente les outils permettant de configurer un serveur de rapports, de gérer le contenu et les opérations d'un serveur de rapports, et de créer et publier des rapports. Ce didacticiel a pour but d'aider les nouveaux utilisateurs à savoir rechercher et ouvrir chaque outil. Si vous connaissez déjà les différents outils, vous pouvez enchaîner sur les autres didacticiels qui peuvent vous aider à acquérir d'importantes compétences dans l'utilisation de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Pour plus d’informations sur les autres didacticiels, consultez [didacticiels sur Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).  
  
 Dans cette rubrique :  
  
-   [Gestionnaire de configuration de Reporting Services (mode natif)](#bkmk_configuration_manager)  
  
-   [Gestionnaire de rapports (Mode natif)](#bkmk_report_manager)  
  
-   [Management Studio](#bkmk_managements_studio)  
  
-   [SQL Server Data Tools avec le Concepteur de rapports et l’Assistant rapport](#bkmk_ssdt)  
  
-   [Générateur de rapports](#bkmk_report_builder)  
  
##  <a name="bkmk_configuration_manager"></a> Gestionnaire de configurations de Reporting Services (mode natif)  
 Utilisez le Gestionnaire de configuration en mode natif pour terminer les opérations suivantes : , , , , et.  
  
-   Spécifiez le compte de service.  
  
-   Créez ou mettez à niveau la base de données de serveur de rapports.  
  
-   Modifiez les propriétés de connexion.  
  
-   Spécifiez des URL.  
  
-   Gérez les clés de chiffrement.  
  
-   Configurez le traitement des rapports sans assistance et la remise de rapports par courrier électronique.  
  
 **Installation :** Le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] est installé en même temps que le mode natif de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Pour plus d’informations, consultez [Installer le serveur de rapports Reporting Services en mode natif](../install-windows/install-reporting-services-native-mode-report-server.md).  
  
#### <a name="to-start-the-reporting-services-configuration-manager"></a>Pour démarrer le Gestionnaire de configuration de Reporting Services  
  
1.  Sur l’écran d’accueil Windows, tapez `reporting` et dans le **applications** résultats de la recherche, cliquez sur **Gestionnaire de Configuration de Reporting Services**.  
  
     ![Gestionnaire de configuration de Reporting Services au cours du démarrage](../media/bi-ssrs-configmanager-win8-startscreen.gif "Gestionnaire de configuration de Reporting Services au cours du démarrage")  
  
     **Or**  
  
     Cliquez sur **Démarrer**, puis sur **Programmes**, sur [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis sur **Gestionnaire de configuration de Reporting Services**.  
  
     La boîte de dialogue **Sélection de l'instance d'installation de Report Server** s'affiche pour que vous spécifiiez l'instance de serveur de rapports à configurer.  
  
2.  Dans **Nom du serveur**, spécifiez le nom de l'ordinateur sur lequel est installée l'instance de serveur de rapports. Le nom de l'ordinateur local est spécifié par défaut, mais vous pouvez également taper le nom d'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distante.  
  
     Si vous spécifiez un ordinateur distant, cliquez sur **Rechercher** pour établir une connexion. Le serveur de rapports doit être configuré à l'avance pour l'administration à distance. Pour plus d’informations, consultez [Configurer un serveur de rapports pour l’administration à distance](../report-server/configure-a-report-server-for-remote-administration.md).  
  
3.  Dans **Dansstance Name**, choisissez l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] que vous souhaitez configurer. Seules les instances de serveur de rapports [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] figurent dans la liste. Vous ne pouvez pas configurer d'instances de versions antérieures de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
4.  Cliquer sur **Se connecter**.  
  
5.  Pour vérifier si l'outil a été lancé, comparez vos résultats à l'image suivante :  
  
     ![Outil de configuration de Reporting Services](../media/rs-ui-reportserverconfigkatmai.gif "Outil de configuration de Reporting Services")  
  
 **Étapes suivantes :** [Configurer et administrer un serveur de rapports &#40;SSRS en mode natif&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) et [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
##  <a name="bkmk_report_manager"></a> Gestionnaire de rapports (Mode natif)  
 Utilisez [le Gestionnaire de rapports &#40;SSRS en Mode natif&#41; ](../report-manager-ssrs-native-mode.md) pour définir des autorisations, gérer les abonnements et planifications et travailler avec les rapports. Pour afficher les rapports, vous pouvez aussi utiliser le Gestionnaire de rapports.  
  
 **Installation :** Le Gestionnaire de rapports est installé lorsque vous installez [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en mode natif : [Installer le serveur de rapports Reporting Services en mode natif](../install-windows/install-reporting-services-native-mode-report-server.md)  
  
 Avant de pouvoir ouvrir le Gestionnaire de rapports, vous devez avoir les autorisations suffisantes (initialement, seuls les membres du groupe local Administrateurs ont les autorisations nécessaires pour accéder aux fonctionnalités du Gestionnaire de rapports). Le Gestionnaire de rapports propose des pages et options différentes en fonctions des attributions de rôle de l'utilisateur en cours. Les utilisateurs qui ne bénéficient pas d'autorisations obtiennent une page vide. Les utilisateurs avec l'autorisation d'afficher les rapports obtiennent des liens sur lesquels ils peuvent cliquer pour ouvrir les rapports. Pour en savoir plus sur les autorisations, consultez [Rôles et autorisations &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).  
  
#### <a name="to-start-report-manager"></a>Pour démarrer le Gestionnaire de rapports  
  
1.  Ouvrez votre navigateur. Pour plus d’informations sur les versions et les navigateurs pris en charge, consultez [planification pour Reporting Services et la prise en charge du navigateur Power View &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).  
  
2.  Dans la barre d'adresses du navigateur Web, tapez l'URL du Gestionnaire de rapports. Par défaut, l’URL est **http://\<serverName > / reports**. Vous pouvez utiliser l'outil de configuration de Reporting Services pour confirmer le nom du serveur et l'URL. Pour plus d’informations sur les URL utilisées dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], consultez [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md).  
  
3.  Le Gestionnaire de rapports s'ouvre dans la fenêtre du navigateur. La page de démarrage est constituée du dossier Home. En fonction des autorisations, vous verrez au sein de la page de démarrage des dossiers supplémentaires, des liens vers les rapports et des fichiers de ressources. Il se peut aussi que la barre d'outils contienne des commandes et des boutons supplémentaires.  
  
4.  Si vous exécutez le Gestionnaire de rapports sur le serveur de rapports local, consultez [configurer un serveur de rapports en Mode natif pour l’Administration locale &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
 **Étapes suivantes :** [Configurer le Gestionnaire de rapports &#40;en Mode natif&#41;](../report-server/configure-web-portal.md).  
  
##  <a name="bkmk_managements_studio"></a> Management Studio  
 Les administrateurs du serveur de rapports peuvent utiliser [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour gérer le serveur de rapports en même temps que d'autres composants serveur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md).  
  
#### <a name="to-start-sql-server-management-studio"></a>Pour démarrer SQL Server Management Studio  
  
1.  À partir du type de l’écran d’accueil Windows `sql server` et dans le **applications** résultats de la recherche, cliquez sur **SQL Server Management Studio**.  
  
     ![Management Studio sur l’écran de démarrage de Windows](../media/bi-ssms-win8-startscreen.gif "Management Studio sur l’écran de démarrage de Windows")  
  
     **Or**  
  
     Cliquez sur **Démarrer**, puis sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]et sur **SQL Server Management Studio**. La boîte de dialogue **Se connecter au serveur** s'ouvre.  
  
2.  Si la boîte de dialogue **Se connecter au serveur** n'apparaît pas, dans la liste **Explorateur d'objets**, cliquez sur **Se connecter** , puis sélectionnez **Reporting Services**.  
  
3.  Dans la liste **Type de serveur** , sélectionnez **Reporting Services**. Si [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ne figure pas dans la liste, c'est qu'il n'est pas installé.  
  
4.  Dans la liste **Nom du serveur** , sélectionnez une instance de serveur de rapports. Les instances locales figurent dans la liste. Vous pouvez aussi taper le nom d'une instance distante de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
5.  Cliquer sur **Se connecter**. Vous pouvez développer le nœud racine pour définir les propriétés du serveur, modifier les définitions de rôle ou désactiver des fonctionnalités du serveur de rapports.  
  
##  <a name="bkmk_ssdt"></a> SQL Server Data Tools avec le Concepteur de rapports et l'Assistant Rapport  
 Le Concepteur de rapports est disponible dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] - Business Intelligence pour Visual Studio 2012. La surface de dessin des outils inclut des fenêtres avec onglets, des Assistants et des menus pour accéder aux fonctions de création des modèles et des rapports. L'outil de concepteur de rapports devient disponible lorsque vous choisissez un projet Report Server ou un modèle de l'Assistant Report Server. Pour en savoir plus, consultez [Reporting Services dans les outils de données SQL Server &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).  
  
#### <a name="to-start-report-designer"></a>Pour démarrer le Concepteur de rapports  
  
1.  Dans l'écran de démarrage de Windows, tapez **data** , puis dans les résultats de la recherche **Applications** , cliquez sur **SQL Server Data Tools pour Visual Studio 2012**.  
  
     **Or**  
  
     Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, pointez sur [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], puis cliquez sur **Outils de données SQL Server (SSDT)**.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans la liste **Types de projets** , cliquez sur **Projets Business Intelligence**.  
  
4.  Dans la liste **Modèles** , cliquez sur **Projet Report Server**. Le schéma suivant montre comment les modèles de projet s'affichent dans la boîte de dialogue :  
  
     ![Boîte de dialogue Nouveau modèle de projet](../media/rs-ui-newrsproject.gif "Boîte de dialogue Nouveau modèle de projet")  
  
5.  Tapez un nom et un emplacement pour le projet. Vous pouvez également cliquer sur **Parcourir** , puis sélectionner un emplacement.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] s'ouvre avec la page de démarrage de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . L'Explorateur de solutions fournit des catégories pour la création de rapports et de sources de données. Vous pouvez utiliser ces catégories pour créer de nouveaux rapports et de nouvelles sources de données. Les fenêtres avec onglets s'affichent quand vous créez une définition de rapport. Les fenêtres avec onglets sont les suivantes : Données, Mise en page et Aperçu.  
  
 Pour commencer votre premier rapport, consultez [Créer un rapport de table de base &#40;didacticiel SSRS&#41;](../create-a-basic-table-report-ssrs-tutorial.md). Pour en savoir plus sur les concepteurs de requêtes que vous pouvez utiliser dans le Concepteur de rapports, consultez [outils de conception de requête dans le rapport concepteur SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md).  
  
##  <a name="bkmk_report_builder"></a> Générateur de rapports  
 Utilisez [le Générateur de rapports &#40;SSRS&#41; ](report-builder-authoring-environment-ssrs.md) pour créer des rapports dans un [!INCLUDE[msCoName](../../includes/msconame-md.md)] environnement de création semblable à Office. Vous pouvez personnaliser et mettre à jour tous les rapports existants, qu'ils aient été créés dans le Concepteur de rapports ou dans les versions précédentes du Générateur de rapports. Contactez votre administrateur afin de connaître l'emplacement du fichier ReportBuilder3.msi que vous exécutez pour installer le Générateur de rapports sur votre ordinateur local.  
  
 **Installation :** Cliquez sur-une fois que la version du Générateur de rapports est installée par [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] en mode natif ou en mode SharePoint. La version autonome du Générateur de rapports est disponible sous forme d'un téléchargement distinct.  Consultez [installer la Version autonome du Générateur de rapports &#40;Générateur de rapports&#41;](../install-windows/install-report-builder.md)  
  
#### <a name="to-start-report-builder-clickonce-from-report-manager-native-mode"></a>Pour démarrer la version ClickOnce du Générateur de rapports à partir du Gestionnaire de rapports (mode natif)  
  
1.  Dans le navigateur Web, tapez l'URL du Gestionnaire de rapports pour votre serveur de rapports. Par défaut, l’URL est http://\<*nom_serveur*>/reports. Le Gestionnaire de rapports s'ouvre.  
  
2.  Cliquez sur **Générateur de rapports**.  
  
     Le Générateur de rapports s'ouvre et vous pouvez alors créer un rapport ou ouvrir un rapport sur le serveur de rapports.  
  
#### <a name="to-start-report-builder-clickonce-using-a-url"></a>Pour démarrer la version ClickOnce du Générateur de rapports à l'aide d'une URL  
  
1.  Dans le navigateur Web, tapez l'URL suivante dans la barre d'adresses :  
  
     **http://\<servername>/reportserver/reportbuilder/ReportBuilder_3_0_0_0.application**  
  
2.  Appuyez sur Entrée.  
  
     Le Générateur de rapports s'ouvre et vous pouvez alors créer un rapport ou ouvrir un rapport sur le serveur de rapports.  
  
#### <a name="to-start-report-builder-clickonce-in-reporting-services-sharepoint-mode"></a>Pour démarrer la version ClickOnce du Générateur de rapports dans Reporting Services en mode SharePoint  
  
1.  Accédez jusqu'au site qui contient la bibliothèque dans laquelle vous souhaitez créer un rapport.  
  
2.  Ouvrez la bibliothèque.  
  
3.  Dans le menu **Nouveau** , cliquez sur **Rapport du Générateur de rapports**.  
  
     Le Générateur de rapports s'ouvre et vous pouvez alors créer un rapport ou ouvrir un rapport sur le serveur de rapports.  
  
#### <a name="to-start-report-builder-stand-alone"></a>Pour démarrer la version autonome du Générateur de rapports  
  
1.  Dans l'écran de démarrage de Windows, tapez **Générateur de rapports** , puis cliquez sur **Générateur de rapports 3.0**.  
  
     **Or**  
  
     Dans le menu Démarrer, cliquez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2014 Report Builder**.  
  
2.  Cliquez sur **Générateur de rapports**.  
  
     Le Générateur de rapports s'ouvre et vous pouvez créer ou ouvrir un rapport.  
  
3.  Cliquez sur **Aide de Report Builder** pour ouvrir la documentation du Générateur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer, désinstaller et prise en charge du Générateur de rapports](../install-uninstall-and-report-builder-support.md)   
 [Installation en Mode SharePoint de Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](../install-windows/install-reporting-services-sharepoint-mode.md)   
 [Serveur de rapports Reporting Services](../reporting-services-report-server.md)   
 [Interroger des outils de conception dans le rapport concepteur SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md)   
 [Didacticiels sur Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  
