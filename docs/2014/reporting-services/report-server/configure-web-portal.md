---
title: Configurer le Gestionnaire de rapports (Mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], configuring
ms.assetid: e918986c-af15-48f6-8178-256aed829c6a
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 005c9fe0ff5ba3f998e80a93ea19d85c87331403
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028580"
---
# <a name="configure-report-manager-native-mode"></a>Configurer le serveur de rapports (mode natif)
  Le Gestionnaire de rapports est une application Web frontale utilisée pour consulter des rapports, gérer le contenu d'un serveur de rapports et accorder aux utilisateurs l'accès à un serveur de rapports en mode natif. Le Gestionnaire de rapports est installé avec le service Web Report Server dans la même instance du serveur de rapports et est configuré si vous sélectionnez l'option **Installer la configuration par défaut en mode Natif** dans le programme d'installation. Vous pouvez également configurer le Gestionnaire de rapports après son installation. Cette rubrique fournit des informations sur les scénarios de configuration suivants du Gestionnaire de rapports :  
  
-   [Configurer le Gestionnaire de rapports de sorte qu'il utilise l'URL par défaut](#ConfigureRMURL)  
  
     Le Gestionnaire de rapports est une application Web à laquelle les utilisateurs accèdent via un navigateur Web. Vous devez au minimum définir l'URL utilisée pour ouvrir l'application dans une fenêtre de navigateur. L'URL est formée d'un nom d'hôte, d'un port et d'un répertoire virtuel. Les valeurs par défaut de cette URL utilisent les valeurs de nom d'hôte et de port que vous avez définies pour l'URL du service Web Report Server, plus le nom du répertoire virtuel **rapports** . Si vous disposez d’une instance nommée, le répertoire virtuel est **reports_instance**, où **instance** est le nom de votre instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   **Gestionnaire de rapports exécuté à partir d'un ordinateur distant**. Selon la configuration de votre réseau, vous devrez peut-être activer le port 80 sur les ordinateurs pour autoriser les demandes au Gestionnaire de rapports.  
  
    > [!TIP]  
    >  Si vous essayez d'accéder au Gestionnaire de rapports sur un ordinateur distant et que vous obtenez des erreurs de connexion dans votre navigateur, les paramètres du pare-feu sont généralement en cause. Pour plus d’informations, consultez [Configurer un pare-feu pour accéder au serveur de rapports](configure-a-firewall-for-report-server-access.md).  
  
     Si nécessaire, activez le port 80 sur les deux ordinateurs afin d'autoriser les requêtes sur ce port. Pour plus d’informations, consultez [Configurer un pare-feu pour accéder au serveur de rapports](configure-a-firewall-for-report-server-access.md).  
  
-   [Configurer le Gestionnaire de rapports de sorte qu'il utilise une URL de serveur de rapports spécifique](#ConfigureSpecificURL)  
  
     Par défaut, le Gestionnaire de rapports se connecte au service Web Report Server qui s'exécute dans le même service Report Server. Le Gestionnaire de rapports utilise l'URL du service Web Report Server pour établir cette connexion. Si vous définissez plusieurs URL pour le service Web Report Server, le Gestionnaire de rapports utilise la dernière que vous avez définie. Toutefois, pour certains déploiements, vous souhaiterez peut-être que le Gestionnaire de rapports se connecte toujours au service Web via une URL statique. En effet, si vous avez configuré le filtrage des paquets sur un port ou une adresse IP spécifique et que vous souhaitez que toutes les connexions au serveur de rapports se soumettent aux règles de filtrage que vous avez définies, vous utiliserez une URL statique.  
  
-   [Faire pointer le Gestionnaire de rapports sur un serveur de rapports distant](#ConfigureRemoteRS)  
  
     Par défaut, le Gestionnaire de rapports fournit un accès frontal au service Web Report Server qui s'exécute dans la même instance du serveur. Toutefois, vous pouvez configurer le Gestionnaire de rapports de sorte qu'il se connecte à un service Web Report Server distant si vous souhaitez exécuter le service Web et le Gestionnaire de rapports dans des processus distincts ou si vous configurez l'accès au serveur différemment pour chaque serveur (par exemple, si vous déployez le Gestionnaire de rapports pour des utilisateurs sur une connexion extranet ou Internet et que vous souhaitez placer un pare-feu entre le serveur de rapports et le Gestionnaire de rapports).  
  
-   [Personnaliser les styles et le titre de l'application](#ModifyTitle)  
  
     Le Gestionnaire de rapports, la visionneuse de rapports HTML et la barre d'outils Rapport peuvent être personnalisés de façons limitées en modifiant les styles et en éditant le titre de l'application qui apparaît dans le Gestionnaire de rapports.  
  
-   [Désactiver le Gestionnaire de rapports](#DisableRM)  
  
     Lorsque vous installez une instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui utilise le mode natif, le Gestionnaire de rapports est activé par défaut. Toutefois, vous pouvez désactiver le Gestionnaire de rapports si une application frontale personnalisée fournit des fonctionnalités équivalentes, si vous souhaitez simplement utiliser les interfaces SOAP ou URL Access pour accéder au serveur de rapports, ou si vous utilisez le Gestionnaire de rapports d'une autre instance du serveur de rapports.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour utiliser le Gestionnaire de rapports, vous devez satisfaire aux conditions préalables suivantes :  
  
-   Vous devez disposer d'un serveur de rapports doté d'une configuration minimale. Pour plus d’informations sur la configuration minimale d’un serveur de rapports, consultez [Configurer un serveur de rapports &#40;Reporting Services en mode natif&#41;](configure-a-report-server-reporting-services-native-mode.md).  
  
-   Votre serveur de rapports doit s'exécuter en mode natif. Vous ne pouvez pas utiliser le Gestionnaire de rapports avec un serveur de rapports configuré pour le mode intégré SharePoint. Dans SQL Server 2012, vous ne pouvez pas basculer un serveur de rapports d'un mode à un autre. Si vous souhaitez modifier le type de serveur de rapports que votre environnement utilise, vous devez installer le mode souhaité du serveur de rapports, puis copier ou déplacer les éléments de rapport vers le nouveau serveur de rapports. Ce processus est habituellement désigné sous le terme de « migration ». Les étapes nécessaires pour la migration dépendent du mode vers lequel vous effectuez la migration et de la version d'origine de la migration. Pour plus d'informations, consultez [Upgrade and Migrate Reporting Services](../install-windows/upgrade-and-migrate-reporting-services.md).  
  
-   Internet Explorer 7.0 ou version ultérieure avec activation des scripts doit également être installé. Pour plus d’informations, consultez [planification pour Reporting Services et la prise en charge du navigateur Power View &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).  
  
##  <a name="ConfigureRMURL"></a> Configurer le Gestionnaire de rapports de sorte qu'il utilise l'URL par défaut  
 Par défaut, l'URL du Gestionnaire de rapports est formé d'un nom de répertoire virtuel unique, plus le port et le nom d'hôte défini pour le service Web Report Server qui s'exécute dans la même instance. Dans la plupart des cas, le nom d'hôte est le nom de réseau du serveur de rapports, mais il peut également s'agir d'une adresse IP ou d'un en-tête d'hôte qui résout l'ordinateur. Pour configurer le Gestionnaire de rapports de sorte qu'il utilise l'URL par défaut, utilisez la page **URL du Gestionnaire de rapports** dans l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
#### <a name="to-configure-the-default-report-manager-url-and-virtual-directory"></a>Pour configurer l'URL et le répertoire virtuel par défaut du Gestionnaire de rapports  
  
1.  Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis connectez-vous à l'instance du serveur de rapports.  
  
2.  Dans l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , cliquez sur **URL du Gestionnaire de rapports** pour ouvrir la page permettant de configurer l'URL.  
  
3.  Entrez un nom de répertoire virtuel unique pour le Gestionnaire de rapports.  
  
4.  Cliquez sur **Appliquer**.  
  
5.  Si vous utilisez [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] ou Windows Server 2008, des étapes supplémentaires peuvent être requises pour pouvoir ouvrir le Gestionnaire de rapports. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
##  <a name="ConfigureSpecificURL"></a> Configurer le Gestionnaire de rapports de sorte qu'il utilise une URL de serveur de rapports spécifique  
 Lorsque vous configurez des URL dans l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , le Gestionnaire de rapports détecte et utilise automatiquement toute nouvelle URL ou URL mise à jour pour le serveur de rapports qui s'exécute dans la même instance du serveur. Si votre déploiement exige que vous utilisiez une URL statique unique pour toutes les demandes de serveur de rapports, vous pouvez spécifier cette URL dans le fichier RSReportServer.config.  
  
#### <a name="to-configure-a-static-report-server-url"></a>Pour configurer une URL de serveur de rapports statique  
  
1.  Ouvrez le fichier **RSReportServer.config** dans un éditeur de texte. Par défaut, celui-ci se trouve dans le dossier \Program Files\Microsoft SQL Server\MSRS12.\<*nom_instance*>\Reporting Services\ReportServer.  
  
2.  Recherchez `ReportServerURL`.  
  
3.  Remplacez-le par l'URL de l'instance du serveur de rapports.  
  
4.  Enregistrez vos modifications et fermez le fichier.  
  
 Pour plus d’informations sur le fichier de configuration, consultez [modifier un fichier de Configuration de Reporting Services &#40;RSreportserver.config&#41; ](modify-a-reporting-services-configuration-file-rsreportserver-config.md) et [fichier de Configuration RSReportServer](rsreportserver-config-configuration-file.md).  
  
##  <a name="ConfigureRemoteRS"></a> Configurer le Gestionnaire de rapports de sorte qu'il utilise un serveur de rapports distant  
 Dans les configurations de déploiement qui placent le Gestionnaire de rapports et le serveur de rapports sur des ordinateurs distincts, vous devez avoir deux installations distinctes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Le Gestionnaire de rapports est incorporé dans le service Report Server et ne peut pas être installé par lui-même. Si vous souhaitez exécuter le Gestionnaire de rapports sur un autre ordinateur dans son propre processus, vous devez installer un second serveur de rapports. Les deux instances du serveur doivent être des serveurs de rapports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
#### <a name="to-connect-report-manager-to-a-remote-report-server-instance"></a>Pour connecter le Gestionnaire de rapports à une instance distante du serveur de rapports  
  
1.  Installez deux instances du serveur de rapports  
  
2.  Configurez la première installation qui hébergera le serveur de rapports :  
  
    1.  Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
    2.  Cliquez sur **URL du service Web** pour configurer un nom d'hôte, un port et un répertoire virtuel pour le serveur de rapports.  
  
    3.  Cliquez sur **Base de données** pour configurer la base de données du serveur de rapports.  
  
3.  Configurez la seconde installation qui hébergera le Gestionnaire de rapports :  
  
    1.  Démarrez l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
    2.  Cliquez sur **URL du Gestionnaire de rapports** pour entrer un nom de répertoire virtuel pour le Gestionnaire de rapports.  
  
     Ne configurez pas la base de données. Ne testez pas les URL.  
  
4.  Sur l'ordinateur Gestionnaire de rapports, modifiez les paramètres de configuration dans le fichier RSReportServer.config de manière à pointer sur l'instance distante du serveur de rapports. Au démarrage, le Gestionnaire de rapports lira le fichier de configuration afin d'obtenir l'URL du serveur de rapports :  
  
    1.  Ouvrez RSReportServer.config dans un éditeur de texte. Par défaut, il se trouve dans \Program Files\Microsoft SQL Server\MSRS11. \< *instancename*> \Reporting.  
  
    2.  Recherchez `ReportServerURL`.  
  
    3.  Remplacez-le par l'URL de l'instance distante du serveur de rapports.  
  
    4.  Enregistrez vos modifications et fermez le fichier.  
  
5.  > [!TIP]  
    >  Si nécessaire, activez le port 80 sur les deux ordinateurs afin d'autoriser les requêtes sur ce port. Pour plus d’informations, consultez [Configurer un pare-feu pour accéder au serveur de rapports](configure-a-firewall-for-report-server-access.md).  
  
6.  Redémarrez le serveur de rapports.  
  
7.  Ouvrez le Gestionnaire de rapports dans une fenêtre du navigateur. S'il est déjà ouvert, actualisez le navigateur pour vérifier que le Gestionnaire de rapports est connecté au serveur distant. Le contenu du serveur cible doit être affiché.  
  
8.  Désactivez les fonctionnalités du serveur que vous n'utilisez pas :  
  
    -   Sur l'ordinateur Gestionnaire de rapports, désactivez `WebServiceAndHTTPAccessEnabled` et `ScheduleEventsAndReportDeliveryEnabled`.  
  
    -   Sur l'ordinateur Serveur de rapports, désactivez `ReportManagerEnabled`.  
  
 Pour plus d’informations sur la désactivation des fonctionnalités, consultez la section [Activer ou désactiver les fonctionnalités Reporting Services](turn-reporting-services-features-on-or-off.md).  
  
##  <a name="ModifyTitle"></a> Personnaliser les styles ou le titre de l'application  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ne prend pas en charge la personnalisation des feuilles de style du Gestionnaire de rapports. Toutefois, si vous avez des compétences dans le développement Web, vous pouvez modifier les styles à vos propres risques. Pour plus d’informations sur les fichiers contenant des informations de style, consultez [Personnaliser des feuilles de style pour la visionneuse HTML et pour le Gestionnaire de rapports](../customize-style-sheets-for-html-viewer-and-report-manager.md).  
  
 Le Gestionnaire de rapports contient un titre d'application qui apparaît au haut de la page. Par défaut, ce titre est **SQL Server Reporting Services**. Ce titre peut être personnalisé. Pour modifier le titre, utilisez la page Paramètres du site dans le Gestionnaire de rapports. Pour modifier les paramètres de l'application dans le Gestionnaire de rapports et définir les propriétés sur la page Paramètres du site, le rôle **Administrateur système** doit vous être attribué. Pour pouvoir voir le titre de l'application, le rôle **Utilisateur système** doit être attribué à l'utilisateur.  
  
#### <a name="to-modify-application-title"></a>Pour modifier le titre de l'application  
  
1.  Connectez-vous à l'aide d'un compte auquel les autorisations **Administrateur système** sont assignées sur le serveur de rapports.  
  
2.  Ouvrez Internet Explorer.  
  
3.  Entrez l'URL du Gestionnaire de rapports. Par défaut, il s’agit de http://\<**nom_de_votre_serveur**>/reports, mais si vous avez installé Reporting Services sous la forme d’une instance nommée, l’URL par défaut sera http://\<**nom_de_votre_serveur**>/reports\<**_nominstance**>.  
  
4.  Cliquez sur **Paramètres du site**.  
  
5.  Sous l'onglet **Général** , dans **Nom**, remplacez **SQL Server Reporting Services** par un nom différent.  
  
6.  Cliquez sur **Appliquer**.  
  
##  <a name="DisableRM"></a> Turn Off Report Manager  
 Vous pouvez désactiver le Gestionnaire de rapports si une application personnalisée fournit des fonctionnalités équivalentes ou si vous utilisez l'application Gestionnaire de rapports d'une instance distincte du service. Pour désactiver le Gestionnaire de rapports, vous pouvez modifier le fichier RSReportServer.config.  
  
#### <a name="to-turn-off-report-manager"></a>Pour désactiver le Gestionnaire de rapports  
  
1.  Ouvrez le fichier RSReportServer.config dans un éditeur de texte. Par défaut, il se trouve dans \Program Files\Microsoft SQL Server\MSRS11. \< *instancename*> \Reporting.  
  
2.  Recherchez **IsReportManagerEnabled**.  
  
3.  Affectez la valeur **False**.  
  
4.  Enregistrez vos modifications et fermez le fichier.  
  
 Pour plus d’informations sur la façon de modifier le fichier de configuration, consultez [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md). Pour plus d’informations sur la désactivation des fonctionnalités dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Activer ou désactiver les fonctionnalités Reporting Services](turn-reporting-services-features-on-or-off.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md)   
 [Planification pour Reporting Services et la prise en charge du navigateur Power View &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)   
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Vérifier une installation de Reporting Services](../install-windows/verify-a-reporting-services-installation.md)   
 [Personnaliser des feuilles de style pour la visionneuse HTML et pour le Gestionnaire de rapports](../customize-style-sheets-for-html-viewer-and-report-manager.md)   
 [Activer ou désactiver les fonctionnalités Reporting Services](turn-reporting-services-features-on-or-off.md)   
 [Gérer un serveur de rapports Reporting Services (SSRS) en mode natif](manage-a-reporting-services-native-mode-report-server.md)   
 [Fichier de Configuration RSReportServer](rsreportserver-config-configuration-file.md)   
 [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)  
  
  
