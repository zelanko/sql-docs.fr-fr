---
title: "Gestionnaire de configurations de Reporting Services (mode natif) | Microsoft Docs"
ms.custom: ""
ms.date: "06/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Outil de configuration de Reporting Services"
  - "options de configuration [Reporting Services]"
  - "serveurs de rapports [Reporting Services], configuration"
  - "composants [Reporting Services], outil de configuration de Reporting Services."
ms.assetid: 379eab68-7f13-4997-8d64-38810240756e
caps.latest.revision: 49
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 46
---
# Gestionnaire de configurations de Reporting Services (mode natif)
  Utilisez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour configurer une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif. Si vous avez installé un serveur de rapports à l'aide de l'option d'installation de fichiers uniquement, vous devez utiliser le gestionnaire de configuration pour configurer le serveur avant de pouvoir vous en servir. Si vous avez installé un serveur de rapports à l'aide de l'option d'installation de configuration par défaut, vous pouvez utiliser le gestionnaire de configuration pour vérifier ou modifier les paramètres spécifiés au cours de l'installation. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peut servir à configurer une instance de serveur de rapports locale ou distante.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
> [!NOTE] À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , le gestionnaire de configuration d' [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne gère plus les serveurs de rapports en mode SharePoint. Le mode SharePoint est géré et configuré à l'aide de l'Administration centrale et des scripts PowerShell SharePoint.  
  
##  <a name="bkmk_scenarios"></a> Scénarios d'utilisation du gestionnaire de configuration de Reporting Services  
 Utilisez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour effectuer les tâches suivantes :  
  
-   Configurer le compte de service Report Server. Le compte est initialement configuré au cours de l'installation et il est modifiable par le biais du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] si vous voulez mettre le mot de passe à jour ou utiliser un compte différent.  
  
-   Créer et configurer des URL. Le serveur de rapports et le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] sont des applications [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] accessibles au moyen d’URL. L'URL du serveur de rapports offre un accès aux points de terminaison SOAP du serveur de rapports, tandis que l’URL du [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] permet d’ouvrir le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] . Vous pouvez configurer une URL unique ou plusieurs URL pour chaque application.  
  
-   Créer et configurer la base de données du serveur de rapports. Le serveur de rapports est un serveur sans état qui utilise une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le stockage interne. Vous pouvez utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour créer et configurer une connexion à la base de données du serveur de rapports. Vous avez également la possibilité de sélectionner une base de données existante qui contient déjà le contenu que vous souhaitez utiliser.  
  
-   Configurer un déploiement avec montée en puissance parallèle en mode natif. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prend en charge une topologie de déploiement qui permet à plusieurs instances de serveur de rapports d'utiliser une seule base de données partagée de serveur de rapports. Pour développer un déploiement avec montée en puissance parallèle de serveurs de rapports, vous utilisez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour connecter chaque serveur de rapports à la base de données de serveur de rapports partagée.  
  
-   Sauvegarder, restaurer ou remplacer la clé symétrique utilisée pour chiffrer des chaînes de connexion stockées et des informations d'identification. Vous devez avoir une sauvegarde de la clé symétrique si vous modifiez le compte de service ou si vous déplacez une base de données de serveur de rapports vers un autre ordinateur.  
  
-   Configurer le compte d'exécution sans assistance. Ce compte est utilisé pour les connexions distantes au cours d'opérations planifiées ou lorsque les informations d'identification de l'utilisateur ne sont pas disponibles.  
  
-   Configurer la messagerie Report Server. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend une extension de remise par messagerie de serveur de rapports qui utilise un protocole SMTP (Simple Mail Transfer Protocol) pour remettre des rapports ou une notification de traitement des rapports à une boîte aux lettres électronique. Vous pouvez utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour spécifier le serveur ou la passerelle SMTP sur votre réseau à utiliser pour cette remise.  
  
 Vous ne pouvez pas utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour gérer le contenu du serveur de rapports, activer des fonctionnalités supplémentaires ou accorder l'accès au serveur. Le déploiement complet requiert que vous utilisiez également [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour activer des fonctionnalités supplémentaires ou modifier des valeurs par défaut, ainsi que le Gestionnaire de rapports pour accorder aux utilisateurs l'accès au serveur.  
  
##  <a name="bkmk_requirements"></a> Spécifications  
 Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est spécifique à la version. Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé avec cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas être utilisé pour configurer une version antérieure de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si vous exécutez des versions anciennes et récentes d'[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] côte à côte sur le même ordinateur, vous devez utiliser le gestionnaire de configuration Reporting Services fourni avec chaque version pour configurer chaque instance.  
  
 Pour utiliser le gestionnairel de configuration d'[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez respecter les conditions suivantes :  
  
-   Vous devez disposer d'autorisations d'administrateur système local sur l'ordinateur qui héberge le serveur de rapports que vous configurez. Si vous configurez un ordinateur distant, vous devez également disposer d'autorisations d'administrateur système local sur cet ordinateur.  
  
-   Vous devez être autorisé à créer des bases de données sur le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilisé pour héberger la base de données du serveur de rapports.  
  
-   Le service WMI (Windows Management Instrumentation) doit être activé et en cours d'exécution sur tous les serveurs de rapports que vous configurez. Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise le fournisseur WMI du serveur de rapports pour se connecter aux serveurs de rapports locaux et distants. Si vous configurez un serveur de rapports distant, l'ordinateur doit également utiliser l'accès WMI à distance. Pour plus d’informations, consultez [Configurer un serveur de rapports pour l’administration à distance](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md).  
  
-   Pour pouvoir configurer une instance de serveur de rapports distante et vous y connecter, vous devez permettre aux appels WMI (Windows Management Instrumentation) distants de traverser le Pare-feu Windows. Pour plus d’informations, consultez [Configurer un serveur de rapports pour l’administration à distance](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 l’URL du [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé automatiquement lorsque vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
##  <a name="bkmk_start_configuration_manager"></a> Pour démarrer le gestionnaire de configuration de Reporting Services  
  
1.  Suivez l'étape appropriée pour votre version de Microsoft Windows :  
  
    -   Dans l'écran de démarrage de Windows, tapez **Reporting** et cliquez sur **Gestionnaire de configuration de Reporting Services** dans les résultats de la recherche.  
  
    -   Sélectionnez **Démarrer**, pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], puis sur **Outils de configuration**.  
  
         Si vous souhaitez configurer une instance de serveur de rapports à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ouvrez le dossier de programme pour cette version. Par exemple, pointez sur [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] au lieu de [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] pour ouvrir les outils de configuration pour les composants serveur [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
         Sélectionnez **Gestionnaire de configuration de Reporting Services**.  
  
2.  La boîte de dialogue **Connexion de la configuration de Report Server** s'affiche pour que vous spécifiiez l'instance de serveur de rapports à configurer. Sélectionnez **Se connecter**.  
  
3.  Dans **Nom du serveur**, spécifiez le nom de l'ordinateur sur lequel est installée l'instance de serveur de rapports. Le nom de l'ordinateur local apparaît par défaut, mais vous pouvez taper le nom d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] distante si vous souhaitez vous connecter à un serveur de rapports installé sur un ordinateur distant.  
  
4.  Si vous spécifiez un ordinateur distant, cliquez sur **Rechercher** pour établir une connexion.  
  
5.  Dans **Report Server Dansstance**, sélectionnez l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous souhaitez configurer. Seules les instances de serveur de rapports pour cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'affichent dans la liste. Vous ne pouvez pas configurer d'instances de versions antérieures de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
6.  Sélectionnez **Se connecter**.  
  
## Voir aussi  
 [Portail web &#40;SSRS en mode natif&#41;](../../reporting-services/web-portal-ssrs-native-mode.md)   
 [Outils de Reporting Services](../../reporting-services/tools/reporting-services-tools.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
 [Configurer et administrer un serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  