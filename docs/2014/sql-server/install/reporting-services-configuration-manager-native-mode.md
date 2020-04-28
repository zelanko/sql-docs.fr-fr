---
title: Gestionnaire de configuration de Reporting Services (mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
- components [Reporting Services], Reporting Services Configuration tool
ms.assetid: 379eab68-7f13-4997-8d64-38810240756e
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: e7b5e46b90702bf39bf2902eed3e5a6c609757e0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952495"
---
# <a name="reporting-services-configuration-manager-native-mode"></a>Gestionnaire de configurations de Reporting Services (mode natif)
  Utilisez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour configurer une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif. Si vous avez installé un serveur de rapports à l'aide de l'option d'installation de fichiers uniquement, vous devez utiliser le gestionnaire de configuration pour configurer le serveur avant de pouvoir vous en servir. Si vous avez installé un serveur de rapports à l'aide de l'option d'installation de configuration par défaut, vous pouvez utiliser le gestionnaire de configuration pour vérifier ou modifier les paramètres spécifiés au cours de l'installation. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peut servir à configurer une instance de serveur de rapports locale ou distante.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode natif.  
  
> [!NOTE]  
>  À compter de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , le gestionnaire de configuration d' [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne gère plus les serveurs de rapports en mode SharePoint. Le mode SharePoint est géré et configuré à l'aide de l'Administration centrale et des scripts PowerShell SharePoint. Pour plus d’informations, consultez [Reporting Services installation en mode sharepoint &#40;sharepoint 2010 et sharepoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
 **Dans cette section :**  
  
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Fournit des recommandations et des procédures pour la modification du compte de service et du mot de passe.  
  
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Décrit comment configurer les URL qui servent à accéder au service Web Report Server et au Gestionnaire de rapports.  
  
 [Créer une base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 Décrit le mode de création d'une base de données du serveur de rapports, tel qu'il est exigé pour le stockage des objets et des métadonnées de serveur.  
  
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Décrit le mode de modification de la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la base de données du serveur de rapports.  
  
 [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Décrit comment configurer un compte d'utilisateur de manière à traiter les rapports en mode sans assistance.  
  
 [Configurer un serveur de rapports pour la remise par messagerie &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Décrit comment configurer un serveur de rapports pour la prise en charge de la distribution des rapports par courrier électronique.  
  
 [Configurer un déploiement avec montée en puissance parallèle de serveurs de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 Fournit des informations sur la configuration de plusieurs instances du serveur de rapports pour utiliser une base de données partagée du serveur de rapports.  
  
 [Configurer et gérer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
 Explique comment utiliser et gérer les clés de chiffrement utilisées pour le stockage de données sensibles.  
  
 [Gérer un serveur de rapports Reporting Services en mode natif](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
 Fournit des instructions, étape par étape, pour les tâches les plus courantes.  
  
 [Gestionnaire de configuration de Reporting Services les rubriques d’aide F1 &#40;le mode natif SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
 Fournit des rubriques d'aide sur les pages de l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 **Dans cette rubrique :**  
  
-   [Scénarios d'utilisation du gestionnaire de configuration de Reporting Services](#bkmk_scenarios)  
  
-   [Configuration requise](#bkmk_requirements)  
  
-   [Pour démarrer le gestionnaire de configuration de Reporting Services](#bkmk_start_configuration_manager)  
  
##  <a name="scenarios-to-use-reporting-services-configuration-manager"></a><a name="bkmk_scenarios"></a>Scénarios à utiliser Gestionnaire de configuration de Reporting Services  
 Utilisez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour effectuer les tâches suivantes :  
  
-   Configurer le compte de service Report Server. Le compte est initialement configuré au cours de l'installation et il est modifiable par le biais du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] si vous voulez mettre le mot de passe à jour ou utiliser un compte différent.  
  
-   Créer et configurer des URL. Le serveur de rapports et le Gestionnaire de rapports sont des applications [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] accessibles via des URL. L'URL du serveur de rapports offre un accès aux points de terminaison SOAP du serveur de rapports, tandis que l'URL du Gestionnaire de rapports s'utilise pour ouvrir le Gestionnaire de rapports. Vous pouvez configurer une URL unique ou plusieurs URL pour chaque application.  
  
-   Créer et configurer la base de données du serveur de rapports. Le serveur de rapports est un serveur sans état qui utilise une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le stockage interne. Vous pouvez utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour créer et configurer une connexion à la base de données du serveur de rapports. Vous avez également la possibilité de sélectionner une base de données existante qui contient déjà le contenu que vous souhaitez utiliser.  
  
-   Configurer un déploiement avec montée en puissance parallèle en mode natif. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prend en charge une topologie de déploiement qui permet à plusieurs instances de serveur de rapports d'utiliser une seule base de données partagée de serveur de rapports. Pour développer un déploiement avec montée en puissance parallèle de serveurs de rapports, vous utilisez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour connecter chaque serveur de rapports à la base de données de serveur de rapports partagée.  
  
-   Sauvegarder, restaurer ou remplacer la clé symétrique utilisée pour chiffrer des chaînes de connexion stockées et des informations d'identification. Vous devez avoir une sauvegarde de la clé symétrique si vous modifiez le compte de service ou si vous déplacez une base de données de serveur de rapports vers un autre ordinateur.  
  
-   Configurer le compte d'exécution sans assistance. Ce compte est utilisé pour les connexions distantes au cours d'opérations planifiées ou lorsque les informations d'identification de l'utilisateur ne sont pas disponibles.  
  
-   Configurer la messagerie Report Server. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] comprend une extension de remise par messagerie de serveur de rapports qui utilise un protocole SMTP (Simple Mail Transfer Protocol) pour remettre des rapports ou une notification de traitement des rapports à une boîte aux lettres électronique. Vous pouvez utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour spécifier le serveur ou la passerelle SMTP sur votre réseau à utiliser pour cette remise.  
  
 Vous ne pouvez pas utiliser le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour gérer le contenu du serveur de rapports, activer des fonctionnalités supplémentaires ou accorder l'accès au serveur. Le déploiement complet requiert que vous utilisiez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] également pour activer des fonctionnalités supplémentaires ou modifier des valeurs par défaut, et gestionnaire de rapports pour accorder à l’utilisateur l’accès au serveur.  
  
##  <a name="requirements"></a><a name="bkmk_requirements"></a> Spécifications  
 Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est spécifique à la version. Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé avec cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas être utilisé pour configurer une version antérieure de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si vous exécutez des versions anciennes et récentes d' [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] côte à côte sur le même ordinateur, vous devez utiliser le gestionnaire de configuration Reporting Services fourni avec chaque version pour configurer chaque instance.  
  
 Pour utiliser le gestionnairel de configuration d' [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous devez respecter les conditions suivantes :  
  
-   Vous devez disposer d'autorisations d'administrateur système local sur l'ordinateur qui héberge le serveur de rapports que vous configurez. Si vous configurez un ordinateur distant, vous devez également disposer d'autorisations d'administrateur système local sur cet ordinateur.  
  
-   Vous devez être autorisé à créer des bases de données sur le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilisé pour héberger la base de données du serveur de rapports.  
  
-   Le service WMI (Windows Management Instrumentation) doit être activé et en cours d'exécution sur tous les serveurs de rapports que vous configurez. Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise le fournisseur WMI du serveur de rapports pour se connecter aux serveurs de rapports locaux et distants. Si vous configurez un serveur de rapports distant, l'ordinateur doit également utiliser l'accès WMI à distance. Pour plus d’informations, consultez [Configurer un serveur de rapports pour l’administration à distance](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md).  
  
-   Pour pouvoir configurer une instance de serveur de rapports distante et vous y connecter, vous devez permettre aux appels WMI (Windows Management Instrumentation) distants de traverser le Pare-feu Windows. Pour plus d’informations, consultez [Configurer un serveur de rapports pour l’administration à distance](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 l’URL du [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé automatiquement lorsque vous installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
##  <a name="to-start-the-reporting-services-configuration-manager"></a><a name="bkmk_start_configuration_manager"></a>Pour démarrer le Gestionnaire de configuration de Reporting Services  
  
#### <a name="to-start-reporting-services-configuration"></a>Pour lancer la configuration de Reporting Services  
  
1.  Suivez l'étape appropriée pour votre version de Microsoft Windows :  
  
    -   Dans l'écran de démarrage de Windows, tapez **Reporting** et cliquez sur **Gestionnaire de configuration de Reporting Services** dans les résultats de la recherche.  
  
    -   Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], puis sur **Outils de configuration**.  
  
         Si vous souhaitez configurer une instance de serveur de rapports à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ouvrez le dossier de programme pour cette version. Par exemple, pointez sur [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] au lieu de [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] pour ouvrir les outils de configuration pour les composants serveur [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .  
  
         Cliquez sur **Gestionnaire de configuration de Reporting Services**.  
  
2.  La boîte de dialogue **Connexion de la configuration de Report Server** s'affiche pour que vous spécifiiez l'instance de serveur de rapports à configurer. Cliquez sur **Connecter**.  
  
3.  Dans **Nom du serveur**, spécifiez le nom de l'ordinateur sur lequel est installée l'instance de serveur de rapports. Le nom de l'ordinateur local apparaît par défaut, mais vous pouvez taper le nom d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] distante si vous souhaitez vous connecter à un serveur de rapports installé sur un ordinateur distant.  
  
4.  Si vous spécifiez un ordinateur distant, cliquez sur **Rechercher** pour établir une connexion.  
  
5.  Dans **Instance du serveur de rapports**, sélectionnez l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous souhaitez configurer. Seules les instances de serveur de rapports pour cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'affichent dans la liste. Vous ne pouvez pas configurer d'instances de versions antérieures de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
6.  Cliquez sur **Connecter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Outils de Reporting Services](../../reporting-services/tools/reporting-services-tools.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;SSRS Configuration Manager&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Gestionnaire de configuration SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
 [Configurer et administrer un serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
