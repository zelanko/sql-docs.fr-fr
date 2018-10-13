---
title: Installer le serveur de rapports en Mode natif de Services Reporting | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- report servers [Reporting Services], default configurations
- installation options [Reporting Services]
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9bfbae24063bfa3daa7fbafd1004125e826f6886
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851864"
---
# <a name="install-reporting-services-native-mode-report-server"></a>Installer le serveur de rapports Reporting Services en mode natif
  Un serveur de rapports en mode natif [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peut être installé via l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou à partir de la ligne de commande. Dans l'Assistant Installation, vous pouvez choisir 1) d'installer les fichiers te de configurer le serveur avec les paramètres par défaut ou 2) d'installer uniquement les fichiers et le serveur n'est pas configuré par l'Assistant Installation. Cette rubrique passe en revue *la configuration par défaut pour le mode natif* où le programme d'installation installe et configure une instance de serveur de rapports. Une fois l'installation terminée, le serveur de rapports fonctionne et est opérationnel. Un serveur de rapports en mode natif s'exécute comme serveur d'applications autonome. Le mode natif est le mode serveur par défaut.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif|  
  
##  <a name="bkmk_top"></a> Dans cette rubrique  
  
-   [Quelle est la Configuration par défaut ?](#bkmk_whatisdefaultconfiguration)  
  
-   [Quand installer la Configuration par défaut pour le Mode natif](#bkmk_whentoinstalldefaultconfig)  
  
-   [Spécifications](#bkmk_requirements)  
  
-   [Réservations d’URL par défaut](#bkmk_defaultURLreservations)  
  
-   [Installer le Mode natif avec l’Assistant Installation de SQL Server](#bkmk_installwithwizard)  
  
-   [Installer le Mode natif avec la ligne de commande](#bkmk_commandline)  
  
##  <a name="bkmk_whatisdefaultconfiguration"></a> Quelle est la Configuration par défaut ?  
 Le programme d'installation installe les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] suivantes lorsque vous sélectionnez la configuration par défaut de l'option de mode natif :  
  
-   Le service Report Server (lequel inclut le service Web Report Server, application de traitement en arrière-plan, et le gestionnaire de rapports)  
  
-   Le gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   Les outils de ligne de commande [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsconfig.exe, rskeymgmt.exe et rs.exe)  
  
 Cette option ne s'applique pas aux fonctionnalités partagées telles que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], qui doivent être spécifiées comme éléments séparés si vous souhaitez les installer.  
  
 L'installation configure les éléments suivants pour une installation de serveur de rapports en mode natif :  
  
-   Compte de service pour le service Report Server.  
  
-   URL du service Web Report Server.  
  
-   URL du Gestionnaire de rapports.  
  
-   Base de données du serveur de rapports.  
  
-   Accès des comptes de service aux bases de données Report Server  
  
-   Connexion DSN aux bases du serveur de rapports.  
  
 L'installation ne configure pas le compte d'exécution sans assistance, la messagerie électronique de serveur de rapports, la sauvegarde des clés de chiffrement ou le déploiement avec montée en puissance parallèle. Vous pouvez utiliser le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour configurer ces propriétés. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
##  <a name="bkmk_whentoinstalldefaultconfig"></a> Quand installer la Configuration par défaut pour le Mode natif  
 Une configuration par défaut installe [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans un état opérationnel afin que vous puissiez utiliser immédiatement le serveur de rapports une fois l'installation terminée. Spécifiez ce mode lorsque vous souhaitez économiser des étapes en éliminant toutes les tâches de configuration requises que vous devriez autrement exécuter dans l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 L'installation de la configuration par défaut ne garantit pas que le serveur de rapports fonctionne après que l'installation est terminée. L'inscription des URL par défaut peut ne pas s'effectuer quand le service démarre. Testez toujours votre installation pour vérifier que le service démarre et s'exécute comme prévu.  
  
##  <a name="bkmk_requirements"></a> Spécifications  
 L'option de configuration par défaut utilise les valeurs par défaut pour configurer les paramètres principaux obligatoires pour rendre un serveur de rapports opérationnel. Elle comporte les impératifs suivants :  
  
-   Votre matériel doit correspondre aux configurations matérielle et logicielle minimales requises pour l'exécution de Microsoft SQL Server. Pour plus d'informations, consultez [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] doivent être installés ensemble dans la même instance. L'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] héberge la base de données du serveur de rapports que le programme d'installation crée et configure.  
  
-   Le compte d'utilisateur utilisé pour exécuter le programme d'installation doit être membre du groupe local Administrateurs et avoir l'autorisation de créer des bases de données et d'y accéder sur l'instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui héberge les bases de données du serveur de rapports.  
  
-   L'installation doit être en mesure d'utiliser les valeurs par défaut pour réserver les URL qui fournissent l'accès au serveur de rapports et au Gestionnaire de rapports. Ces valeurs sont le port 80, un caractère générique fort et les noms de répertoire virtuel aux formats **ReportServer_\<***nom_instance***>** et **Reports_\<***nom_instance***>**.  
  
-   L'installation doit être en mesure d'utiliser les valeurs par défaut pour créer les bases de données du serveur de rapports. Ces valeurs sont **ReportServer** et **ReportServerTempDB**. Si vous avez des bases de données d'une précédente installation, le programme d'installation sera bloqué car il ne peut pas configurer le serveur de rapports dans la configuration par défaut pour le mode natif. Vous devez renommer, déplacer ou supprimer les bases de données pour débloquer le programme d'installation.  
  
 Si votre ordinateur ne satisfait pas à toutes les spécifications d'une installation par défaut, vous devez installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode fichiers uniquement, puis utiliser le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour le configurer une fois l'installation terminée.  
  
 N'essayez pas de reconfigurer votre ordinateur uniquement pour autoriser une installation par défaut à se poursuivre. Un tel choix pourrait nécessiter plusieurs heures de travail, en éliminant concrètement l'avantage en termes de gain de temps que l'option d'installation fournit. La meilleure solution consiste à installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode fichiers uniquement, puis à configurer le serveur de rapports pour utiliser des valeurs spécifiques.  
  
##  <a name="bkmk_defaultURLreservations"></a> Réservations d’URL par défaut  
 Les réservations d'URL se composent d'un préfixe, d'un nom d'hôte, d'un port et d'un répertoire virtuel :  
  
|Élément|Description|  
|----------|-----------------|  
|Prefix|Le préfixe par défaut est HTTP. Si vous avez préalablement installé un certificat SSL (Secure Sockets Layer), l'installation tente de créer des réservations d'URL qui utilisent le préfixe HTTPS.|  
|Nom d'hôte|Le nom d'hôte par défaut est un caractère générique fort (+). Il spécifie que le serveur de rapports accepte toute requête HTTP sur le port désigné pour tout nom d’hôte qui correspond à l’ordinateur, y compris http://\<nom_ordinateur > / reportserver, http://localhost/reportserver, ou http://\<IPAddress > / ReportServer.|  
|d’|Le port par défaut est 80. Notez que si vous utilisez un port autre que le port 80, vous devez l'ajouter explicitement à l'URL lorsque vous ouvrez une application Web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans une fenêtre de navigateur.|  
|Répertoire virtuel|Par défaut, les répertoires virtuels sont créés au format ReportServer_\<*nom_instance*> pour le service Web Report Server et Reports_\<*nom_instance*> pour le Gestionnaire de rapports. Pour le service Web Report Server, le répertoire virtuel par défaut est **reportserver**. Par défaut, le répertoire virtuel du Gestionnaire de rapports est **reports**.|  
  
 Voici un exemple de chaîne URL complète :  
  
-   http://+:80/reportserver fournit l’accès au serveur de rapports.  
  
-   http://+:80/reports, permet d’accéder au Gestionnaire de rapports.  
  
##  <a name="bkmk_installwithwizard"></a> Installer le Mode natif avec l’Assistant Installation de SQL Server  
 La liste suivante décrit les étapes et les options spécifiques à  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous pouvez sélectionner dans l'Assistant Installation de SQL Server. La liste ne décrit pas chacune des pages que vous voyez dans l'Assistant Installation. Seules les pages relatives à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et qui font partie d'une installation en mode natif sont décrites.  
  
1.  Dans la page **Rôle d'installation** , sélectionnez **Installation de fonctionnalités SQL Server**.  
  
     ![Installation des fonctionnalités SQL Server pour le rôle d’installation](../../../2014/sql-server/install/media/rs-setuprole.gif "Installation des fonctionnalités SQL Server pour le rôle d’installation")  
  
2.  Dans la page **Sélection de fonctionnalités** , sélectionnez ce qui suit :  
  
    -   **Services Moteur de base de données**, à moins qu'une instance du moteur de base de données ne soit déjà installée.  
  
    -   **Reporting Services - Natif**.  
  
    -   **Outils de gestion - De base**. Les outils d'administration ne sont pas nécessaires mais ils sont recommandés, sauf si vous disposez déjà d'une autre installation d'outils d'administration. L’option de configuration par défaut entraîne un serveur de rapports opérationnel mais vous souhaiterez peut-être modifier les options de configuration à une date ultérieure. Certaines options telles que « Mes rapports » sont gérées via [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
     ![SSRS en mode natif sélectionné lors de la sélection de fonctionnalités](../../../2014/sql-server/install/media/rs-setupfeatureselection-native-withcircles.gif "SSRS en mode natif sélectionné lors de la sélection de fonctionnalités")  
  
3.  Si vous envisagez d'utiliser la fonctionnalité d'abonnement de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vérifiez dans la page **Configuration du serveur** si SQL Server Agent est configuré pour le type de démarrage **Automatique** .  
  
4.  Dans la page **Configuration de Reporting Services** , sélectionnez **Installer et configurer**.  
  
     ![Configuration de SSRS en mode natif](../../../2014/sql-server/install/media/rs-setupconfiguration-native-with-circles.gif "Configuration de SSRS en mode natif")  
  
5.  Une fois l'Assistant Installation de SQL Server terminé, vérifiez l'installation du mode natif par défaut à l'aide des étapes de base suivantes.  
  
    -   Ouvrez le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis vérifiez que vous pouvez vous connecter au serveur de rapports.  
  
    -   Ouvrez votre navigateur avec des privilèges d'administrateur et connectez-vous au Gestionnaire de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , par exemple `http://loclahost/Reports`.  
  
    -   Ouvrez votre navigateur avec des privilèges d'administrateur et connectez-vous à la page du serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Par exemple,  `http://loclahost/ReportServer`  
  
 Pour plus d'informations, consultez la section relative au mode natif dans les deux rubriques suivantes :  
  
 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)  
  
 [Résoudre les problèmes d’une installation de Reporting Services](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)  
  
##  <a name="bkmk_commandline"></a> Installer le Mode natif avec la ligne de commande  
 L'exemple suivant inclut le service [!INCLUDE[ssDE](../../includes/ssde-md.md)] parce qu'il est requis pour une configuration par défaut.  
  
```  
setup /q /ACTION=install /FEATURES=SQL,RS,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS"   
/RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK   
SERVICE" /RSSVCSTARTUPTYPE="Manual" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
 Pour plus d’informations et des exemples, consultez [invite de commandes de Reporting Services SharePoint Mode d’Installation et en Mode natif](../../reporting-services/install-windows/install-reporting-services-at-the-command-prompt.md) et [installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Dépanner une installation de Reporting Services](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Installation de fichiers uniquement &#40;Reporting Services&#41;](../../reporting-services/install-windows/files-only-installation-reporting-services.md)   
 [Initialiser un serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Configurer des connexions SSL sur un serveur de rapports en mode natif](../security/configure-ssl-connections-on-a-native-mode-report-server.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [Installation de démarrage rapide de SQL Server 2014](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
