---
title: Résoudre les problèmes d’une installation Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: e2536f7f-d90c-4571-9ffd-6bbfe69018d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a9415e7258216c975dd066995bf347deca1d623
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75253198"
---
# <a name="troubleshoot-a-reporting-services-installation"></a>Dépanner une installation de Reporting Services
  Si vous ne parvenez pas à installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] suite à des erreurs qui se produisent durant l'installation, utilisez les instructions fournies dans cette rubrique pour étudier les conditions les plus susceptibles de provoquer des erreurs d'installation.  
  
 Pour obtenir les informations les plus récentes sur les problèmes liés à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez [Conseils, astuces et dépannage pour Reporting Services SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=221297).  
  
 Pour plus d'informations sur d'autres erreurs et problèmes liés à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , consultez [Résoudre les problèmes et erreurs de SSRS.](https://social.technet.microsoft.com/wiki/contents/articles/ssrs-troubleshooting-issues-and-errors.aspx)  
  
 Passez en revue les [notes de publication en ligne](https://go.microsoft.com/fwlink/?linkid=236893) si le problème que vous rencontrez est décrit dans les notes de publication.  
  
 Cette rubrique contient les informations suivantes :  
  
-   [Vérifier les journaux d’installation](#bkmk_setuplogs)  
  
-   [Vérifier la configuration requise](#bkmk_prereq)  
  
-   [Résoudre les problèmes liés aux installations en mode SharePoint](#bkmk_tshoot_sharepoint)  
  
-   [Résoudre les problèmes liés aux installations en mode natif](#bkmk_tshoot_native)  
  
-   [Ressources supplémentaires](#bkmk_additional)  
  
##  <a name="bkmk_setuplogs"></a>Vérifier les journaux d’installation  
 Les erreurs d'installation sont enregistrées dans des fichiers journaux, dans le dossier **Program Files\Microsoft SQL Server\110\Setup Bootstrap\Log** . Un sous-dossier est créé chaque fois que vous exécutez le programme d'installation. Le nom du sous-dossier est l'heure et la date d'exécution du programme d'installation. Pour obtenir des instructions sur la manière d’afficher les fichiers journaux d’installation, consultez [Afficher et lire les fichiers journaux d’installation de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
-   Les fichiers journaux incluent une collection de fichiers.  
  
-   Ouvrez le fichier *_summary.txt pour afficher des informations sur les produits, les composants et les instances.  
  
-   Ouvrez le fichier *_errorlog.txt pour afficher des informations sur les erreurs générées durant l'installation.  
  
-   Ouvrez le fichier *_RS\_\*_ComponentUpdateSetup.log pour consulter les informations de l’installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
##  <a name="bkmk_prereq"></a>Vérifier la configuration requise  
 Le programme d'installation vérifie automatiquement les conditions préalables. Toutefois, si vous tentez de résoudre des problèmes d'installation, il est utile de connaître les vérifications effectuées par le programme d'installation.  
  
-   Les spécifications relatives aux comptes pour l'exécution du programme d'installation incluent l'appartenance au groupe Administrateurs local. Le programme d'installation doit avoir l'autorisation d'ajouter des fichiers et des paramètres du Registre, de créer des groupes de sécurité locaux et de définir des autorisations. Si vous installez une configuration par défaut, le programme d'installation doit avoir l'autorisation de créer une base de données du serveur de rapports sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle vous effectuez l'installation.  
  
-   Le système d'exploitation doit prendre en charge HTTP.SYS 1.1.  
  
-   Le service HTTP doit être activé et en cours d'exécution.  
  
-   Le Coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator) doit s'exécuter si vous installez également le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
-   Authz.dll doit être présent dans le dossier System32.  
  
 Le programme d'installation ne recherche plus les services Internet (IIS) ou [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]nécessite MDAC 2,0 et la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] version 2,0 ; Si elles ne sont pas déjà installées, le programme d’installation les installe.  
  
##  <a name="bkmk_tshoot_sharepoint"></a>Résoudre les problèmes liés aux installations en mode SharePoint  
  
-   [Gestionnaire de configuration de Reporting Services ne démarre pas](#bkmk_configmanager_notstart)  
  
-   [Vous ne voyez pas le service SQL Server Reporting Services dans l'Administration centrale de SharePoint après avoir installé SQL Server 2012 SSRS en mode SharePoint](#bkmk_no_ssrs_service)  
  
-   [Les applets de commande Reporting Services PowerShell ne sont pas disponibles et les commandes ne sont pas reconnues](#bkmk_cmdlets_not_recognized)  
  
-   [Vous voyez un message d’erreur indiquant que l’URL n’est pas configurée](#bkmk_URL_not_configured)  
  
-   [Le programme d’installation échoue sur un ordinateur sur lequel SharePoint est installé, mais il n’est pas configuré](#bkmk_sharepoint_not_confiugred)  
  
-   [La page Administration centrale de SharePoint est vide](#bkmk_central_admin_blank)  
  
-   [Un message d’erreur s’affiche lorsque vous essayez de créer un rapport de Générateur de rapports](#bkmk_reportbuilder_newreport_error)  
  
-   [Vous voyez un message d’erreur indiquant que RS_SHP n’est pas pris en charge avec PREPAREIMAGE](#bkmk_RS_SHP_notsupported)  
  
###  <a name="bkmk_configmanager_notstart"></a>Gestionnaire de configuration de Reporting Services ne démarre pas  
 **Description :** Ce problème est lié à la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]conception dans. 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dispose dorénavant d'une architecture pour l'architecture de service SharePoint. Le Gestionnaire de configuration n'est plus nécessaire pour configurer et administrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.  
  
 **Solution de contournement :** Utilisez l’administration centrale de SharePoint pour configurer un serveur de rapports en mode SharePoint. Pour plus d’informations, consultez [Gérer une application de service SharePoint Reporting Services](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
###  <a name="bkmk_no_ssrs_service"></a>Vous ne voyez pas le service de SQL Server Reporting Services dans l’administration centrale de SharePoint après l’installation de SQL Server SSRS 2012 en mode SharePoint  
 **Description :** Si, après avoir [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] correctement installé en mode SharePoint [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et le complément pour SharePoint 2010, vous ne voyez pas « SQL Server Reporting Services » dans les deux menus suivants, le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service n’a pas été enregistré :  
  
-   Administration centrale de SharePoint 2010-> « gestion des applications »-> page « gérer les services sur le serveur »  
  
-   Administration centrale de SharePoint 2010-> « gestion des applications »-> « gérer les applications de service »-> menu « nouveau »  
  
 **Solution de contournement :** Pour inscrire et démarrer les [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] services SharePoint, procédez comme suit :  
  
1.  Sur l'ordinateur qui exécute l'Administration centrale de SharePoint 2010  
  
    1.  Ouvrez SharePoint 2010 Management Shell avec des privilèges d'administrateur. Cliquez avec le bouton droit sur l'icône et cliquez sur « Exécuter en tant qu'administrateur ». Exécutez les trois applets de commande suivantes à partir de l'interpréteur de commandes :  
  
    2.  ```powershell
        Install-SPRSService  
        ```  
  
    3.  ```powershell
        Install-SPRSServiceProxy  
        ```  
  
    4.  ```powershell
        Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
        ```  
  
2.  Vérifiez que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] le service affiche l’état «**démarré**» sur la page : administration centrale de SharePoint 2010-> «**gestion des applications**»-> « gérer les**services sur le serveur**»  
  
###  <a name="bkmk_cmdlets_not_recognized"></a>Les applets de commande Reporting Services PowerShell ne sont pas disponibles et les commandes ne sont pas reconnues  
 **Description :** Lorsque vous essayez d’exécuter une [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applet de commande PowerShell, un message d’erreur semblable au suivant s’affiche :  
  
-   Le terme « Install-SPRSServiceInstall-SPRSService » **n’est pas reconnu** comme nom d’applet de commande, fonction, fichier de script ou programme exécutable. Vérifiez l'orthographe du nom, ou si le chemin d'accès existe, vérifiez que le chemin d'accès est correct et réessayez. At line:1 char:39+ Install-SPRSServiceInstall-SPRSService <<<<    + CategoryInfo          : ObjectNotFound: (Install-SPRSServiceInstall-SPRSService:String) [], CommandNotFoundExcep  
  
 **Solution de contournement :** Effectuez l’une des opérations suivantes :  
  
-   Exécutez le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint. **rsSharePoint. msi**.  
  
-   Installez le mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à partir du support d'installation SQL Server.  
  
 **Remarque :** Si **SharePoint 2013 Management Shell** est ouvert lorsque vous effectuez l’une des solutions de contournement, fermez et rouvrez le shell de gestion.  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Installer Reporting Services mode SharePoint pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
-   [Installer le mode SharePoint de Reporting Services pour SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
###  <a name="bkmk_URL_not_configured"></a>Vous voyez un message d’erreur indiquant que l’URL n’est pas configurée  
 **Description :** Vous voyez s’afficher un message d’erreur semblable à ce qui suit :  
  
 Cette fonctionnalité SQL Server Reporting Services (SSRS) n'est pas prise en charge. Utilisez l'Administration centrale pour vérifier et résoudre un ou plusieurs des problèmes suivants : • Une URL de serveur de rapports n'est pas configurée. Utilisez la page d'intégration SSRS pour la configurer. • Le proxy d'application de service SSRS n'est pas configuré. Utilisez les pages d'application de service SSRS pour configurer le proxy. • L'application de service SSRS n'est pas mappée à cette application Web. Utilisez les pages d'application de service SSRS pour associer le proxy d'application de service SSRS au Groupe de proxy d'application pour cette application Web.  
  
 **Solution de contournement :** Le message d’erreur contient trois étapes suggérées pour corriger ce problème. La première suggestion dans le message « une URL de serveur de rapports n’est pas configurée.. ». s'applique lors de l'intégration à la version de serveur de rapports antérieure à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. La configuration SharePoint pour les versions de serveurs de rapports précédentes est effectuée dans la page **Paramètres généraux de l’application** , à l’aide de **SQL Server Reporting Services (2008 et 2008 R2)**.  
  
 **Plus d’informations :** Ce message d’erreur s’affiche lorsque vous tentez d’utiliser une [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fonctionnalité qui requiert une connexion au [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service. notamment :  
  
-   Ouverture du Générateur de rapports Microsoft SQL Server à partir d'une bibliothèque de documents SharePoint.  
  
-   Gestion des abonnements.  
  
-   Gestion d'une application de service.  
  
###  <a name="bkmk_sharepoint_not_confiugred"></a>Le programme d’installation échoue sur un ordinateur sur lequel SharePoint est installé, mais il n’est pas configuré  
 **Description :** Si vous choisissez d’installer Reporting Services mode SharePoint sur un ordinateur sur lequel SharePoint est installé mais que SharePoint n’est pas configuré, un message semblable au suivant s’affiche et l’installation s’arrête :  
  
 Le programme d'installation de SQL Server a cessé de fonctionner  
  
 **Solution de contournement :** Configurez SharePoint, puis exécutez SQL Server installation.  
  
 **Plus d’informations :** Lors de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] l’installation de dans et de l’installation SharePoint existante, le programme [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] d’installation tente d’installer et de démarrer le service SharePoint. Si SharePoint n'est pas configuré, le programme d'installation de service échoue, ce qui entraîne l'échec de l'installation.  
  
###  <a name="bkmk_central_admin_blank"></a>La page Administration centrale de SharePoint est vide  
 **Description :** Vous avez pu installer correctement SharePoint 2010, sans erreur d’installation. Toutefois, lorsque vous accédez à l'Administration centrale, vous voyez uniquement une page vide :  
  
 **Solution de contournement :** Ce problème n’est pas spécifique [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à, mais est lié à la configuration des autorisations dans votre installation SharePoint globale. La liste ci-dessous répertorie les suggestions :  
  
-   Consultez la rubrique SharePoint sur les environnements de développement. [Installation de l'environnement de développement pour SharePoint 2010 sur Windows Vista, Windows 7 et Windows Server 2008](https://msdn.microsoft.com/library/ee554869\(office.14\).aspx)  
  
-   Consultez la question du forum : [Central Administration returns page vierge après l’installation sur Windows 7](https://social.technet.microsoft.com/Forums/en/sharepoint2010setup/thread/a422a3c8-39f6-4b9e-988a-4c4d1e745694)  
  
-   Le compte de service que vous utilisez pour les services SharePoint tels que le service Administration centrale de SharePoint 2010 doit être doté des privilèges d'administrateur du système d'exploitation local.  
  
###  <a name="bkmk_reportbuilder_newreport_error"></a>Un message d’erreur s’affiche lorsque vous essayez de créer un rapport de Générateur de rapports  
 **Description :** Un message d’erreur semblable au suivant s’affiche lorsque vous tentez de créer un Générateur de rapports rapport à l’intérieur d’une bibliothèque de documents :  
  
 Cette fonctionnalité n'est pas prise en charge car une application de service SQL Server Reporting Services n'existe pas ou une URL de serveur de rapports n'a pas été configurée dans l'Administration centrale.  
  
 **Solution de contournement :** Vérifiez que vous disposez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] d’une application de service et qu’elle est correctement configurée. Pour plus d’informations, consultez la section « créer une application de service Reporting Services » dans [installer Reporting Services mode SharePoint pour sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
###  <a name="bkmk_RS_SHP_notsupported"></a>Vous voyez un message d’erreur indiquant que RS_SHP n’est pas pris en charge avec PREPAREIMAGE  
 **Description :** Lorsque vous essayez d’exécuter PREPAREIMAGE pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , un message d’erreur semblable au suivant s’affiche :  
  
 « La fonctionnalité spécifiée « RS_SHP » n’est pas prise en charge lors de l’exécution de l’action PREPAREIMAGE, car elle ne prend pas en charge SysPrep. Supprimez les fonctionnalités qui ne sont pas compatibles avec SysPrep et réexécutez le programme d'installation. »  
  
 **Solution de contournement :** Il n’existe aucune solution de contournement. 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne prend pas en charge SYSPREP (PREPAREIMAGE). 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne prends pas en charge SYSPREP.  
  
##  <a name="bkmk_tshoot_native"></a>Résoudre les problèmes liés aux installations en mode natif  
  
###  <a name="PerfCounters"></a>Les compteurs de performance ne sont pas visibles après la mise à niveau vers Windows Vista ou Windows Server 2008  
 Si vous mettez à niveau le système d'exploitation vers [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] ou [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] sur un ordinateur qui exécute [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les compteurs de performance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne seront pas définis après la mise à niveau.  
  
#### <a name="to-reinstate-reporting-services-performance-counters"></a>Pour rétablir les compteurs de performances Reporting Services  
  
1.  Supprimez les clés de Registre suivantes :  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service**  
  
    -   **HKLM\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service**  
  
2.  Ouvrez une fenêtre de commande et tapez la commande suivante à l'invite de commandes :  
  
    -   **Exécutez \< ** le *répertoire .NET 2,0 Framework* **> \< ** *répertoire bin du serveur de rapports* \installutil.exe **> \reportingserviceslibrary.dll**  
  
        > [!NOTE]  
        >  Remplacez \<le *répertoire .NET 2,0 Framework*> par le chemin d’accès physique des fichiers 2,0 .NET Framework \<et remplacez le *répertoire bin du serveur de rapports*> par le chemin d’accès physique des fichiers bin du serveur de rapports.  
  
3.  Redémarrez le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Pour vérifier que les opérations effectuées ont fonctionné, ouvrez un navigateur Web et accédez à l'URL du Gestionnaire de rapports ou à l'URL du serveur de rapports. Ouvrez ensuite l'Analyseur de performances pour vérifier que les compteurs fonctionnent.  
  
#### <a name="to-re-add-the-performance-registry-keys-by-using-registry-editor"></a>Pour rajouter les clés de Registre Performance à l'aide de l'Éditeur du Registre  
  
1.  Ouvrez l'Éditeur du Registre :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**.  
  
    2.  Dans la boîte de dialogue **exécuter** , dans la zone **ouvrir** , `regedit`tapez.  
  
2.  Dans l'Éditeur du Registre, sélectionnez la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
3.  Cliquez avec le bouton droit sur le nœud **Performance** , pointez sur **Nouveau**, puis cliquez sur **Valeur de chaînes multiples**.  
  
4.  Tapez `Counter Names` et appuyez sur Entrée.  
  
5.  Répétez l’opération pour ajouter la clé de Registre `Counter Types` dans ce nœud.  
  
6.  Accédez à la clé de Registre suivante : `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance`  
  
7.  Cliquez avec le bouton droit sur le nœud **Performance** , pointez sur **Nouveau**, puis cliquez sur **Valeur de chaînes multiples**.  
  
8.  Tapez `Counter Names` et appuyez sur Entrée.  
  
9. Répétez l’opération pour ajouter la clé de Registre `Counter Types` dans ce nœud.  
  
 Après avoir réparé l'instance 64 bits ou rajouté les clés de Registre manuellement, vous pouvez utiliser l'Analyseur de performances pour configurer les objets de performance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à surveiller.  
  
###  <a name="ConfigPropsMissing"></a>Les propriétés de configuration ReportServerExternalURL et PassThroughCookies ne sont pas configurées après une mise à niveau à partir de SQL Server 2005  
 Lorsque vous mettez à niveau à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] vers [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)], les propriétés de configuration `ReportServerExternalURL` et `PassThroughCookies` ne sont pas configurées par le processus de mise à niveau. `ReportServerExternalURL`est une propriété facultative, et elle doit être définie uniquement si vous utilisez SharePoint 2,0 composants WebPart et que vous souhaitez que les utilisateurs puissent récupérer un rapport et l’ouvrir dans une nouvelle fenêtre de navigateur. Pour plus d’informations `ReportServerExternalURL`sur, consultez [URL dans les fichiers de Configuration &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md). `PassThroughCookies`est requis uniquement lors de l’utilisation de la méthode d’authentification personnalisée. Pour plus d’informations `PassThroughCookies`sur, consultez [configurer gestionnaire de rapports pour passer des cookies d’authentification personnalisée](../security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
> [!NOTE]  
>  Lorsque vous utilisez l'authentification personnalisée, il est recommandé de migrer votre installation plutôt que d'effectuer une mise à niveau. Pour plus d’informations sur la migration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Migrer une installation Reporting Services &#40;mode natif&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
 Par défaut, ces propriétés n'existent pas dans la configuration de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] . Si vous avez configuré ces propriétés dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et que vous avez toujours besoin des fonctionnalités qu'elles offrent, vous devez les ajouter manuellement au fichier **RSReportServer.config** après la mise à niveau. Pour plus d’informations, consultez [Modifier un fichier de configuration &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
###  <a name="Default2005InstallBreaks2008"></a>L’installation échoue pour une instance par défaut de SQL Server 2005 Reporting Services sur un ordinateur qui exécute SQL Server services 2012 Reporting  
 Si vous tentez d’installer une instance par [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] défaut de sur un ordinateur qui exécute déjà une [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , l’installation de l’instance de échouera avec le message d’erreur suivant :  
  
 « Une instance portant le même nom est déjà installée sur un ou plusieurs nœuds du cluster. Pour poursuivre l'installation de SQL Server, fournissez un nom d'instance unique. »  
  
 Ce problème se produit indépendamment du fait que l'instance de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] soit une instance par défaut ou nommée, et indépendamment du fait qu'une instance de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] portant ce nom soit déjà présente ou non sur l'ordinateur.  
  
 Pour contourner ce problème, choisissez l'une des méthodes suivantes :  
  
-   Si vous devez exécuter [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en tant qu’instance par défaut sur l’ordinateur, vous devez [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installer l’instance [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] avant l’instance de.  
  
-   Si l' [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance n’a pas besoin d’être une instance par défaut, vous pouvez [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installer l’instance en tant qu’instance nommée après [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] l’installation de l’instance.  
  
###  <a name="WindowsAuthBreaksAfterUpgrade"></a>401-erreur non autorisée lors de l’utilisation de l’authentification Windows après une mise à niveau de SQL Server 2005 vers SQL Server 2012  
 Si vous effectuez une [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mise [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]à niveau de vers et que vous utilisez l’authentification NTLM avec un compte intégré pour le compte de service Report Server, vous pouvez rencontrer une erreur 401 non autorisée lorsque vous accédez au serveur de rapports ou gestionnaire de rapports après la mise à niveau.  
  
 Cette erreur se produit à cause d'une modification dans la configuration par défaut de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] pour l'authentification Windows. Negotiate est configuré lorsque le compte de service Report Server est Service réseau ou Système local. NTLM est configuré lorsque le compte de service Report Server n'est pas l'un de ces comptes intégrés. Pour résoudre ce problème après la mise à niveau, vous pouvez modifier le fichier RSReportServer.config et attribuer à `AuthenticationType` la valeur `RSWindowsNTLM`. Pour plus d’informations, consultez [Configure Windows Authentication on the Report Server](../security/configure-windows-authentication-on-the-report-server.md).  
  
###  <a name="Uninstall32BitBreaks64Bit"></a>La désinstallation d’une instance 32 bits de SQL Server 2012 Reporting Services dans un déploiement côte à côte avec une instance de 64 bits interrompt l’instance de 64 bits  
 Lorsque vous installez une instance 32 bits et une instance 64 bits de [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] côte à côte sur un ordinateur, puis désinstallez l’instance 32 bits, quatre clés de Registre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont supprimées. Cela arrête l'instance 64 bits de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Les clés de Registre [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui sont supprimées lorsque vous désinstallez l’instance 32 bits sont les suivantes :  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Names` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Web Service\Performance:Counter Types` `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSRS 2011 Windows Service\Performance:Counter Types`  
  
 Pour résoudre ce problème, vous pouvez réparer l'instance 64 bits. Bien qu'il soit recommandé d'utiliser la réparation, vous pouvez manuellement rajouter les clés de Registre à l'aide de l'Éditeur du Registre.  
  
> [!CAUTION]  
>  Une modification incorrecte du Registre peut sérieusement endommager votre système. Avant d'apporter des modifications au Registre, il convient de sauvegarder les données importantes qui se trouvent sur l'ordinateur.  
  
##  <a name="bkmk_additional"></a>Ressources supplémentaires  
 Vous trouverez ci-dessous des ressources complémentaires pour vous aider à résoudre les problèmes :  
  
-   Wiki TechNet : rubriques de dépannage [Dépanner SQL Server Reporting Services (SSRS) en mode intégré SharePoint](https://social.technet.microsoft.com/wiki/contents/articles/troubleshoot-sql-server-reporting-services-ssrs-in-sharepoint-integrated-mode.aspx)  
  
-   [Forum : SQL Server Reporting Services](https://social.msdn.microsoft.com/Forums/sqlreportingservices/threads)  
  
