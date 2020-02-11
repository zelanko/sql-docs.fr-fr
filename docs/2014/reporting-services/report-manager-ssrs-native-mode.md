---
title: Gestionnaire de rapports (SSRS en mode natif) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 04/26/2019
ms.openlocfilehash: 55581ae96660732ee01bf12fa37e1c5e8ac9634e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "64568385"
---
# <a name="report-manager--ssrs-native-mode"></a>Report Manager  (SSRS Native Mode)
  Le Gestionnaire de rapports est un outil permettant d'accéder aux rapports et de les gérer via une interface Web. Vous l'utilisez pour administrer à partir d'un emplacement distant une instance de serveur de rapports unique par le biais d'une connexion HTTP. Cet outil met également à votre disposition une visionneuse de rapports et des fonctionnalités de navigation. Dans cette rubrique :  
  
-   [Qu'est-ce que le Gestionnaire de rapports ?](#bkmk_whatis_report_manager)  
  
-   [Démarrer et utiliser le Gestionnaire de rapports](#bkmk_start_report_manager)  
  
-   [Descriptions des icônes](#bkmk_icon_descriptions)  
  
##  <a name="bkmk_whatis_report_manager"></a>Qu’est-ce que Gestionnaire de rapports ?  
 Vous pouvez utiliser le Gestionnaire de rapports pour exécuter les tâches suivantes :  
  
-   Afficher, rechercher, imprimer et s'abonner à des rapports,  
  
-   Créer, sécuriser et gérer l'arborescence des dossiers pour organiser les éléments sur le serveur.  
  
-   configurer la sécurité basée sur les rôles qui définit l'accès aux éléments et aux opérations,  
  
-   configurer l'historique, les paramètres et les propriétés d'exécution des rapports,  
  
-   Créer des modèles de rapport qui se connectent aux données [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] d’une source de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relationnelle et les récupèrent à partir d’une source de données relationnelle.  
  
-   Définir la sécurité de l'élément de modèle de façon à autoriser l'accès à des entités spécifiques dans le modèle ou mapper des entités à des rapports générés interactifs prédéfinis que vous créez par avance,  
  
-   créer des planifications partagées et des sources de données partagées pour faciliter la gestion des planifications et des connexions aux sources de données,  
  
-   créer des abonnements pilotés par les données qui assurent la présentation des rapports à un nombre important de destinataires,  
  
-   créer des rapports liés pour réutiliser de différentes manières ou adapter à d'autres fins un rapport existant,  
  
-   Lancer le Générateur de rapports pour créer des rapports que vous pouvez enregistrer et exécuter sur le serveur de rapports.  
  
 Utilisez le Gestionnaire de rapports pour parcourir l'arborescence des dossiers du serveur de rapports ou rechercher des rapports spécifiques. Vous pouvez afficher des rapports, consulter leurs propriétés générales et leurs anciennes copies capturées dans l'historique de rapport, Selon vos autorisations, vous pouvez aussi vous abonner à ces rapports pour les recevoir dans votre boîte de réception de messagerie électronique ou dans un dossier partagé sur votre système de fichiers.  
  
> [!NOTE]  
>  Pour plus d’informations sur les navigateurs et versions pris en charge, consultez [planification de la prise en charge des navigateurs Reporting Services et Power View &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md).  
  
 Le Gestionnaire de rapports est utilisé uniquement pour un serveur de rapports qui s'exécute en mode natif. Il n'est pas pris en charge sur un serveur de rapports que vous configurez en mode intégré SharePoint.  
  
 Certaines fonctionnalités du gestionnaire de rapports sont disponibles uniquement dans les éditions spécifiées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Dans le cas d'une nouvelle installation, seuls les administrateurs locaux possèdent les autorisations suffisantes pour travailler avec le contenu et les paramètres. Pour octroyer des autorisations à d'autres utilisateurs, un administrateur local doit créer des attributions de rôles permettant d'accéder au serveur de rapports. Les pages et les tâches auxquelles un utilisateur pourra ensuite accéder dépendent des attributions de rôles qui ont été définies pour cet utilisateur. Pour plus d’informations, consultez [Accorder à un utilisateur l’accès à un serveur de rapports &#40;Gestionnaire de rapports&#41;](security/grant-user-access-to-a-report-server.md)ne doit être attribué qu'à un nombre très limité d'utilisateurs.  
  
 Si vous utilisez [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)] ou Windows Server 2008, vous devez configurer le Gestionnaire de rapports pour l'administration locale. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
##  <a name="bkmk_start_report_manager"></a>Démarrer et utiliser Gestionnaire de rapports  
 Le Gestionnaire de rapports est une application Web que vous ouvrez en tapant l'URL du Gestionnaire de rapports dans la barre d'adresses d'une fenêtre de navigateur. Lorsque vous démarrez le Gestionnaire de rapports, les pages, liens et options que vous voyez varient en fonction des autorisations dont vous disposez pour le serveur de rapports. Pour effectuer une tâche, vous devez être titulaire d'un rôle qui inclut la tâche. Un utilisateur doté d'un rôle disposant d'autorisations complètes peut accéder à l'ensemble des menus et des pages de l'application qui sont disponibles pour gérer un serveur de rapports. Un utilisateur doté d'un rôle limité aux autorisations d'affichage et d'exécution des rapports ne peut voir que les menus et les pages concernées par ces activités. Chaque utilisateur peut disposer de rôles divers pour les différents serveurs de rapports qu'il utilise, voire pour les divers rapports et dossiers stockés sur un serveur de rapports unique.  
  
 Pour plus d'informations, consultez [Attribution d'autorisations sur un serveur de rapports en mode natif](security/granting-permissions-on-a-native-mode-report-server.md).  
  
> [!NOTE]  
>  Si vous utilisez Windows Vista ou Windows Server 2008, vous devez configurer le serveur de rapports pour l'administration locale avant de pouvoir utiliser le Gestionnaire de rapports pour gérer une instance de serveur de rapports locale. Pour obtenir des instructions sur la configuration du serveur, consultez [configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="start-report-manager"></a>démarrer le Gestionnaire de rapports  
  
#### <a name="to-start-report-manager-from-a-browser"></a>Pour démarrer le Gestionnaire de rapports à partir du navigateur  
  
1.  Ouvrez [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 7.0 ou version ultérieure.  
  
2.  Dans la barre d'adresses du navigateur Web, tapez l'URL du Gestionnaire de rapports.  
  
    -   Par défaut, l’URL est `http://[ComputerName]/reports`.  
  
    -   Le serveur de rapports peut être configuré pour utiliser un port spécifique. Par exemple, `http:// [ComputerName]:80/reports` ou `http:// [ComputerName]:8080/reports`.  
  
## <a name="configuring-report-manager"></a>Configuration du Gestionnaire de rapports  
 La configuration du Gestionnaire de rapports implique la définition d'une URL pour l'application. D'autres tâches de configuration sont nécessaires si votre déploiement inclut l'exécution du Gestionnaire de rapports sur un ordinateur séparé.  
  
 La personnalisation du Gestionnaire de rapports est très limitée. Par exemple, vous pouvez modifier le titre de l'application sur la page Paramètres du site. En tant que développeur Web, vous avez la possibilité de modifier les feuilles de style qui contiennent des informations exploitées par le Gestionnaire de rapports. Cet outil n'étant pas conçu spécifiquement pour la personnalisation, il est important de tester soigneusement chacune de vos modifications. Si vous estimez que le Gestionnaire de rapports ne répond pas à vos besoins, développez une visionneuse de rapports personnalisés ou configurez des composants WebPart de SharePoint pour rechercher et afficher des rapports dans un site SharePoint. Pour plus d’informations, consultez [Configurer le Gestionnaire de rapports &#40;mode natif&#41;](report-server/configure-web-portal.md).  
  
##  <a name="bkmk_icon_descriptions"></a>Descriptions des icônes  
 Le tableau suivant décrit les icônes utilisées dans le Gestionnaire de rapports. Pour plus d’informations sur les icônes qui apparaissent dans la barre d’outils rapport, consultez [visionneuse HTML et barre d’outils rapport](html-viewer-and-the-report-toolbar.md).  
  
|Icône|Description|Action|  
|----------|-----------------|------------|  
|![Icône de rapport](media/hlp-16doc.gif "Icône de rapport")|Rapport|Cliquez sur l'icône ou le nom du rapport pour ouvrir le rapport. Le rapport s'ouvre dans une fenêtre distincte.|  
|![Icône de modèle](media/model-icon.gif "Icône Modèle")|Modèle de rapport|Cliquez sur l'icône Modèle de rapport pour ouvrir les pages des propriétés du modèle.|  
|![Icône Rapport lié](media/hlp-16linked.gif "Icône Rapport lié")|Rapport lié|Cliquez sur l'icône ou sur le nom du rapport pour ouvrir le rapport lié. Le rapport s'ouvre dans une fenêtre distincte.|  
|![Icône Dossier](media/hlp-16folder.gif "Icône Dossier")|Dossier|Cliquez sur l'icône ou le nom du dossier pour ouvrir le dossier.|  
|![Icône Abonnement](media/hlp-16subscription.gif "Icône Abonnement")|Subscription|Cliquez sur l'icône ou sur la description d'un abonnement pour le modifier.|  
|![Icône Abonnement piloté par les données](media/hlp-16subscriptiondd.gif "Icône Abonnement piloté par les données")|Abonnement piloté par les données|Cliquez sur l'icône ou sur la description d'un abonnement piloté par les données pour le modifier.|  
|![icône de ressource générique](media/hlp-16file.gif "icône de ressource générique")|Ressource|Cliquez sur l'icône ou le nom de la ressource pour ouvrir la ressource. La ressource s'ouvre dans une fenêtre distincte.|  
|![Icône de source de données partagée](media/hlp-16datasource.png "Icône de source de données partagée")|Élément de source de données partagée|Cliquez sur l'icône d'une source de données partagée pour ouvrir la page des propriétés, la liste des rapports et la liste des abonnements de cette source de données.|  
|![Icône de page de propriétés](media/hlp-16prop.gif "Icône Page de propriétés")|Page des propriétés|Cliquez sur l'icône d'une propriété pour accéder aux pages supplémentaires afin de pouvoir définir des propriétés et des niveaux de sécurité.|  
  
## <a name="see-also"></a>Voir aussi

- [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](install-windows/configure-a-url-ssrs-configuration-manager.md)
- [Planification de la prise en charge des navigateurs Reporting Services et Power View &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)
- [Générateur de rapports &#40;SSRS&#41;](tools/report-builder-authoring-environment-ssrs.md)
- - [Outils de Reporting Services](tools/reporting-services-tools.md)
- [Gestion du contenu du serveur de rapports &#40;SSRS en mode natif&#41;](report-server/report-server-content-management-ssrs-native-mode.md)  
[Aide F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)