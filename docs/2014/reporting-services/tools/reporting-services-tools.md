---
title: Outils de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SSRS, tools
- Reporting Services, tools
- components [Reporting Services]
- components [Reporting Services], about components
- Reporting Services, components
- SSRS, components
- reports [Reporting Services], tools
- SQL Server Reporting Services, components
- SQL Server Reporting Services, tools
- architecture [Reporting Services]
ms.assetid: 23d616e3-eb90-43fb-9b7a-869bd7e22e7b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 21c56f28a6f65b22d8fe334a1046f44f868c4453
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66099910"
---
# <a name="reporting-services-tools"></a>Outils de Reporting Services
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] contient un ensemble d'outils de graphisme et de script qui prennent en charge le développement et l'utilisation de rapports complets dans un environnement géré. Le jeu d'outils comprend des outils de développement, des outils de configuration et d'administration, et des outils d'affichage des rapports. Cette rubrique donne une vue d'ensemble de chaque outil, ainsi que son mode d'accès, dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Pour rechercher un outil immédiatement, consultez [didacticiel : Comment localiser et démarrer Reporting Services outils &#40;SSRS&#41;](tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md).  
  
## <a name="tools-for-report-authoring"></a>Outils de création de rapports  
 La table suivante répertorie les outils disponibles pour la création de rapports dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
|Tool|Description|Procédure accès|  
|----------|-----------------|-------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]|Une exploration interactive des données et une expérience de présentation visuelle conçue pour vous permettre de créer et interagir avec les rapports basés sur des modèles tabulaires de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .<br /><br /> Remarque : Requiert [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.|Navigateur avec Silverlight.|  
|Concepteur de rapports|Utilisez cet outil pour concevoir des rapports et déployer sur un serveur de rapports en mode natif ou en mode SharePoint.<br /><br /> Hébergé dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<br /><br /> Volet des données de rapport pour organiser les données utilisées dans votre rapport<br /><br /> Vues à onglets pour la conception et aperçu pour la création de rapports interactifs<br /><br /> Des concepteurs de requêtes pour spécifier les données à récupérer à partir de sources de données, et qui sont associés à la source de données dans [RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md)<br /><br /> Un éditeur d'expression avec Intellisense pour générer les expressions de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] qui personnalisent le contenu et l'apparence d'un rapport<br /><br /> Prend en charge les éléments de rapport personnalisés et les concepteurs de requêtes personnalisés<br /><br /> <br /><br /> Pour plus d’informations, consultez [Reporting Services dans les outils de données SQL Server &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).|[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|  
|Générateur de rapports|Utilisez cet outil pour concevoir des rapports et déployer sur un serveur de rapports en mode natif ou en mode SharePoint.<br /><br /> Environnement de création semblable à Office de [!INCLUDE[msCoName](../../includes/msconame-md.md)]<br /><br /> Capacité à enregistrer des éléments de rapport en tant que parties de rapports<br /><br /> Un assistant pour la création de cartes<br /><br /> Agrégat d'agrégats<br /><br /> Prise en charge améliorée des expressions<br /><br /> Des concepteurs de requêtes pour spécifier quelles données extraire d'une sélection de types de sources de données intégrées<br /><br /> <br /><br /> Pour plus d’informations, consultez [le Générateur de rapports &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md).|Téléchargez MSI ou ouvrez le gestionnaire de rapports/de SharePoint|  
  
## <a name="tools-for-report-server-administration"></a>Outils pour l'administration de Report Server  
 Un ensemble d'outils graphiques et de scripts sont disponibles pour administrer le serveur de rapports dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Les outils à utiliser dépendent du mode de déploiement de votre serveur de rapports.  
  
### <a name="native-mode"></a>Mode natif  
 La table suivante répertorie les outils disponibles pour administrer le serveur de rapports qui est déployé en mode natif.  
  
|Tool|Description|Procédure accès|  
|----------|-----------------|-------------------|  
|Gestionnaire de configuration de Reporting Services|Utilisez cet outil pour configurer une installation de services de rapports. Notez que le Gestionnaire de Configuration de Reporting Services ne pas vous aider à gérer le contenu du serveur de rapports, activer des fonctionnalités supplémentaires ou accorder l’accès au serveur. Les tâches disponibles sont les suivantes :<br /><br /> configuration des instances de serveur de rapports locales et distantes<br /><br /> configuration du compte de service Report Server<br /><br /> création et configuration d'une ou plusieurs URL de service Web.<br /><br /> configuration de l'URL du Gestionnaire de rapports<br /><br /> création et configuration de la base de données du serveur de rapports.<br /><br /> configuration d'un déploiement avec montée en puissance parallèle.<br /><br /> sauvegarde, restauration ou remplacement de la clé symétrique utilisée pour chiffrer des chaînes de connexion stockées et des informations d'identification.<br /><br /> configuration du compte d'exécution sans assistance.<br /><br /> configuration d'un serveur SMTP pour la remise du courrier électronique.<br /><br /> <br /><br /> Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).|Menu Démarrer|  
|SQL Server Management Studio|Utilisez cet outil pour gérer une ou plusieurs instances de serveurs de rapports dans un environnement unique, y compris :<br /><br /> la gestion des instances de serveur de rapports locales et distantes<br /><br /> la définition des propriétés du serveur de rapports<br /><br /> la modification des définitions de rôles<br /><br /> la désactivation des fonctionnalités du serveur que vous n'utilisez pas<br /><br /> la gestion des travaux<br /><br /> la gestion des planifications partagées|Menu Démarrer|  
|Gestionnaire de configuration SQL Server|Utilisez cet outil pour :<br /><br /> installer et démarrer les services Windows de services de rapport<br /><br /> configurer la création de rapports pour les commentaires client, l'emplacement du répertoire de vidage et le rapport d'erreurs<br /><br /> <br /><br /> **\*\* Avertissement \* \***  n’utilisez pas cet outil pour configurer le compte de service. Utilisez plutôt l'outil Configuration de Reporting Services.<br /><br /> Pour plus d'informations, consultez [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md).|Menu Démarrer|  
|Utilitaire rsconfig|Utilisez cet outil pour configurer et gérer la connexion du serveur de rapports à la base de données du serveur de rapports. mais aussi à définir un compte d'utilisateur pour le traitement des rapports autonomes.<br /><br /> Pour plus d’informations, consultez [Utilitaires d’invite de commandes du serveur de rapports &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).|Ligne de commande|  
|Utilitaire Rskeymgmt|Utilisez cet outil pour :<br /><br /> extraire, restaurer, créer et supprimer la clé symétrique utilisée pour chiffrer les données de serveur de rapports<br /><br /> joindre des instances de serveurs de rapports dans un déploiement avec montée en puissance parallèle<br /><br /> <br /><br /> Pour plus d’informations, consultez [Utilitaires d’invite de commandes du serveur de rapports &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).|Ligne de commande|  
|Classes WMI (Windows Management Instrumentation)|Utilisez ces classes pour automatiser les tâches de configuration dans le gestionnaire de configuration des services de rapports sans qu'il soit nécessaire d'utiliser l'interface utilisateur graphique.<br /><br /> Pour plus d'informations, consultez [Accessing the WMI Provider Programmatically](../accessing-the-wmi-provider-programmatically.md).|Script Visual Basic|  
  
### <a name="sharepoint-integrated-mode"></a>Mode intégré SharePoint  
 En mode SharePoint, les services de rapports constituent une application de service dans l'architecture SharePoint, et sont administrés directement par SharePoint  
  
|Tool|Description|Procédure accès|  
|----------|-----------------|-------------------|  
|Démarrez l'Administration centrale de SharePoint.|Utilisez l'administration centrale de SharePoint pour créer, interroger et gérer les demandes de service partagé de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> Pour plus d’informations, consultez [Configuration et administration d’un serveur de rapports &#40;mode SharePoint de Reporting Services&#41;](../configure-administer-report-server-reporting-services-sharepoint-mode.md).|Navigateur vers l'URL de site SharePoint pour l'administration centrale|  
|Applets de commande Powershell|Utilisez les applets de commande PowerShell pour créer, interroger et gérer les demandes de service partagé de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> Pour plus d’informations, consultez [Applets de commande PowerShell pour le mode SharePoint de Reporting Services](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md).|SharePoint 2010 Management Shell.|  
  
## <a name="tools-for-report-content-management"></a>Outils pour la gestion de contenu du rapport  
 Un ensemble d'outils graphiques et de script sont disponibles pour gérer le contenu dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Les outils à utiliser dépendent du mode de déploiement de votre serveur de rapports.  
  
|Tool|Description|Procédure accès|  
|----------|-----------------|-------------------|  
|URL de service Web de Report Server|Utilisez cet outil pour parcourir le contenu du catalogue de rapport dans une page de navigation d'élément générique.<br /><br /> Pour plus d'informations, consultez [Report Server Web Service](../report-server-web-service/report-server-web-service.md).|Browser|  
|Gestionnaire de rapports|**(Mode natif uniquement)** Utilisez cet outil pour administrer l’instance de serveur de rapports unique d’un emplacement distant par le biais d’une connexion HTTP. Vous pouvez effectuer les opérations suivantes :<br /><br /> Afficher, rechercher, imprimer et s'abonner à des rapports,<br /><br /> Créer, sécuriser et gérer l'arborescence des dossiers pour organiser les éléments sur le serveur.<br /><br /> configurer la sécurité basée sur les rôles qui définit l'accès aux éléments et aux opérations,<br /><br /> configurer l'historique, les paramètres et les propriétés d'exécution des rapports,<br /><br /> créer des modèles de rapport qui se connectent et récupérer les données d'une source de données Microsoft SQL Server Analysis Services ou d'une source de données relationnelle SQL Server,<br /><br /> définir la sécurité de l'élément de modèle de façon à autoriser l'accès à des entités spécifiques dans le modèle ou mapper des entités à des rapports générés interactifs prédéfinis que vous créez par avance,<br /><br /> créer des planifications partagées et des sources de données partagées pour faciliter la gestion des planifications et des connexions aux sources de données,<br /><br /> créer des abonnements pilotés par les données qui assurent la présentation des rapports à un nombre important de destinataires,<br /><br /> créer des rapports liés pour réutiliser de différentes manières ou adapter à d'autres fins un rapport existant,<br /><br /> Lancer le Générateur de rapports pour créer des rapports que vous pouvez enregistrer et exécuter sur le serveur de rapports.<br /><br /> <br /><br /> Pour plus d’informations, consultez [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).||  
|Utilitaire RS|Cet outil est un hôte de script que vous pouvez utiliser pour réaliser des opérations contenant des scripts. Par son intermédiaire, vous exécutez des scripts [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] pour publier des rapports, créer des éléments dans une base de données de serveur de rapports, copier des données entre des bases de données de serveurs de rapports, etc.<br /><br /> Pour plus d’informations, consultez [Utilitaires d’invite de commandes du serveur de rapports &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).|Ligne de commande|  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur de rapports Reporting Services](../reporting-services-report-server.md)   
 [Concepts de Reporting Services &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md)   
 [Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
