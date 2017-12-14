---
title: "Installer SQL Server à partir de l’invite de commandes | Microsoft Docs"
ms.custom: 
ms.date: 09/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: server-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing SQL Server, command prompt
- installation scripts [SQL Server]
- maintenance scripts [SQL Server]
- REMOVENODE property
- components [SQL Server], removing
- command prompt [SQL Server], SQL Server installations
- ASACCOUNT parameter
- failover clustering [SQL Server], installing
- master database [SQL Server], rebuilding
- SQLCOLLATION parameter
- clusters [SQL Server], installing
- unattended installations [SQL Server]
- modifying collations
- AGTPASSWORD parameter
- USESYSDB parameter
- RSPASSWORD parameter
- AUTOSTART parameter
- ASPASSWORD parameter
- stand-alone installations [SQL Server]
- SAMPLEDATABASESERVER parameter
- adding components
- SAPWD parameter
- scripts [SQL Server], uninstallations
- remote installations [SQL Server]
- components [SQL Server], installing
- TARGETCOMPUTER parameter
- REMOVENODE parameter
- REINSTALLMODE parameter
- scripts [SQL Server], maintenance
- rebuilding registry
- SQLPASSWORD parameter
- rebuilding databases
- IP property
- PIDKEY parameter
- RSCONFIGURATION parameter
- ADDLOCAL parameter
- Setup [SQL Server], command prompt
- REBUILDDATABASE parameter
- SECURITYMODE parameter
- REMOVE property
- DISABLENETWORKPROTOCOLS parameter
- INSTALLDATADIR parameter
- REMOVE parameter
- removing components
- SQLACCOUNT parameter
- parameters [SQL Server], SQL Server installations
- UPGRADE parameter
- shortcuts [SQL Server]
- updating components
- removing SQL Server
- clustered instance of SQL Server
- INSTALLSQLDATADIR parameter
- RSACCOUNT parameter
- ADMINPASSWORD parameter
- GROUP property
- ERRORREPORTING property
- uninstallation scripts [SQL Server]
- AGTACCOUNT parameter
- SAVESYSDB parameter
- INSTALLVS parameter
- INSTANCENAME parameter
- scripts [SQL Server], installations
- rebuilding database, master
- uninstalling SQL Server
- ASCOLLATION parameter
- .ini files
- ADDNODE parameter
- command line installations [SQL Server]
- VS parameter
- INSTALLASDATADIR parameter
- INSTALLSQLDIR parameter
- nodes [Faillover Clustering], command prompt
- INSTALLSQLSHAREDDIR parameter
ms.assetid: df40c888-691c-4962-a420-78a57852364d
caps.latest.revision: "255"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: cf7f4a160fe33cad667f1b469ee6178835d0c384
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="install-sql-server-from-the-command-prompt"></a>Installer SQL Server à partir de l'invite de commandes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Avant d’exécuter le programme d’installation de SQL Server, consultez [Planification d’une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md).  
  
 L’installation d’une nouvelle instance de SQL Server à partir de l’invite de commandes vous permet de spécifier les composants à installer et la façon dont ils doivent être configurés. Vous pouvez également spécifier une interaction en mode silencieux, de base ou complète avec l'interface utilisateur du programme d'installation.  
  
> **REMARQUE :** Quand vous effectuez l’installation à partir de l’invite de commandes, SQL Server prend en charge le mode silencieux complet à l’aide du paramètre /Q ou le mode silencieux simple avec le paramètre /QS. Le commutateur /QS affiche seulement la progression ; il n'accepte pas d'entrée et n'affiche aucun message d'erreur. Le paramètre /QS est pris en charge uniquement lorsque /Action=install est spécifié.  
  
 Indépendamment de la méthode d'installation, vous êtes invité à confirmer l'acceptation des termes de la licence de logiciel en tant que personne physique ou pour le compte d'une entité, sauf si votre utilisation du logiciel est régie par un accord distinct, tel qu'un accord de concession de licence en volume de Microsoft ou un accord tiers avec un éditeur de logiciels ou un fabricant OEM.  
  
 Les termes du contrat de licence sont affichés afin que vous puissiez les consulter et les accepter dans l'interface utilisateur du programme d'installation. Les installations sans assistance (à l'aide du paramètre /Q ou /QS) doivent inclure le paramètre /IACCEPTSQLSERVERLICENSETERMS. Vous pouvez consulter les termes du contrat de licence séparément sur la page [Termes du contrat de licence logiciel Microsoft](http://go.microsoft.com/fwlink/?LinkId=148209).  
  
> **REMARQUE :** Selon la façon dont vous avez reçu le logiciel (par exemple, par le biais du programme de licence en volume Microsoft), votre utilisation du logiciel peut être soumise à des termes et conditions supplémentaires.  
  
 L'installation à partir de l'invite de commandes est prise en charge dans les scénarios suivants :  
  
-   Installation, mise à niveau ou suppression d’une instance et des composants partagés de SQL Server sur un ordinateur local à l’aide de la syntaxe et des paramètres spécifiés à l’invite de commandes.  
  
-   Installation, mise à niveau ou suppression d'une instance de cluster de basculement.  
  
-   Mise à niveau d’une édition de SQL Server vers une autre édition de SQL Server.  
  
-   Installation d’une instance de SQL Server sur un ordinateur local à l’aide de la syntaxe et des paramètres spécifiés dans un fichier de configuration. Vous pouvez utiliser cette méthode pour copier une configuration d'installation sur plusieurs ordinateurs ou pour installer plusieurs nœuds d'une installation de cluster de basculement.  
  
 Quand vous installez SQL Server à partir de l’invite de commandes, spécifiez les paramètres de votre installation à l’invite de commandes dans le cadre de votre syntaxe d’installation.  
  
> **REMARQUE :** Pour des installations locales, vous devez exécuter le programme d’installation comme administrateur. Si vous installez SQL Server à partir d'un partage distant, vous devez utiliser un compte de domaine qui dispose des autorisations de lecture et d'exécution sur le partage distant. Pour les installations de cluster de basculement, vous devez être un administrateur local autorisé à vous connecter en tant que service et à agir dans le cadre du système d'exploitation sur tous les nœuds du cluster de basculement.  
  
##  <a name="ProperUse"></a> Utilisation exacte des paramètres du programme d’installation  
 Utilisez les instructions suivantes pour développer des commandes d'installation ayant la syntaxe adéquate :  
  
-   /PARAMETER  
  
-   /PARAMETER=true/false  
  
-   /PARAMETER=1/0 pour les types booléens  
  
-   /PARAMETER="value" pour tous les paramètres à valeur unique. L'utilisation de guillemets doubles est recommandée ; toutefois, elle devient obligatoire si la valeur contient un espace  
  
-   /PARAMETER="value1" "value2" "value3" pour tous les paramètres à valeurs multiples. L'utilisation de guillemets doubles est recommandée ; toutefois, elle devient obligatoire si la valeur contient un espace  
  
 **Exceptions :**  
  
-   /FEATURES, qui est un paramètre à valeurs multiples mais dont le format est /FEATURES=AS,RS,IS sans espace et délimité par des virgules  
  
 **Exemples :**  
  
-   /INSTANCEDIR=c:\Path est pris en charge.  
  
-   /INSTANCEDIR=”c:\Path” est pris en charge.  
  
> [!NOTE]  
>  -   Quand vous installez SQL Server, si vous spécifiez le même chemin de répertoire pour INSTANCEDIR et SQLUSERDBDIR, SQL Server Agent et la recherche en texte intégral ne démarrent pas en raison d’autorisations manquantes.  
>   
>      Les valeurs relationnelles de serveur prennent en charge les formats de fin supplémentaires de barre oblique inverse (barre oblique inverse ou deux barres obliques inverses) pour le chemin d'accès.  
> -   /PID, la valeur de ce paramètre doit être placée entre des guillemets doubles.  
  
## <a name="sql-server-parameters"></a>Paramètres du serveur SQL Server  
 Les sections suivantes fournissent des paramètres qui permettent de développer des scripts d'installation en ligne de commande pour des scénarios d'installation, de mise à jour et de réparation.  
  
 Les paramètres répertoriés pour un composant SQL Server sont spécifiques de ce composant. Les paramètres de SQL Server Agent et SQL Server Browser sont applicables quand vous installez le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
-   [Paramètres d’installation](#Install)  
  
-   [Paramètres SysPrep](#SysPrep)  
  
-   [Paramètres de mise à niveau](#Upgrade)  
  
-   [Paramètres de réparation](#Repair)  
  
-   [Paramètres de reconstruction des bases de données système](#Rebuild)  
  
-   [Paramètres de désinstallation](#Uninstall)  
  
-   [Paramètres de cluster de basculement](#ClusterInstall)  
  
-   [Paramètres des comptes de service](#Accounts)  
  
-   [Paramètres de fonctionnalités](#Feature)  
  
-   [Paramètres de rôle](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#RoleParameters)  
  
-   [Contrôle du comportement du basculement à l’aide du paramètre /FAILOVERCLUSTERROLLOWNERSHIP](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#RollOwnership)  
  
-   [Configuration de l’ID d’instance ou d’InstanceID](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#InstanceID) 
  
##  <a name="Install"></a> Paramètres d’installation  
 Utilisez les paramètres répertoriés dans le tableau ci-dessous pour développer des scripts d'installation en ligne de commande.  
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail d'installation.<br /><br /> Valeurs prises en charge : **Install**.|  
|Contrôle d'installation SQL Server|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance.**|Obligatoire pour l'acceptation des termes du contrat de licence.|  
|Contrôle d'installation SQL Server|/IACCEPTROPENLICENSETERMS <br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance qui incluent R Services (dans la base de données) ou Microsoft R Server.**|Obligatoire pour l'acceptation des termes du contrat de licence.| 
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/UpdateEnabled<br /><br /> **Facultatif**|Spécifiez si le programme d'installation de SQL Server doit rechercher et inclure les mises à jour du produit. Les valeurs valides sont True et False ou 1 et 0. Par défaut, le programme d'installation de SQL Server inclut les mises à jour trouvées.|  
|Contrôle d'installation SQL Server|/UpdateSource<br /><br /> **Facultatif**|Spécifiez l'emplacement où le programme d'installation de SQL Server va récupérer les mises à jour du produit. Les valeurs valides sont « MU » pour rechercher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, un chemin au dossier valide, un chemin relatif tel que .\MyUpdates ou un partage UNC. Par défaut, le programme d’installation de SQL Server lance une recherche dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update ou un service Windows Update par le biais de Windows Server Update Services.|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/ERRORREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/> Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’erreurs pour SQL Server.<br /><br /> Pour plus d'informations, consultez [Déclaration de confidentialité du service de rapport d'erreurs Microsoft](http://go.microsoft.com/fwlink/?LinkID=72173).<br /><br /> Valeurs prises en charge :<br /><br /> 0 = désactivé<br /><br /> 1 = activé|  
|Contrôle d'installation SQL Server|/FEATURES<br /><br /> - Ou -<br /><br /> /ROLE<br /><br /> **Obligatoire**|Spécifie les composants à installer.<br /><br /> Choisissez **/FEATURES** pour spécifier des composants SQL Server individuels à installer. Pour plus d'informations, consultez [Paramètres de fonctionnalités](#Feature) ci-dessous.<br /><br /> Choisissez **/ROLE** pour spécifier un rôle d’installation. Les rôles d'installation permettent d'installer SQL Server selon une configuration prédéterminée.|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres d'installation.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé est redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTALLSHAREDDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés 64 bits.<br /><br /> Par défaut : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server<br /><br /> Ne peut pas être défini avec la valeur %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server|  
|Contrôle d'installation SQL Server|/INSTALLSHAREDWOWDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés 32 bits. Pris en charge uniquement sur un système 64 bits.<br /><br /> Par défaut : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server<br /><br /> Ne peut pas être défini avec la valeur %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server|  
|Contrôle d'installation SQL Server|/ INSTANCEDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants spécifiques à l'instance.|  
|Contrôle d'installation SQL Server|/INSTANCEID<br /><br /> **Facultatif**|Spécifie une valeur différente de la valeur par défaut pour [InstanceID](#InstanceID).|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du compte de service du moteur.|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|PolyBase|/PBPORTRANGE<br /><br /> **Facultatif**|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **Facultatif**|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. Valeurs prises en charge : **True**, **False**|  
|Contrôle d'installation SQL Server|/PID<br /><br /> **Facultatif**|Spécifie la clé de produit pour l’édition de SQL Server. Si ce paramètre n'est pas spécifié, Evaluation est utilisée.|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/QS<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute et affiche sa progression via l'interface utilisateur ; toutefois, aucune entrée n'est acceptée et aucun message d'erreur n'est affiché.|  
|Contrôle d'installation SQL Server|/UIMODE<br /><br /> **Facultatif**|Spécifie s'il faut présenter uniquement le nombre minimal de boîtes de dialogue pendant l'installation.<br /><br /> **/UIMode** ne peut être utilisé qu'avec les paramètres **/ACTION=INSTALL** et **UPGRADE** . Valeurs prises en charge :<br /><br /> **/UIMODE=Normal** est la valeur par défaut des éditions non-Express et présente toutes les boîtes de dialogue d'installation des fonctionnalités sélectionnées.<br /><br /> **/UIMODE=AutoAdvance** est la valeur par défaut des éditions Express et ignore les boîtes de dialogue non essentielles.<br /><br /> <br /><br /> Remarque : en cas de combinaison avec d’autres paramètres, **UIMODE** est remplacé. Par exemple, quand **/UIMODE=AutoAdvance** et **/ADDCURRENTUSERASSQLADMIN=FALSE** sont fournis tous les deux, la boîte de dialogue d’approvisionnement n’est pas remplie automatiquement pour l’utilisateur actuel.<br /><br /> Le paramètre **UIMode** ne peut pas être utilisé avec les paramètres **/Q** ou **/QS** .|  
|Contrôle d'installation SQL Server|/SQMREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’utilisation des fonctionnalités pour SQL Server.<br /><br />Valeurs prises en charge :<br /><br /> 0 = désactivé<br /><br /> 1 = activé|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
|SQL Server Agent|/AGTSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour le service SQL Server Agent.|  
|SQL Server Agent|/AGTSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de service SQL Server Agent.|  
|SQL Server Agent|/AGTSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service SQL Server Agent.<br /><br /> Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASBACKUPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de sauvegarde [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCOLLATION<br /><br /> **Facultatif**|Spécifie le paramètre de classement pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> Valeur par défaut : **Latin1_General_CI_AS**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCONFIGDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de configuration [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASDATADIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers journaux [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Log.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Log.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSERVERMODE<br /><br /> **Facultatif**|Spécifie le mode serveur de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Les valeurs valides sont MULTIDIMENSIONAL, POWERPIVOT ou TABULAR. La casse est prise en compte pour**ASSERVERMODE** . Toutes les valeurs doivent être exprimées en majuscules. Pour plus d’informations sur les valeurs valides, consultez [Installer Analysis Services](../../analysis-services/instances/install-windows/install-analysis-services.md).|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSYSADMINACCOUNTS<br /><br /> **Obligatoire**|Spécifie les informations d'identification d'administrateur pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASTEMPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers temporaires [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server \\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Temp.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Temp.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASPROVIDERMSOLAP<br /><br /> **Facultatif**|Spécifie si le fournisseur MSOLAP peut s'exécuter in-process.<br /><br /> Valeur par défaut : 1=activé|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/FARMACCOUNT<br /><br /> **Obligatoire pour SPI_AS_NewFarm**|Spécifie un compte d'utilisateur de domaine pour l'exécution des services de l'Administration centrale de SharePoint et des autres services essentiels dans une batterie de serveurs.<br /><br /> Ce paramètre est utilisé uniquement pour les instances d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installées par le biais de /ROLE = SPI_AS_NEWFARM.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/FARMPASSWORD<br /><br /> **Obligatoire pour SPI_AS_NewFarm**|Spécifie un mot de passe pour le compte de batterie de serveurs.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/PASSPHRASE<br /><br /> **Obligatoire pour SPI_AS_NewFarm**|Spécifie une phrase secrète qui permet d'ajouter des serveurs d'applications ou des serveurs Web frontaux supplémentaires à une batterie de serveurs SharePoint.<br /><br /> Ce paramètre est utilisé uniquement pour les instances d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installées par le biais de /ROLE = SPI_AS_NEWFARM.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/FARMADMINIPORT<br /><br /> **Obligatoire pour SPI_AS_NewFarm**|Spécifie un port de connexion à l'application Web de l'Administration centrale de SharePoint.<br /><br /> Ce paramètre est utilisé uniquement pour les instances d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] installées par le biais de /ROLE = SPI_AS_NEWFARM.|  
|SQL Server Browser|/BROWSERSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service SQL Server Browser. Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/ENABLERANU<br /><br /> **Facultatif**|Active les informations d'identification Exécuter en tant que pour les installations [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] .|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/INSTALLSQLDATADIR<br /><br /> **Facultatif**|Spécifie le répertoire de données pour les fichiers de données SQL Server. Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **Obligatoire quand /SECURITYMODE=SQL**|Spécifie le mot de passe du compte SQL Serversa.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SECURITYMODE<br /><br /> **Facultatif**|Spécifie le mode de sécurité pour SQL Server.<br /><br /> Si ce paramètre n'est pas fourni, le mode d'authentification Windows uniquement est pris en charge.<br /><br /> Valeur prise en charge : **SQL**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLBACKUPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de sauvegarde.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Backup|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **Facultatif**|Spécifie les paramètres de classement pour SQL Server.<br /><br /> La valeur par défaut est basée sur les paramètres régionaux de votre système d'exploitation Windows. Pour plus d'informations, consultez [Paramètres de classement du programme d'installation](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/ADDCURRENTUSERASSQLADMIN<br /><br /> **Facultatif**|Ajoute l’utilisateur actuel au rôle serveur fixe**sysadmin** de SQL Server. Le paramètre /ADDCURRENTUSERASSQLADMIN peut être utilisé lors de l'installation d'éditions Express ou lors de l'utilisation de /Role=ALLFeatures_WithDefaults. Pour plus d’informations, consultez /ROLE ci-dessous.<br /><br /> L'utilisation du paramètre /ADDCURRENTUSERASSQLADMIN est facultative, mais /ADDCURRENTUSERASSQLADMIN ou /SQLSYSADMINACCOUNTS est obligatoire. Valeurs par défaut :<br /><br /> **True** pour les éditions de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> **False** pour toutes les autres éditions|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage du service SQL Server.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe pour SQLSVCACCOUNT.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) du service SQL Server. Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **Obligatoire**|Utilisez ce paramètre pour configurer des connexions en tant que membres du rôle sysadmin.<br /><br /> Pour les éditions SQL Server autres que [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], /SQLSYSADMINACCOUNTS est obligatoire. Pour les éditions de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], l'utilisation du paramètre /SQLSYSADMINACCOUNTS est facultative, mais /SQLSYSADMINACCOUNTS ou /ADDCURRENTUSERASSQLADMIN est obligatoire.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **Facultatif**|Spécifie les répertoires des fichiers de données tempdb. Lorsque vous spécifiez plusieurs répertoires, utilisez l’espace comme séparateur. Si plusieurs répertoires sont spécifiés, les fichiers de données tempdb sont répartis entre les répertoires selon le principe du tourniquet (round robin).<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire du fichier journal tempdb.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **Facultatif**|Spécifie le nombre de fichiers de données tempdb que le programme d’installation doit ajouter. Cette valeur peut être augmentée jusqu’au nombre de cœurs. Valeur par défaut :<br /><br /> 1 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 ou le nombre de cœurs, la valeur la plus petite étant applicable pour toutes les autres éditions<br /><br /> **\*\* Important \*\*** Le fichier de base de données principale pour tempdb est toujours tempdb.mdf. Les fichiers tempdb supplémentaires sont nommés tempdb_mssql_#.ndf, où # représente un nombre unique pour chaque fichier de base de données tempdb supplémentaire créé pendant l’installation. L’objectif de cette convention d’affectation de noms est de les rendre uniques. La désinstallation d’une instance de SQL Server supprime les fichiers nommés tempdb_mssql_#.ndf d’après la convention d’affectation de noms. N’utilisez pas la convention d’affectation de noms tempdb_mssql_*.ndf pour les fichiers de base de données utilisateur.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier de données tempdb.<br/><br/>Par défaut = 4 Mo pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 8 Mo pour toutes les autres éditions.<br/><br/>Min = (4 ou 8 Mo).<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)])|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **Facultatif**|Spécifie l’incrément de croissance de chaque fichier de données tempdb en Mo. La valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé. Le programme d’installation autorise la taille maximale de 1 024 Mo.<br /><br /> Valeur par défaut : 64. Plage autorisée : Min = 0, Max = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier journal tempdb.<br/><br/>Par défaut = 4 Mo pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 8 Mo pour toutes les autres éditions.<br/><br/>Min = (4 ou 8 Mo).<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)])|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **Facultatif**|Spécifie l’incrément de croissance de chaque fichier de données tempdb en Mo. La valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé. La taille maximale autorisée par le programme d’installation s’élève à 1 024.<br /><br /> Valeur par défaut : 64. Plage autorisée : Min = 0, Max = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers de données pour les bases de données utilisateur.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCINSTANTFILEINIT<br /><br /> **Facultatif**|Active l’initialisation instantanée de fichiers pour le compte de service SQL Server. Pour connaître les considérations relatives à la sécurité et aux performances, consultez [Initialisation instantanée des fichiers de base de données](../../relational-databases/databases/database-instant-file-initialization.md).<br /><br /> Valeur par défaut : « False »<br /><br /> Valeur facultative : « True »|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers journaux pour les bases de données utilisateur.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|FILESTREAM|/FILESTREAMLEVEL<br /><br /> **Facultatif**|Spécifie le niveau d'accès pour la fonctionnalité FILESTREAM. Valeurs prises en charge :<br /><br /> 0 = désactiver la prise en charge de FILESTREAM pour cette instance. (Valeur par défaut)<br /><br /> 1 = activer FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] .<br /><br /> 2 = activer FILESTREAM pour [!INCLUDE[tsql](../../includes/tsql-md.md)] et l'accès en continu des E/S de fichier. (Non valide pour les scénarios de clusters)<br /><br /> 3 = permettre aux clients distants d'avoir un accès en continu aux données FILESTREAM.|  
|FILESTREAM|/FILESTREAMSHARENAME<br /><br /> **Facultatif**<br /><br /> **Obligatoire quand FILESTREAMLEVEL est supérieur à 1.**|Spécifie le nom du partage Windows dans lequel les données FILESTREAM doivent être stockées.|  
|Texte intégral SQL Server|/FTSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service du lanceur de filtre de texte intégral.<br /><br /> Ce paramètre est ignoré dans [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]. ServiceSID est utilisé pour aider à sécuriser la communication entre SQL Server et le démon de filtre de texte intégral. Si les valeurs ne sont pas fournies, le service du lanceur de filtre de texte intégral est désactivé. Vous devez utiliser le Gestionnaire de contrôle des services SQL Server pour modifier le compte de service et activer les fonctionnalités de texte intégral.<br /><br /> Valeur par défaut : Compte de service local|  
|Texte intégral SQL Server|/FTSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du service du lanceur de filtre de texte intégral.<br /><br /> Ce paramètre est ignoré dans [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)].|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].<br /><br /> Valeur par défaut : NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|Configuration du réseau SQL Server|/NPENABLED<br /><br /> **Facultatif**|Spécifie l’état du protocole des canaux nommés pour le service SQL Server. Valeurs prises en charge :<br /><br /> 0 = désactiver le protocole des canaux nommés<br /><br /> 1 = activer le protocole des canaux nommés|  
|Configuration du réseau SQL Server|/TCPENABLED<br /><br /> **Facultatif**|Spécifie l’état du protocole TCP pour le service SQL Server. Valeurs prises en charge :<br /><br /> 0 = désactiver le protocole TCP<br /><br /> 1 = activer le protocole TCP|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **Facultatif**|Spécifie le mode d'installation pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Valeurs prises en charge :<br /><br /> **SharePointFilesOnlyMode**<br /><br /> **DefaultNativeMode**<br /><br /> **FilesOnlyMode**<br /><br /> <br /><br /> Remarque : Si l’installation inclut le[!INCLUDE[ssDE](../../includes/ssde-md.md)]SQL Server, la valeur par défaut de RSINSTALLMODE est DefaultNativeMode.<br /><br /> Si l’installation n’inclut pas le[!INCLUDE[ssDE](../../includes/ssde-md.md)]SQL Server, la valeur par défaut de RSINSTALLMODE est FilesOnlyMode.<br /><br /> Si vous choisissez DefaultNativeMode, mais que l’installation n’inclut pas le[!INCLUDE[ssDE](../../includes/ssde-md.md)]SQL Server, le programme d’installation remplace automatiquement la valeur de RSINSTALLMODE par FilesOnlyMode.|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de démarrage pour le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|R Services (dans la base de données)|MRCACHEDIRECTORY|Utilisez ce paramètre pour spécifier le répertoire de Cache pour les composants Microsoft R Open et Microsoft R Server, comme décrit dans [cette section](https://msdn.microsoft.com/library/mt695942.aspx). Ce paramètre est généralement utilisé pendant l’installation de SQL Server R Services à partir de la ligne de commande sur un ordinateur sans accès à Internet.|  
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour installer une nouvelle instance autonome avec les composants [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], Réplication et Recherche en texte intégral et activer l’initialisation instantanée de fichiers pour [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. 
  
```  
  
Setup.exe /q /ACTION=Install /FEATURES=SQL /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /SQLSVCINSTANTFILEINIT="True" /IACCEPTSQLSERVERLICENSETERMS  
  
```  
  
##  <a name="SysPrep"></a> Paramètres SysPrep  
 Pour plus d’informations sur SQL Server SysPrep, consultez  
  
 [Installer SQL Server 2016 à l’aide de SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md). 
  
#### <a name="prepare-image-parameters"></a>Paramètres de préparation d'image  
 Utilisez les paramètres du tableau suivant pour développer des scripts de ligne de commande afin de préparer une instance de SQL Server sans la configurer. 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail d'installation.<br /><br /> Valeurs prises en charge : **PrepareImage**|  
|Contrôle d’installation de SQL Server|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance.**|Obligatoire pour l'acceptation des termes du contrat de licence.|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/UpdateEnabled<br /><br /> **Facultatif**|Spécifiez si le programme d'installation de SQL Server doit rechercher et inclure les mises à jour du produit. Les valeurs valides sont True et False ou 1 et 0. Par défaut, le programme d'installation de SQL Server inclut les mises à jour trouvées.|  
|Contrôle d'installation SQL Server|/UpdateSource<br /><br /> **Facultatif**|Spécifiez l'emplacement où le programme d'installation de SQL Server va récupérer les mises à jour du produit. Les valeurs valides sont « MU » pour rechercher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, un chemin au dossier valide, un chemin relatif tel que .\MyUpdates ou un partage UNC. Par défaut, le programme d’installation de SQL Server lance une recherche dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update ou un service Windows Update par le biais de Windows Server Update Services.|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/FEATURES<br /><br /> **Obligatoire**|Spécifie les [composants](#Feature) à installer.<br /><br /> Les valeurs prises en charge sont SQLEngine, Replication, FullText, DQ, AS, AS_SPI, RS, RS_SHP, RS_SHPWFE, DQC, Conn, IS, BC, SDK, DREPLAY_CTLR, DREPLAY_CLT, SNAC_SDK, SQLODBC, SQLODBC_SDK, LocalDB, MDS, POLYBASE|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres d'installation.|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé est redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTALLSHAREDDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés 64 bits.<br /><br /> Par défaut : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server<br /><br /> Ne peut pas être défini avec la valeur %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server|  
|Contrôle d'installation SQL Server|/ INSTANCEDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants spécifiques à l'instance.|  
|Contrôle d'installation SQL Server|/INSTANCEID<br /><br /> Avant la mise à jour cumulative 2 de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 (janvier 2013) **Requis**<br /><br /> À partir de la mise à jour cumulative 2 de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 **Requis** pour les fonctionnalités de l'instance.|Spécifie un InstanceID pour l'instance en cours de préparation.|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du compte de service du moteur.|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|PolyBase|/PBPORTRANGE<br /><br /> **Facultatif**|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **Facultatif**|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. Valeurs prises en charge : **True**, **False**|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/QS<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute et affiche sa progression via l'interface utilisateur ; toutefois, aucune entrée n'est acceptée et aucun message d'erreur n'est affiché.|  
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour préparer une instance nouvelle et autonome avec les composants [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], Réplication et Recherche en texte intégral et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. 
  
```  
Setup.exe /q /ACTION=PrepareImage /FEATURES=SQL,RS /InstanceID =<MYINST> /IACCEPTSQLSERVERLICENSETERMS  
```  
  
#### <a name="complete-image-parameters"></a>Paramètres de finalisation d'image  
 Utilisez les paramètres du tableau suivant pour développer des scripts de ligne de commande afin de terminer et de configurer une instance préparée de SQL Server. 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail d'installation.<br /><br /> Valeurs prises en charge : **CompleteImage**|  
|Contrôle d'installation SQL Server|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance.**|Obligatoire pour l'acceptation des termes du contrat de licence.|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/ERRORREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’erreurs pour SQL Server.<br /><br /> Pour plus d'informations, consultez [Déclaration de confidentialité du service de rapport d'erreurs Microsoft](http://go.microsoft.com/fwlink/?LinkID=72173). Valeurs prises en charge :<br /><br /> 1 = activé<br /><br /> 0 = désactivé|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres d'installation.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé est redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTANCEID<br /><br /> Avant la mise à jour cumulative 2 de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 (janvier 2013) **Requis**<br /><br /> À partir de la mise à jour cumulative 2 de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 **Facultatif**|Utilisez l'ID d'instance spécifié pendant l'étape de préparation d'image.<br /><br /> Valeurs prises en charge : InstanceID d’une instance préparée.|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> Avant la mise à jour cumulative 2 de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 (janvier 2013) **Requis**<br /><br /> À partir de la mise à jour cumulative 2 de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 **Facultatif**|Spécifie le nom d’une instance SQL Server pour l’instance en cours de finalisation.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du compte de service du moteur.|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|PolyBase|/PBPORTRANGE<br /><br /> **Facultatif**|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **Facultatif**|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. Valeurs prises en charge : **True**, **False**|  
|Contrôle d'installation SQL Server|/PID<br /><br /> **Facultatif**|Spécifie la clé de produit pour l’édition de SQL Server. Si ce paramètre n'est pas spécifié, Evaluation est utilisée.<br /><br /> Remarque : Si vous installez SQL Server Express, SQL Server Express with Tools ou SQL Server Express with Advanced Services, le PID est prédéfini.|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/QS<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute et affiche sa progression via l'interface utilisateur ; toutefois, aucune entrée n'est acceptée et aucun message d'erreur n'est affiché.|  
|Contrôle d'installation SQL Server|/SQMREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’utilisation des fonctionnalités pour SQL Server.<br /><br />Valeurs prises en charge :<br /><br /> 0 = désactivé<br /><br /> 1 = activé|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
|SQL Server Agent|/AGTSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour le service SQL Server Agent.|  
|SQL Server Agent|/AGTSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de service SQL Server Agent.|  
|SQL Server Agent|/AGTSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service SQL Server Agent. Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|SQL Server Browser|/BROWSERSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service SQL Server Browser. Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/ENABLERANU<br /><br /> **Facultatif**|Active les informations d’identification Exécuter en tant que pour les installations de SQL Server Express.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/INSTALLSQLDATADIR<br /><br /> **Facultatif**|Spécifie le répertoire de données pour les fichiers de données SQL Server. Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **Obligatoire quand /SECURITYMODE=SQL**|Spécifie le mot de passe du compte SQL Serversa.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SECURITYMODE<br /><br /> **Facultatif**|Spécifie le mode de sécurité pour SQL Server.<br /><br /> Si ce paramètre n'est pas fourni, le mode d'authentification Windows uniquement est pris en charge.<br /><br /> Valeur prise en charge : **SQL**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLBACKUPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de sauvegarde.<br /><br /> Valeur par défaut :<br /><br /> \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Backup|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **Facultatif**|Spécifie les paramètres de classement pour SQL Server.<br /><br /> La valeur par défaut est basée sur les paramètres régionaux de votre système d'exploitation Windows. Pour plus d'informations, consultez [Paramètres de classement du programme d'installation](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage du service SQL Server.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe pour SQLSVCACCOUNT.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) du service SQL Server. Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **Obligatoire**|Utilisez ce paramètre pour configurer des connexions en tant que membres du rôle sysadmin.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **Facultatif**|Spécifie les répertoires des fichiers de données tempdb. Lorsque vous spécifiez plusieurs répertoires, utilisez l’espace comme séparateur. Si plusieurs répertoires sont spécifiés, les fichiers de données tempdb sont répartis entre les répertoires selon le principe du tourniquet (round robin).<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire du fichier journal tempdb.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier de données tempdb.<br/><br/>Par défaut = 4 Mo pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 8 Mo pour toutes les autres éditions.<br/><br/>Min = (4 ou 8 Mo).<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)]).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **Facultatif**|Spécifie l’incrément de croissance de chaque fichier de données tempdb en Mo. La valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé. La taille maximale autorisée par le programme d’installation s’élève à 1 024.<br /><br /> Valeur par défaut : 64<br /><br /> Plage autorisée : Min = 0, Max = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **Facultatif**|Spécifie la taille initiale en Mo du fichier journal tempdb. La taille maximale autorisée par le programme d’installation s’élève à 1 024.<br /><br /> Valeur par défaut :<br /><br /> 4 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 pour toutes les autres éditions<br /><br /> Plage autorisée : Min = valeur par défaut (4 ou 8), Max = 1 024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier journal tempdb.<br/><br/>Par défaut = 4 Mo pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 8 Mo pour toutes les autres éditions.<br/><br/>Min = (4 ou 8 Mo).<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)])|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **Facultatif**|Spécifie le nombre de fichiers de données tempdb que le programme d’installation doit ajouter. Cette valeur peut être augmentée jusqu’au nombre de cœurs. Valeur par défaut :<br /><br /> 1 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 ou le nombre de cœurs, la valeur la plus petite étant applicable pour toutes les autres éditions<br /><br /> **\*\* Important \*\*** Le fichier de base de données principale pour tempdb est toujours tempdb.mdf. Les fichiers tempdb supplémentaires sont nommés tempdb_mssql_#.ndf, où # représente un nombre unique pour chaque fichier de base de données tempdb supplémentaire créé pendant l’installation. L’objectif de cette convention d’affectation de noms est de les rendre uniques. La désinstallation d’une instance de SQL Server supprime les fichiers nommés tempdb_mssql_#.ndf d’après la convention d’affectation de noms. N’utilisez pas la convention d’affectation de noms tempdb_mssql_\*.ndf pour les fichiers de base de données utilisateur.<br /><br /> **\*\* Avertissement \*\*** [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]n’est pas pris en charge pour la configuration de ce paramètre. Le programme d’installation installe uniquement 1 fichier de données tempdb.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers de données pour les bases de données utilisateur.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers journaux pour les bases de données utilisateur.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|FILESTREAM|/FILESTREAMLEVEL<br /><br /> **Facultatif**|Spécifie le niveau d'accès pour la fonctionnalité FILESTREAM. Valeurs prises en charge :<br /><br /> 0 = désactiver la prise en charge de FILESTREAM pour cette instance. (Valeur par défaut)<br /><br /> 1 = activer FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] .<br /><br /> 2 = activer FILESTREAM pour [!INCLUDE[tsql](../../includes/tsql-md.md)] et l'accès en continu des E/S de fichier. (Non valide pour les scénarios de clusters)<br /><br /> 3 = permettre aux clients distants d'avoir un accès en continu aux données FILESTREAM.|  
|FILESTREAM|/FILESTREAMSHARENAME<br /><br /> **Facultatif**<br /><br /> **Obligatoire quand FILESTREAMLEVEL est supérieur à 1.**|Spécifie le nom du partage Windows dans lequel les données FILESTREAM doivent être stockées.|  
|Texte intégral SQL Server|/FTSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service du lanceur de filtre de texte intégral.<br /><br /> Ce paramètre est ignoré dans [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]. ServiceSID est utilisé pour aider à sécuriser la communication entre SQL Server et le démon de filtre de texte intégral. Si les valeurs ne sont pas fournies, le service du lanceur de filtre de texte intégral est désactivé. Vous devez utiliser le Gestionnaire de contrôle des services SQL Server pour modifier le compte de service et activer les fonctionnalités de texte intégral.<br /><br /> Valeur par défaut : Compte de service local|  
|Texte intégral SQL Server|/FTSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du service du lanceur de filtre de texte intégral.<br /><br /> Ce paramètre est ignoré dans [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)].|  
|Configuration du réseau SQL Server|/NPENABLED<br /><br /> **Facultatif**|Spécifie l’état du protocole des canaux nommés pour le service SQL Server. Valeurs prises en charge :<br /><br /> 0 = désactiver le protocole des canaux nommés<br /><br /> 1 = activer le protocole des canaux nommés|  
|Configuration du réseau SQL Server|/TCPENABLED<br /><br /> **Facultatif**|Spécifie l’état du protocole TCP pour le service SQL Server. Valeurs prises en charge :<br /><br /> 0 = désactiver le protocole TCP<br /><br /> 1 = activer le protocole TCP|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **Facultatif**|Spécifie le mode d'installation pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de démarrage pour le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour finaliser une instance préparée et autonome qui inclut les composants [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], Réplication et Recherche en texte intégral. 
  
```  
  
setup.exe /q /ACTION=CompleteImage /INSTANCENAME=MYNEWINST /INSTANCEID=<MYINST> /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /IACCEPTSQLSERVERLICENSETERMS  
  
```  
  
##  <a name="Upgrade"></a> Paramètres de mise à niveau  
 Utilisez les paramètres répertoriés dans le tableau ci-dessous pour développer des scripts de mise à niveau en ligne de commande. 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail d'installation. Valeurs prises en charge :<br /><br /> **Upgrade**<br /><br /> **EditionUpgrade**<br /><br /> <br /><br /> La valeur **EditionUpgrade** est utilisée pour mettre à niveau une édition existante de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vers une autre édition. Pour plus d'informations sur les mises à niveau des versions et éditions prises en charge, consultez [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).|  
|Contrôle d'installation SQL Server|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance.**|Obligatoire pour l'acceptation des termes du contrat de licence.|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/*UpdateEnabled*<br /><br /> **Facultatif**|Spécifiez si le programme d'installation de SQL Server doit rechercher et inclure les mises à jour du produit. Les valeurs valides sont True et False ou 1 et 0. Par défaut, le programme d'installation de SQL Server inclut les mises à jour trouvées.|  
|Contrôle d'installation SQL Server|/*UpdateSource*<br /><br /> **Facultatif**|Spécifiez l'emplacement où le programme d'installation de SQL Server va récupérer les mises à jour du produit. Les valeurs valides sont « MU » pour rechercher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, un chemin au dossier valide, un chemin relatif tel que .\MyUpdates ou un partage UNC. Par défaut, le programme d’installation de SQL Server lance une recherche dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update ou un service Windows Update par le biais de Windows Server Update Services.|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/ERRORREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’erreurs pour SQL Server.<br /><br /> Pour plus d'informations, consultez [Déclaration de confidentialité du service de rapport d'erreurs Microsoft](http://go.microsoft.com/fwlink/?LinkID=72173). Valeurs prises en charge :<br /><br /> 1 = activé<br /><br /> 0 = désactivé|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé sera redirigé vers la console.|  
|Contrôle d'installation SQL Server|/ INSTANCEDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés.|  
|Contrôle d'installation SQL Server|/INSTANCEID<br /><br /> **Obligatoire lors de la mise à niveau depuis [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]** ou d'une version ultérieure.<br /><br /> **Facultatif lors de la mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]**|Spécifie une valeur différente de la valeur par défaut pour [InstanceID](#InstanceID).|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|Contrôle d'installation SQL Server|/PID<br /><br /> **Facultatif**|Spécifie la clé de produit pour l’édition de SQL Server. Si ce paramètre n'est pas spécifié, Evaluation est utilisée.|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/UIMODE<br /><br /> **Facultatif**|Spécifie s'il faut présenter uniquement le nombre minimal de boîtes de dialogue pendant l'installation. <br />                **/UIMode** ne peut être utilisé qu'avec les paramètres **/ACTION=INSTALL** et **UPGRADE** . Valeurs prises en charge :<br /><br /> **/UIMODE=Normal** est la valeur par défaut des éditions non-Express et présente toutes les boîtes de dialogue d'installation des fonctionnalités sélectionnées.<br /><br /> **/UIMODE=AutoAdvance** est la valeur par défaut des éditions Express et ignore les boîtes de dialogue non essentielles.<br /><br /> Notez que le paramètre **UIMode** ne peut pas être utilisé avec les paramètres **/Q** ou **/QS** .|  
|Contrôle d'installation SQL Server|/SQMREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’utilisation des fonctionnalités pour SQL Server.<br /><br />Valeurs prises en charge :<br /><br /> 1 = activé<br /><br /> 0 = désactivé|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie si la fenêtre de console est masquée ou fermée.|  
|Service SQL Server Browser|/BROWSERSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service SQL Server Browser. Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|Texte intégral SQL Server|/FTUPGRADEOPTION<br /><br /> **Facultatif**|Spécifie l'option de mise à niveau du catalogue de texte intégral. Valeurs prises en charge :<br /><br /> **REBUILD**<br /><br /> **RESET**<br /><br /> **IMPORT**|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].<br /><br /> Valeur par défaut : NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSUPGRADEDATABASEACCOUNT<br /><br /> **Facultatif**|La propriété est utilisée uniquement lors de la mise à niveau d'un serveur de rapports en mode SharePoint avec la version 2008 R2 ou antérieure. Des opérations de mise à niveau supplémentaires sont effectuées pour les serveurs de rapports qui utilisent l'ancienne architecture du mode SharePoint, modifiée dans SQL Server 2012 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si cette option n'est pas incluse dans l'installation de ligne de commande, le compte de service par défaut de l'ancienne instance de serveur de rapports est utilisé. Si cette propriété est utilisée, fournissez le mot de passe du compte à l'aide de la propriété **/RSUPGRADEPASSWORD** .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSUPGRADEPASSWORD<br /><br /> **Facultatif**|Mot de passe du compte de service Report Server existant.|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/ALLOWUPGRADEFORSSRSSHAREPOINTMODE|Le commutateur est requis pour la mise à niveau d'une installation en mode SharePoint basée sur l'architecture de service partagé SharePoint. Le commutateur n'est pas nécessaire pour mettre à niveau les versions de service non partagé de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour mettre à niveau une instance existante ou un nœud de cluster de basculement existant à partir d’une version précédente de SQL Server,  
  
```  
Setup.exe /q /ACTION=upgrade /INSTANCEID = <INSTANCEID>/INSTANCENAME=MSSQLSERVER /RSUPGRADEDATABASEACCOUNT="<Provide a SQL Server logon account that can connect to the report server during upgrade>" /RSUPGRADEPASSWORD="<Provide a password for the report server upgrade account>" /ISSVCAccount="NT Authority\Network Service" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
##  <a name="Repair"></a> Paramètres de réparation  
 Utilisez les paramètres répertoriés dans le tableau ci-dessous pour développer des scripts de réparation en ligne de commande. 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail de réparation.<br /><br /> Valeurs prises en charge : **Repair**|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/FEATURES<br /><br /> **Obligatoire**|Spécifie les [composants](#Feature) à réparer.|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du compte de service du moteur.|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|PolyBase|/PBPORTRANGE<br /><br /> **Facultatif**|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **Facultatif**|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. Valeurs prises en charge : **True**, **False**|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Réparer une instance et des composants partagés. 
  
```  
Setup.exe /q /ACTION=Repair /INSTANCENAME=<instancename>  
```  
  
##  <a name="Rebuild"></a> Paramètres de reconstruction des bases de données système  
 Utilisez les paramètres répertoriés dans le tableau suivant pour développer des scripts en ligne de commande qui permettent de reconstruire les bases de données système MASTER, model, msdb et tempdb. Pour plus d’informations, consultez [Reconstruire des bases de données système](../../relational-databases/databases/rebuild-system-databases.md). 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail de reconstruction des bases de données.<br /><br /> Valeurs prises en charge : **Rebuilddatabase**|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **Facultatif**|Spécifie un nouveau classement au niveau du serveur.<br /><br /> La valeur par défaut est basée sur les paramètres régionaux de votre système d'exploitation Windows. Pour plus d'informations, consultez [Paramètres de classement du programme d'installation](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **Obligatoire quand /SECURITYMODE=SQL a été spécifié pendant l’installation de l’instance.**|Spécifie le mot de passe du compte d'administrateur système (SA) SQL.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **Obligatoire**|Utilisez ce paramètre pour configurer des connexions en tant que membres du rôle sysadmin.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **Facultatif**|Spécifie les répertoires des fichiers de données tempdb. Lorsque vous spécifiez plusieurs répertoires, utilisez l’espace comme séparateur. Si plusieurs répertoires sont spécifiés, les fichiers de données tempdb sont répartis entre les répertoires selon le principe du tourniquet (round robin).<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire du fichier journal tempdb.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **Facultatif**|Spécifie le nombre de fichiers de données tempdb que le programme d’installation doit ajouter. Cette valeur peut être augmentée jusqu’au nombre de cœurs. Valeur par défaut :<br /><br /> 1 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 ou le nombre de cœurs, la valeur la plus petite étant applicable pour toutes les autres éditions<br /><br /> **\*\* Important \*\*** Le fichier de base de données principale pour tempdb est toujours tempdb.mdf. Les fichiers tempdb supplémentaires sont nommés tempdb_mssql_#.ndf, où # représente un nombre unique pour chaque fichier de base de données tempdb supplémentaire créé pendant l’installation. L’objectif de cette convention d’affectation de noms est de les rendre uniques. La désinstallation d’une instance de SQL Server supprime les fichiers nommés tempdb_mssql_#.ndf d’après la convention d’affectation de noms. N’utilisez pas la convention d’affectation de noms tempdb_mssql_\*.ndf pour les fichiers de base de données utilisateur.<br /><br /> **\*\* Avertissement \*\*** [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]n’est pas pris en charge pour la configuration de ce paramètre. Le programme d’installation installe uniquement 1 fichier de données tempdb.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier de données tempdb.<br/><br/>Par défaut = 4 Mo pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 8 Mo pour toutes les autres éditions.<br/><br/>Min = (4 ou 8 Mo).<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)]).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **Facultatif**|Spécifie l’incrément de croissance de chaque fichier de données tempdb en Mo. La valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé. La taille maximale autorisée par le programme d’installation s’élève à 1 024.<br /><br /> Valeur par défaut : 64<br /><br /> Plage autorisée : Min = 0, Max = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **Facultatif**|Spécifie la taille initiale en Mo du fichier journal tempdb. La taille maximale autorisée par le programme d’installation s’élève à 1 024. Valeur par défaut :<br /><br /> 4 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 pour toutes les autres éditions<br /><br /> Plage autorisée : Min = valeur par défaut (4 ou 8), Max = 1 024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier journal tempdb.<br/><br/>Par défaut = 4 Mo pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 8 Mo pour toutes les autres éditions.<br/><br/>Min = (4 ou 8 Mo).<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)])|  
  
##  <a name="Uninstall"></a> Paramètres de désinstallation  
 Utilisez les paramètres répertoriés dans le tableau ci-dessous pour développer des scripts de désinstallation en ligne de commande. 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail de désinstallation.<br /><br /> Valeurs prises en charge : **Uninstall**|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/FEATURES<br /><br /> **Obligatoire**|Spécifie les [composants](#Feature) à désinstaller.|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé sera redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour désinstaller une instance existante de SQL Server. 
  
```  
Setup.exe /Action=Uninstall /FEATURES=SQL,AS,RS,IS,Tools /INSTANCENAME=MSSQLSERVER  
```  
  
 Pour supprimer une instance nommée, spécifiez le nom de l'instance au lieu de « MSSQLSERVER » dans l'exemple mentionné plus haut dans cette rubrique. 
  
##  <a name="ClusterInstall"></a> Paramètres de cluster de basculement  
 Avant d’installer une instance de cluster de basculement SQL Server, consultez les rubriques suivantes :  
  
-   [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [[Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)]
  
-   [Avant l’installation du clustering de basculement](../../sql-server/failover-clusters/install/before-installing-failover-clustering.md)  
  
-   [Instances de cluster de basculement Always On &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
    > [!IMPORTANT]  
    >  Toutes les commandes d'installation de cluster de basculement nécessitent un cluster Windows sous-jacent. Tous les nœuds qui font partie d’un cluster de basculement SQL Server doivent appartenir au même cluster Windows. 
  
 Testez et modifiez les scripts d'installation de cluster de basculement suivants selon les besoins de votre organisation. 
  
#### <a name="integrated-install-failover-cluster-parameters"></a>Paramètres d'installation intégrée de cluster de basculement  
 Utilisez les paramètres répertoriés dans le tableau suivant pour développer des scripts d'installation de cluster de basculement en ligne de commande. 
  
 Pour plus d’informations sur l’Installation intégrée, consultez [Instances de cluster de basculement Always On &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md). 
  
> [REMARQUE :](#AddNode) Pour ajouter d’autres nœuds après l’installation, utilisez l’action **Ajouter un nœud**. 
  
|composant SQL Server|Paramètre|Détails|  
|-----------------------------------------|---------------|-------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail d'installation du cluster de basculement.<br /><br /> Valeur prise en charge : **InstallFailoverCluster**|  
|Contrôle d'installation SQL Server|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance.**|Obligatoire pour l'acceptation des termes du contrat de licence.|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERGROUP<br /><br /> **Facultatif**|Spécifie le nom du groupe de ressources à utiliser pour le cluster de basculement SQL Server. Il peut s'agir du nom d'un groupe de clusters existant ou du nom d'un nouveau groupe de ressources.<br /><br /> Valeur par défaut :<br /><br /> SQL Server (\<nom_instance>)|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du compte de service du moteur.|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|PolyBase|/PBPORTRANGE<br /><br /> **Facultatif**|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **Facultatif**|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. Valeurs prises en charge : **True**, **False**|  
|Contrôle d'installation SQL Server|/*UpdateEnabled*<br /><br /> **Facultatif**|Spécifiez si le programme d'installation de SQL Server doit rechercher et inclure les mises à jour du produit. Les valeurs valides sont True et False ou 1 et 0. Par défaut, le programme d'installation de SQL Server inclut les mises à jour trouvées.|  
|Contrôle d'installation SQL Server|/*UpdateSource*<br /><br /> **Facultatif**|Spécifiez l'emplacement où le programme d'installation de SQL Server va récupérer les mises à jour du produit. Les valeurs valides sont « MU » pour rechercher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, un chemin au dossier valide, un chemin relatif tel que .\MyUpdates ou un partage UNC. Par défaut, le programme d’installation de SQL Server lance une recherche dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update ou un service Windows Update par le biais de Windows Server Update Services.|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/ERRORREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’erreurs pour SQL Server.<br /><br /> Pour plus d'informations, consultez [Déclaration de confidentialité du service de rapport d'erreurs Microsoft](http://go.microsoft.com/fwlink/?LinkID=72173). Valeurs prises en charge :<br /><br /> 1 = activé<br /><br /> 0 = désactivé|  
|Contrôle d'installation SQL Server|/FEATURES<br /><br /> **Obligatoire**|Spécifie les [composants](#Feature) à installer.|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé sera redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTALLSHAREDDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés 64 bits.<br /><br /> Par défaut : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server<br /><br /> Ne peut pas être défini avec la valeur %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server|  
|Contrôle d'installation SQL Server|/INSTALLSHAREDWOWDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés 32 bits. Pris en charge uniquement sur un système 64 bits.<br /><br /> Par défaut : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server<br /><br /> Ne peut pas être défini avec la valeur %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server|  
|Contrôle d'installation SQL Server|/ INSTANCEDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants spécifiques à l'instance.|  
|Contrôle d'installation SQL Server|/INSTANCEID<br /><br /> **Facultatif**|Spécifie une valeur différente de la valeur par défaut pour [InstanceID](#InstanceID).|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|Contrôle d'installation SQL Server|/PID<br /><br /> **Facultatif**|Spécifie la clé de produit pour l’édition de SQL Server. Si ce paramètre n'est pas spécifié, Evaluation est utilisée.|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/QS<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute et affiche sa progression via l'interface utilisateur ; toutefois, aucune entrée n'est acceptée et aucun message d'erreur n'est affiché.|  
|Contrôle d'installation SQL Server|/SQMREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’utilisation des fonctionnalités pour SQL Server.<br /><br />Valeurs prises en charge :<br /><br /> 1 = activé<br /><br /> 0 = désactivé|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie si la fenêtre de console est masquée ou fermée.|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERDISKS<br /><br /> **Facultatif**|Spécifie la liste des disques partagés à inclure dans le groupe de ressources de cluster de basculement SQL Server.<br /><br /> Valeur par défaut : le premier lecteur est utilisé comme lecteur par défaut pour toutes les bases de données.|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERIPADDRESSES<br /><br /> **Obligatoire**|Spécifie une adresse IP encodée. Les encodages sont délimités par un point-virgule (;) et suivent le format \<type_IP>;\<adresse>;\<nom_réseau>;\<masque_sous-réseau>. Les types IP pris en charge sont DHCP, IPv4 et IPv6.<br />Vous pouvez spécifier plusieurs adresses IP de cluster de basculement en les séparant avec une espace. Observez les exemples suivants :<br /><br /> FAILOVERCLUSTERIPADDRESSES=DEFAULT<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;172.16.0.0;ClusterNetwork1;172.31.255.255<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;2001:db8:23:1002:20f:1fff:feff:b3a3;ClusterNetwork1|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERNETWORKNAME<br /><br /> **Obligatoire**|Spécifie le nom réseau du nouveau cluster de basculement SQL Server. Ce nom sert à identifier la nouvelle instance de cluster de basculement SQL Server sur le réseau.|  
|SQL Server Agent|/AGTSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour le service SQL Server Agent.|  
|SQL Server Agent|/AGTSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de service SQL Server Agent.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASBACKUPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de sauvegarde [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCOLLATION<br /><br /> **Facultatif**|Spécifie le paramètre de classement pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> Valeur par défaut : **Latin1_General_CI_AS**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCONFIGDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de configuration [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASDATADIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers journaux [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Log.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Log.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSYSADMINACCOUNTS<br /><br /> **Obligatoire**|Spécifie les informations d'identification d'administrateur pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASTEMPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers temporaires [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Temp.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Temp.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASPROVIDERMSOLAP<br /><br /> **Facultatif**|Spécifie si le fournisseur MSOLAP peut s'exécuter in-process.<br /><br /> Valeur par défaut : 1=activé|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSERVERMODE<br /><br /> **Facultatif**|Spécifie le mode serveur de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Les valeurs valides dans un scénario de cluster sont MULTIDIMENSIONAL ou TABULAR. La casse est prise en compte pour**ASSERVERMODE** . Toutes les valeurs doivent être exprimées en majuscules. Pour plus d'informations sur les valeurs valides, consultez Installation d'Analysis Services en mode tabulaire.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/INSTALLSQLDATADIR<br /><br /> **Obligatoire**|Spécifie le répertoire de données pour les fichiers de données SQL Server.<br /><br /> Le répertoire de données doit être spécifié et se trouver sur un disque de cluster partagé.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **Obligatoire quand /SECURITYMODE=SQL**|Spécifie le mot de passe du compte SQL Serversa.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SECURITYMODE<br /><br /> **Facultatif**|Spécifie le mode de sécurité pour SQL Server.<br /><br /> Si ce paramètre n'est pas fourni, le mode d'authentification Windows uniquement est pris en charge.<br /><br /> Valeur prise en charge : **SQL**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLBACKUPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de sauvegarde.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Backup.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **Facultatif**|Spécifie les paramètres de classement pour SQL Server.<br /><br /> La valeur par défaut est basée sur les paramètres régionaux de votre système d'exploitation Windows. Pour plus d'informations, consultez [Paramètres de classement du programme d'installation](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage du service SQL Server.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe pour SQLSVCACCOUNT.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **Obligatoire**|Utilisez ce paramètre pour configurer des connexions en tant que membres du rôle sysadmin.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers de données pour les bases de données utilisateur.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **Facultatif**|Spécifie les répertoires des fichiers de données tempdb. Lorsque vous spécifiez plusieurs répertoires, utilisez l’espace comme séparateur. Si plusieurs répertoires sont spécifiés, les fichiers de données tempdb sont répartis entre les répertoires selon le principe du tourniquet (round robin).<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire du fichier journal tempdb.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **Facultatif**|Spécifie le nombre de fichiers de données tempdb que le programme d’installation doit ajouter. Cette valeur peut être augmentée jusqu’au nombre de cœurs. Valeur par défaut :<br /><br /> 1 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 ou le nombre de cœurs, la valeur la plus petite étant applicable pour toutes les autres éditions<br /><br /> **\*\* Important \*\*** Le fichier de base de données principale pour tempdb est toujours tempdb.mdf. Les fichiers tempdb supplémentaires sont nommés tempdb_mssql_#.ndf, où # représente un nombre unique pour chaque fichier de base de données tempdb supplémentaire créé pendant l’installation. L’objectif de cette convention d’affectation de noms est de les rendre uniques. La désinstallation d’une instance de SQL Server supprime les fichiers nommés tempdb_mssql_#.ndf d’après la convention d’affectation de noms. N’utilisez pas la convention d’affectation de noms tempdb_mssql_\*.ndf pour les fichiers de base de données utilisateur.<br /><br /> **\*\* Avertissement \*\*** [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]n’est pas pris en charge pour la configuration de ce paramètre. Le programme d’installation installe uniquement 1 fichier de données tempdb.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier de données tempdb.<br/><br/>Par défaut = 8 Mo.<br/><br/>Min = 8 Mo.<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)]).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **Facultatif**|Spécifie l’incrément de croissance de chaque fichier de données tempdb en Mo. La valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé. La taille maximale autorisée par le programme d’installation s’élève à 1 024.<br /><br /> Valeur par défaut : 64<br /><br /> Plage autorisée : Min = 0, Max = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **Facultatif**|Spécifie la taille initiale en Mo du fichier journal tempdb. La taille maximale autorisée par le programme d’installation s’élève à 1 024. <br /> Valeur par défaut :<br /><br /> 4 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 pour toutes les autres éditions<br /><br /> Plage autorisée : Min = valeur par défaut (4 ou 8), Max = 1 024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier journal tempdb.<br/><br/>Par défaut = 4 Mo pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 8 Mo pour toutes les autres éditions.<br/><br/>Min = (4 ou 8 Mo).<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)])|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers journaux pour les bases de données utilisateur.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|FILESTREAM|/FILESTREAMLEVEL<br /><br /> **Facultatif**|Spécifie le niveau d'accès pour la fonctionnalité FILESTREAM. Valeurs prises en charge :<br /><br /> 0 = désactiver la prise en charge de FILESTREAM pour cette instance. (Valeur par défaut)<br /><br /> 1 = activer FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] .<br /><br /> 2 = activer FILESTREAM pour [!INCLUDE[tsql](../../includes/tsql-md.md)] et l'accès en continu des E/S de fichier. (Non valide pour les scénarios de clusters)<br /><br /> 3 = permettre aux clients distants d'avoir un accès en continu aux données FILESTREAM.|  
|FILESTREAM|/FILESTREAMSHARENAME<br /><br /> **Facultatif**<br /><br /> **Obligatoire quand FILESTREAMLEVEL est supérieur à 1.**|Spécifie le nom du partage Windows dans lequel les données FILESTREAM doivent être stockées.|  
|Texte intégral SQL Server|/FTSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service du lanceur de filtre de texte intégral.<br /><br /> Ce paramètre est ignoré dans [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]. ServiceSID est utilisé pour aider à sécuriser la communication entre SQL Server et le démon de filtre de texte intégral.<br /><br /> Si les valeurs ne sont pas fournies, le service du lanceur de filtre de texte intégral est désactivé. Vous devez utiliser le Gestionnaire de contrôle des services SQL Server pour modifier le compte de service et activer les fonctionnalités de texte intégral.<br /><br /> Valeur par défaut : Compte de service local|  
|Texte intégral SQL Server|/FTSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du service du lanceur de filtre de texte intégral.<br /><br /> Ce paramètre est ignoré dans [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)].|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].<br /><br /> Valeur par défaut : NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **Facultatif**|Spécifie le mode d'installation pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de démarrage pour le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
 Nous vous recommandons d’utiliser le SID de service au lieu des groupes de domaines. 
  
##### <a name="additional-notes"></a>Remarques supplémentaires :  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont les seuls composants à prendre en charge les clusters. Les autres fonctionnalités ne prennent pas en charge les clusters et n'offrent pas de haute disponibilité par le biais du basculement. 
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour installer une instance du cluster de basculement SQL Server à nœud unique avec le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], l’instance par défaut. 
  
```  
setup.exe /q /ACTION=InstallFailoverCluster /InstanceName=MSSQLSERVER /INDICATEPROGRESS /ASSYSADMINACCOUNTS="<DomainName\UserName>" /ASDATADIR=<Drive>:\OLAP\Data /ASLOGDIR=<Drive>:\OLAP\Log /ASBACKUPDIR=<Drive>:\OLAP\Backup /ASCONFIGDIR=<Drive>:\OLAP\Config /ASTEMPDIR=<Drive>:\OLAP\Temp /FAILOVERCLUSTERDISKS="<Cluster Disk Resource Name - for example, 'Disk S:'" /FAILOVERCLUSTERNETWORKNAME="<Insert Network Name>" /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;Cluster Network;xxx.xxx.xxx.x" /FAILOVERCLUSTERGROUP="MSSQLSERVER" /Features=AS,SQL /ASSVCACCOUNT="<DomainName\UserName>" /ASSVCPASSWORD="xxxxxxxxxxx" /AGTSVCACCOUNT="<DomainName\UserName>" /AGTSVCPASSWORD="xxxxxxxxxxx" /INSTALLSQLDATADIR="<Drive>:\<Path>\MSSQLSERVER" /SQLCOLLATION="SQL_Latin1_General_CP1_CS_AS" /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="xxxxxxxxxxx" /SQLSYSADMINACCOUNTS="<DomainName\UserName> /IACCEPTSQLSERVERLICENSETERMS  
```  
  
#### <a name="prepare-failover-cluster-parameters"></a>Paramètres de préparation de cluster de basculement  
 Utilisez les paramètres répertoriés dans le tableau suivant pour développer des scripts de préparation de cluster de basculement en ligne de commande. Il s'agit de la première étape de l'installation avancée de cluster ; au cours de cette étape, vous devez préparer les instances de cluster de basculement sur tous les nœuds du cluster de basculement. Pour plus d'informations, consultez [Instances de cluster de basculement Always On &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md). 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail de préparation du cluster de basculement.<br /><br /> Valeur prise en charge : **PrepareFailoverCluster**|  
|Contrôle d'installation SQL Server|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance.**|Obligatoire pour l'acceptation des termes du contrat de licence.|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/*UpdateEnabled*<br /><br /> **Facultatif**|Spécifiez si le programme d'installation de SQL Server doit rechercher et inclure les mises à jour du produit. Les valeurs valides sont True et False ou 1 et 0. Par défaut, le programme d'installation de SQL Server inclut les mises à jour trouvées.|  
|Contrôle d'installation SQL Server|/*UpdateSource*<br /><br /> **Facultatif**|Spécifiez l'emplacement où le programme d'installation de SQL Server va récupérer les mises à jour du produit. Les valeurs valides sont « MU » pour rechercher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, un chemin au dossier valide, un chemin relatif tel que .\MyUpdates ou un partage UNC. Par défaut, le programme d’installation de SQL Server lance une recherche dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update ou un service Windows Update par le biais de Windows Server Update Services.|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/ERRORREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’erreurs pour SQL Server.<br /><br /> Pour plus d'informations, consultez [Déclaration de confidentialité du service de rapport d'erreurs Microsoft](http://go.microsoft.com/fwlink/?LinkID=72173). Valeurs prises en charge :<br /><br /> 0 = désactivé<br /><br /> 1 = activé|  
|Contrôle d'installation SQL Server|/FEATURES<br /><br /> **Obligatoire**|Spécifie les [composants](#Feature) à installer.|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé sera redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTALLSHAREDDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés 64 bits.<br /><br /> Par défaut : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server<br /><br /> Ne peut pas être défini avec la valeur %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server|  
|Contrôle d'installation SQL Server|/INSTALLSHAREDWOWDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés 32 bits. Pris en charge uniquement sur un système 64 bits.<br /><br /> Par défaut : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server<br /><br /> Ne peut pas être défini avec la valeur %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server|  
|Contrôle d'installation SQL Server|/ INSTANCEDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants spécifiques à l'instance.|  
|Contrôle d'installation SQL Server|/INSTANCEID<br /><br /> **Facultatif**|Spécifie une valeur différente de la valeur par défaut pour [InstanceID](#InstanceID).|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du compte de service du moteur.|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|PolyBase|/PBPORTRANGE<br /><br /> **Facultatif**|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **Facultatif**|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. Valeurs prises en charge : **True**, **False**|  
|Contrôle d'installation SQL Server|/PID<br /><br /> **Facultatif**|Spécifie la clé de produit pour l’édition de SQL Server. Si ce paramètre n'est pas spécifié,<br /><br /> Evaluation est utilisé.|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/QS<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute et affiche sa progression via l'interface utilisateur ; toutefois, aucune entrée n'est acceptée et aucun message d'erreur n'est affiché.|  
|Contrôle d'installation SQL Server|/SQMREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’utilisation des fonctionnalités pour SQL Server.<br /><br />Valeurs prises en charge :<br /><br /> 0 = désactivé<br /><br /> 1 = activé|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
|SQL Server Agent|/AGTSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour le service SQL Server Agent.|  
|SQL Server Agent|/AGTSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de service SQL Server Agent.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage du service SQL Server.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe pour SQLSVCACCOUNT.|  
|FILESTREAM|/FILESTREAMLEVEL<br /><br /> **Facultatif**|Spécifie le niveau d'accès pour la fonctionnalité FILESTREAM. Valeurs prises en charge :<br /><br /> 0 = désactiver la prise en charge de FILESTREAM pour cette instance. (Valeur par défaut)<br /><br /> 1 = activer FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] .<br /><br /> 2 = activer FILESTREAM pour [!INCLUDE[tsql](../../includes/tsql-md.md)] et l'accès en continu des E/S de fichier. (Non valide pour les scénarios de clusters)<br /><br /> 3 = permettre aux clients distants d'avoir un accès en continu aux données FILESTREAM.|  
|FILESTREAM|/FILESTREAMSHARENAME<br /><br /> **Facultatif**<br /><br /> **Obligatoire** lorsque FILESTREAMLEVEL est supérieur à 1.|Spécifie le nom du partage Windows dans lequel les données FILESTREAM doivent être stockées.|  
|Texte intégral SQL Server|/FTSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service du lanceur de filtre de texte intégral.<br /><br /> Ce paramètre est ignoré dans [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]. ServiceSID est utilisé pour aider à sécuriser la communication entre SQL Server et le démon de filtre de texte intégral.<br /><br /> Si les valeurs ne sont pas fournies, le service du lanceur de filtre de texte intégral est désactivé. Vous devez utiliser le Gestionnaire de contrôle des services SQL Server pour modifier le compte de service et activer les fonctionnalités de texte intégral.<br /><br /> Valeur par défaut : Compte de service local|  
|Texte intégral SQL Server|/FTSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du service du lanceur de filtre de texte intégral.<br /><br /> Ce paramètre est ignoré dans [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)].|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].<br /><br /> Valeur par défaut : NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **Disponible seulement en mode Fichiers uniquement.**|Spécifie le mode d'installation pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de démarrage pour le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
 Nous vous recommandons d’utiliser le SID de service au lieu des groupes de domaines. 
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour effectuer l'étape préparatoire d'un scénario avancé d'installation d'un cluster de basculement pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. 
  
 À l'invite de commandes, exécutez la commande suivante pour préparer une instance par défaut :  
  
```  
setup.exe /q /ACTION=PrepareFailoverCluster /InstanceName=MSSQLSERVER /Features=AS,SQL /INDICATEPROGRESS /ASSVCACCOUNT="<DomainName\UserName>" /ASSVCPASSWORD="xxxxxxxxxxx" /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="xxxxxxxxxxx" /AGTSVCACCOUNT="<DomainName\UserName>" /AGTSVCPASSWORD="xxxxxxxxxxx" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
 À l'invite de commandes, exécutez la commande suivante pour préparer une instance nommée :  
  
```  
setup.exe /q /ACTION=PrepareFailoverCluster /InstanceName="<Insert Instance name>" /Features=AS,SQL /INDICATEPROGRESS /ASSVCACCOUNT="<DomainName\UserName>" /ASSVCPASSWORD="xxxxxxxxxxx" /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="xxxxxxxxxxx" /AGTSVCACCOUNT="<DomainName\UserName>" /AGTSVCPASSWORD="xxxxxxxxxxx" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
#### <a name="complete-failover-cluster-parameters"></a>Paramètres de création de cluster de basculement  
 Utilisez les paramètres répertoriés dans le tableau suivant pour développer des scripts de création de cluster de basculement en ligne de commande. Il s'agit de la seconde étape de l'option d'installation avancée de cluster de basculement. Après avoir effectué la préparation de tous les nœuds de cluster de basculement, vous devez exécuter cette commande sur le nœud qui possède les disques partagés. Pour plus d'informations, consultez [Instances de cluster de basculement Always On &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md). 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail d'exécution du cluster de basculement.<br /><br /> Valeur prise en charge : **CompleteFailoverCluster**|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERGROUP<br /><br /> **Facultatif**|Spécifie le nom du groupe de ressources à utiliser pour le cluster de basculement SQL Server. Il peut s'agir du nom d'un groupe de clusters existant ou du nom d'un nouveau groupe de ressources.<br /><br /> Valeur par défaut :<br /><br /> SQL Server (\<nom_instance>)|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/ERRORREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’erreurs pour SQL Server.<br /><br /> Pour plus d'informations, consultez [Déclaration de confidentialité du service de rapport d'erreurs Microsoft](http://go.microsoft.com/fwlink/?LinkID=72173). Valeurs prises en charge :<br /><br /> 1 = activé<br /><br /> 0 = désactivé|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé sera redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|Contrôle d'installation SQL Server|/PID<br /><br /> **Facultatif**|Spécifie la clé de produit pour l’édition de SQL Server. Si ce paramètre n'est pas spécifié, Evaluation est utilisée.|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/QS<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute et affiche sa progression via l'interface utilisateur ; toutefois, aucune entrée n'est acceptée et aucun message d'erreur n'est affiché.|  
|Contrôle d'installation SQL Server|/SQMREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’utilisation des fonctionnalités pour SQL Server.<br /><br />Valeurs prises en charge :<br /><br /> 1 = activé<br /><br /> 0 = désactivé|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERDISKS<br /><br /> **Facultatif**|Spécifie la liste des disques partagés à inclure dans le groupe de ressources de cluster de basculement SQL Server.<br /><br /> Valeur par défaut :<br /><br /> Le premier lecteur est utilisé comme lecteur par défaut pour toutes les bases de données.|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERIPADDRESSES<br /><br /> **Obligatoire**|Spécifie une adresse IP encodée. Les encodages sont délimités par un point-virgule (;) et suivent le format \<type_IP>;\<adresse>;\<nom_réseau>;\<masque_sous-réseau>. Les types IP pris en charge sont DHCP, IPv4 et IPv6.<br />Vous pouvez spécifier plusieurs adresses IP de cluster de basculement en les séparant avec une espace. Observez les exemples suivants :<br /><br /> FAILOVERCLUSTERIPADDRESSES=DEFAULT<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;172.16.0.0;ClusterNetwork1;172.31.255.255<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;2001:db8:23:1002:20f:1fff:feff:b3a3;ClusterNetwork1|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERNETWORKNAME<br /><br /> **Obligatoire**|Spécifie le nom réseau du nouveau cluster de basculement SQL Server. Ce nom sert à identifier la nouvelle instance de cluster de basculement SQL Server sur le réseau.|  
|Contrôle d'installation SQL Server|/CONFIRMIPDEPENDENCYCHANGE|Indique l'acceptation de définir la dépendance de ressource d'adresse IP sur OR pour les clusters de basculement de sous-réseaux multiples. Pour plus d’informations, consultez [Créer un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md). Valeurs prises en charge :<br /><br /> 0 = False (valeur par défaut)<br /><br /> 1 = True|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASBACKUPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de sauvegarde [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Backup.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCOLLATION<br /><br /> **Facultatif**|Spécifie le paramètre de classement pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> Valeur par défaut : **Latin1_General_CI_AS**|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASCONFIGDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de configuration [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Config.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASDATADIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\\<INSTANCEDIR\>\\<ASInstanceID\>\OLAP\Data.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers journaux [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\ \<INSTANCEDIR>\\<ASInstanceID\>\OLAP\Log.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\ \<INSTANCEDIR>\\<ASInstanceID\>\OLAP\Log.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSERVERMODE<br /><br /> **Facultatif**|Spécifie le mode serveur de l'instance Analysis Services. Les valeurs valides dans un scénario de cluster sont MULTIDIMENSIONAL ou TABULAR. La casse est prise en compte pour**ASSERVERMODE** . Toutes les valeurs doivent être exprimées en majuscules. Pour plus d'informations sur les valeurs valides, consultez Installation d'Analysis Services en mode tabulaire.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSYSADMINACCOUNTS<br /><br /> **Obligatoire**|Spécifie les informations d'identification d'administrateur pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASTEMPDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers temporaires [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Valeurs par défaut :<br /><br /> Pour le mode WOW 64 bits : %Program Files(x86)%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\ \<INSTANCEDIR>\\<ASInstanceID\>\OLAP\Temp.<br /><br /> Pour toutes les autres installations : %Program Files%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server\ \<INSTANCEDIR>\\<ASInstanceID\>\OLAP\Temp.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASPROVIDERMSOLAP<br /><br /> **Facultatif**|Spécifie si le fournisseur MSOLAP peut s'exécuter in-process.<br /><br /> Valeur par défaut : 1=activé|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/INSTALLSQLDATADIR<br /><br /> **Obligatoire**|Spécifie le répertoire de données pour les fichiers de données SQL Server.<br /><br /> Le répertoire de données doit être spécifié et se trouver sur un disque de cluster partagé.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SAPWD<br /><br /> **Obligatoire quand /SECURITYMODE=SQL**|Spécifie le mot de passe du compte SQL Serversa.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SECURITYMODE<br /><br /> **Facultatif**|Spécifie le mode de sécurité pour SQL Server.<br /><br /> Si ce paramètre n'est pas fourni, le mode d'authentification Windows uniquement est pris en charge.<br /><br /> Valeur prise en charge : **SQL**|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLBACKUPDIR<br /><br /> **Facultatif**|Spécifie le répertoire pour les fichiers de sauvegarde.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Backup.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLCOLLATION<br /><br /> **Facultatif**|Spécifie les paramètres de classement pour SQL Server.<br /><br /> La valeur par défaut est basée sur les paramètres régionaux de votre système d'exploitation Windows. Pour plus d'informations, consultez [Paramètres de classement du programme d'installation](http://msdn.microsoft.com/library/ms143508%28v=sql.105%29.aspx).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSYSADMINACCOUNTS<br /><br /> **Obligatoire**|Utilisez ce paramètre pour configurer des connexions en tant que membres du rôle sysadmin.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers de données pour les bases de données utilisateur.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLUSERDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire des fichiers journaux pour les bases de données utilisateur.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **Disponible en mode Fichiers uniquement.**|Spécifie le mode d'installation pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBDIR<br /><br /> **Facultatif**|Spécifie les répertoires des fichiers de données tempdb. Lorsque vous spécifiez plusieurs répertoires, utilisez l’espace comme séparateur. Si plusieurs répertoires sont spécifiés, les fichiers de données tempdb sont répartis entre les répertoires selon le principe du tourniquet (round robin).<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGDIR<br /><br /> **Facultatif**|Spécifie le répertoire du fichier journal tempdb.<br /><br /> Valeur par défaut : \<InstallSQLDataDir>\ \<SQLInstanceID>\MSSQL\Data(System Data Directory)<br /><br /> REMARQUE : ce paramètre est également ajouté au scénario RebuildDatabase.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILECOUNT<br /><br /> **Facultatif**|Spécifie le nombre de fichiers de données tempdb que le programme d’installation doit ajouter. Cette valeur peut être augmentée jusqu’au nombre de cœurs. Valeur par défaut :<br /><br /> 1 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 ou le nombre de cœurs (la plus petite valeur des deux) pour toutes les autres éditions.<br /><br /> **\*\* Important \*\*** Le fichier de base de données principale pour tempdb est toujours tempdb.mdf. Les fichiers tempdb supplémentaires sont nommés tempdb_mssql_#.ndf, où # représente un nombre unique pour chaque fichier de base de données tempdb supplémentaire créé pendant l’installation. L’objectif de cette convention d’affectation de noms est de les rendre uniques. La désinstallation d’une instance de SQL Server supprime les fichiers nommés tempdb_mssql_#.ndf d’après la convention d’affectation de noms. N’utilisez pas la convention d’affectation de noms tempdb_mssql_\*.ndf pour les fichiers de base de données utilisateur.<br /><br /> **\*\* Avertissement \*\*** [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]n’est pas pris en charge pour la configuration de ce paramètre. Le programme d’installation installe uniquement 1 fichier de données tempdb.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILESIZE<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier de données tempdb.<br/><br/>Par défaut = 8 Mo.<br/><br/>Min = 8 Mo.<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)]).|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBFILEGROWTH<br /><br /> **Facultatif**|Spécifie l’incrément de croissance de chaque fichier de données tempdb en Mo. La valeur 0 indique que la croissance automatique est désactivée et qu'aucun espace supplémentaire n'est autorisé. La taille maximale autorisée par le programme d’installation s’élève à 1 024.<br /><br /> Valeur par défaut : 64<br /><br /> Plage autorisée : Min = 0, Max = 1024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILESIZE<br /><br /> **Facultatif**|Spécifie la taille initiale en Mo du fichier journal tempdb. La taille maximale autorisée par le programme d’installation s’élève à 1 024. <br /> Valeur par défaut :<br /><br /> 4 pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]<br /><br /> 8 pour toutes les autres éditions<br /><br /> Plage autorisée : Min = valeur par défaut (4 ou 8), Max = 1 024|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLTEMPDBLOGFILEGROWTH<br /><br /> **Ce paramètre est facultatif**|Introduit dans [!INCLUDE[SQL VERSION](../../includes/sssql15-md.md)]. Spécifie la taille initiale de chaque fichier journal tempdb.<br/><br/>Par défaut = 4 Mo pour [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 8 Mo pour toutes les autres éditions.<br/><br/>Min = (4 ou 8 Mo).<br/><br/>Max = 1 024 Mo (262 144 Mo pour [!INCLUDE[SQL VERSION](../../includes/sssqlv14-md.md)])|  
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour effectuer l'étape exécutoire d'un scénario avancé d'installation d'un cluster de basculement pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Exécutez la commande suivante sur l'ordinateur qui constituera le nœud actif dans le cluster de basculement pour le rendre utilisable. Vous devez exécuter l'action « CompleteFailoverCluster » sur le nœud qui possède le disque partagé dans le cluster de basculement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . 
  
 À l'invite de commandes, exécutez la commande suivante pour effectuer l'installation du cluster de basculement pour une instance par défaut :  
  
```  
setup.exe /q /ACTION=CompleteFailoverCluster /InstanceName=MSSQLSERVER /INDICATEPROGRESS /ASSYSADMINACCOUNTS="<DomainName\Username>" /ASDATADIR=<Drive>:\OLAP\Data /ASLOGDIR=<Drive>:\OLAP\Log /ASBACKUPDIR=<Drive>:\OLAP\Backup /ASCONFIGDIR=<Drive>:\OLAP\Config /ASTEMPDIR=<Drive>:\OLAP\Temp /FAILOVERCLUSTERDISKS="<Cluster Disk Resource Name - for example, 'Disk S:'>:" /FAILOVERCLUSTERNETWORKNAME="<Insert FOI Network Name>" /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;Cluster Network;xxx.xxx.xxx.x" /FAILOVERCLUSTERGROUP="MSSQLSERVER" /INSTALLSQLDATADIR="<Drive>:\<Path>\MSSQLSERVER" /SQLCOLLATION="SQL_Latin1_General_CP1_CS_AS" /SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
```  
  
 À l'invite de commandes, exécutez la commande suivante pour effectuer l'installation du cluster de basculement pour une instance nommée :  
  
```  
setup.exe /q /ACTION=CompleteFailoverCluster /InstanceName="<Insert Instance Name>" /INDICATEPROGRESS /ASSYSADMINACCOUNTS="<DomainName\UserName>" /ASDATADIR=<Drive>:\KATMAI\Data /ASLOGDIR=<drive>:\KATMAI\Log /ASBACKUPDIR=<Drive>:\KATMAI\Backup /ASCONFIGDIR=<Drive>:\KATMAI\Config /ASTEMPDIR=<Drive>:\KATMAI\Temp /FAILOVERCLUSTERDISKS="<Cluster Disk Resource Name - for example, 'Disk S:'>" /FAILOVERCLUSTERNETWORKNAME="CompNamedFOI" /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;ClusterNetwork1;xxx.xxx.xxx.x" /FAILOVERCLUSTERGROUP="<Insert New Group Name>" /INSTALLSQLDATADIR="<Drive>:\<Path>\MSSQLSERVER_KATMAI" /SQLCOLLATION="SQL_Latin1_General_CP1_CS_AS" /SQLSYSADMINACCOUNTS="<DomainName\Username>"  
```  
  
#### <a name="upgrade-failover-cluster-parameters"></a>Paramètres de mise à niveau de cluster de basculement  
 Utilisez les paramètres répertoriés dans le tableau suivant pour développer des scripts de mise à niveau de cluster de basculement en ligne de commande. Pour plus d’informations, consultez [Mise à niveau d’une instance de cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md) et [Instances de cluster de basculement Always On &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md). 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail d'installation.<br /><br /> Valeur prise en charge : **Upgrade**|  
|Contrôle d'installation SQL Server|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance.**|Obligatoire pour l'acceptation des termes du contrat de licence.|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/*UpdateEnabled*<br /><br /> **Facultatif**|Spécifiez si le programme d'installation de SQL Server doit rechercher et inclure les mises à jour du produit. Les valeurs valides sont True et False ou 1 et 0. Par défaut, le programme d'installation de SQL Server inclut les mises à jour trouvées.|  
|Contrôle d'installation SQL Server|/*UpdateSource*<br /><br /> **Facultatif**|Spécifiez l'emplacement où le programme d'installation de SQL Server va récupérer les mises à jour du produit. Les valeurs valides sont « MU » pour rechercher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, un chemin au dossier valide, un chemin relatif tel que .\MyUpdates ou un partage UNC. Par défaut, le programme d’installation de SQL Server lance une recherche dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update ou un service Windows Update par le biais de Windows Server Update Services.|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/ERRORREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. <br/><br/>Pour gérer comment les commentaires d’erreur sont envoyés à Microsoft, consultez [How to configure SQL Server 2016 to send feedback to Microsoft (Comment configurer SQL Server 2016 pour envoyer des commentaires à Microsoft)](http://support.microsoft.com/kb/3153756). <br/><br/>Dans les versions antérieures, cela spécifie le rapport d’erreurs pour SQL Server.<br /><br /> Pour plus d'informations, consultez [Déclaration de confidentialité du service de rapport d'erreurs Microsoft](http://go.microsoft.com/fwlink/?LinkID=72173). Valeurs prises en charge :<br /><br /> 0 = désactivé<br /><br /> 1 = activé|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé sera redirigé vers la console.|  
|Contrôle d'installation SQL Server|/ INSTANCEDIR<br /><br /> **Facultatif**|Spécifie un répertoire d'installation différent du répertoire par défaut pour les composants partagés.|  
|Contrôle d'installation SQL Server|/INSTANCEID<br /><br /> **Obligatoire lors de la mise à niveau à partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou version ultérieure.**<br /><br /> **Facultatif lors de la mise à niveau de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]**|Spécifie une valeur différente de la valeur par défaut pour [InstanceID](#InstanceID).|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|Contrôle d'installation SQL Server|/PID<br /><br /> **Facultatif**|Spécifie la clé de produit pour l’édition de SQL Server. Si ce paramètre n'est pas spécifié, Evaluation est utilisée.|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/SQMREPORTING<br /><br /> **Facultatif**|N’a aucun effet dans SQL Server 2016. Dans les versions antérieures, cela spécifie le rapport d’utilisation des fonctionnalités pour SQL Server.<br /><br />Valeurs prises en charge :<br /><br /> 0 = désactivé<br /><br /> 1 = activé|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERROLLOWNERSHIP|Spécifie le [comportement du basculement](#RollOwnership) pendant la mise à niveau.|  
|Service SQL Server Browser|/BROWSERSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service SQL Server Browser. Valeurs prises en charge :<br /><br /> **Automatic**<br /><br /> **Disabled**<br /><br /> **Manual**|  
|Texte intégral SQL Server|/FTUPGRADEOPTION<br /><br /> **Facultatif**|Spécifie l'option de mise à niveau du catalogue de texte intégral. Valeurs prises en charge :<br /><br /> **REBUILD**<br /><br /> **RESET**<br /><br /> **IMPORT**|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].<br /><br /> Valeur par défaut : NT AUTHORITY\NETWORK SERVICE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCStartupType<br /><br /> **Facultatif**|Spécifie le mode de [démarrage](#Accounts) pour le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSUPGRADEDATABASEACCOUNT<br /><br /> **Facultatif**|La propriété est utilisée uniquement lors de la mise à niveau d'un serveur de rapports en mode SharePoint avec la version 2008 R2 ou antérieure. Des opérations de mise à niveau supplémentaires sont effectuées pour les serveurs de rapports qui utilisent l'ancienne architecture du mode SharePoint, modifiée dans SQL Server 2012 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Si cette option n'est pas incluse dans l'installation de ligne de commande, le compte de service par défaut de l'ancienne instance de serveur de rapports est utilisé. Si cette propriété est utilisée, fournissez le mot de passe du compte à l'aide de la propriété **/RSUPGRADEPASSWORD** .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSUPGRADEPASSWORD<br /><br /> **Facultatif**|Mot de passe du compte de service Report Server existant.|  
  
####  <a name="AddNode"></a> Paramètres d’ajout de nœud  
 Utilisez les paramètres répertoriés dans le tableau ci-dessous pour développer des scripts d'ajout de nœud en ligne de commande. 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail d'ajout de nœud.<br /><br /> Valeur prise en charge : **AddNode**|  
|Contrôle d'installation SQL Server|/IACCEPTSQLSERVERLICENSETERMS<br /><br /> **Obligatoire uniquement quand le paramètre /Q ou /QS est spécifié pour les installations sans assistance.**|Obligatoire pour l'acceptation des termes du contrat de licence.|  
|Contrôle d'installation SQL Server|/ENU<br /><br /> **Facultatif**|Utilisez ce paramètre pour installer la version anglaise de SQL Server sur un système d’exploitation localisé quand le support d’installation inclut des modules linguistiques pour l’anglais et la langue qui correspond au système d’exploitation.|  
|Contrôle d'installation SQL Server|/*UpdateEnabled*<br /><br /> **Facultatif**|Spécifiez si le programme d'installation de SQL Server doit rechercher et inclure les mises à jour du produit. Les valeurs valides sont True et False ou 1 et 0. Par défaut, le programme d'installation de SQL Server inclut les mises à jour trouvées.|  
|Contrôle d'installation SQL Server|/*UpdateSource*<br /><br /> **Facultatif**|Spécifiez l'emplacement où le programme d'installation de SQL Server va récupérer les mises à jour du produit. Les valeurs valides sont « MU » pour rechercher [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, un chemin au dossier valide, un chemin relatif tel que .\MyUpdates ou un partage UNC. Par défaut, le programme d’installation de SQL Server lance une recherche dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update ou un service Windows Update par le biais de Windows Server Update Services.|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé sera redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|PolyBase|/PBENGSVCACCOUNT<br /><br /> **Facultatif**|Spécifie le compte pour le service de moteur. La valeur par défaut est **NT Authority\NETWORK SERVICE**.|  
|PolyBase|/PBDMSSVCPASSWORD<br /><br /> **Facultatif**|Spécifie le mot de passe du compte de service du moteur.|  
|PolyBase|/PBENGSVCSTARTUPTYPE<br /><br /> **Facultatif**|Spécifie le mode de démarrage pour le service de moteur PolyBase : automatique (par défaut), désactivé ou manuel|  
|PolyBase|/PBPORTRANGE<br /><br /> **Facultatif**|Spécifie une plage de ports avec au moins 6 ports pour les services PolyBase. Exemple :<br /><br /> `/PBPORTRANGE=16450-16460`|  
|PolyBase|/PBSCALEOUT<br /><br /> **Facultatif**|Spécifie si l’instance SQL Server sera utilisée dans le cadre du groupe de calcul PolyBase Scale-out. Valeurs prises en charge : **True**, **False**|  
|Contrôle d'installation SQL Server|/PID<br /><br /> **Facultatif**|Spécifie la clé de produit pour l’édition de SQL Server. Si ce paramètre n'est pas spécifié, Evaluation est utilisée.|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/QS<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute et affiche sa progression via l'interface utilisateur ; toutefois, aucune entrée n'est acceptée et aucun message d'erreur n'est affiché.|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
|Contrôle d'installation SQL Server|/FAILOVERCLUSTERIPADDRESSES<br /><br /> **Obligatoire**|Spécifie une adresse IP encodée. Les encodages sont délimités par un point-virgule (;) et suivent le format \<type_IP>;\<adresse>;\<nom_réseau>;\<masque_sous-réseau>. Les types IP pris en charge sont DHCP, IPv4 et IPv6.<br />Vous pouvez spécifier plusieurs adresses IP de cluster de basculement en les séparant avec une espace. Observez les exemples suivants :<br /><br /> FAILOVERCLUSTERIPADDRESSES=DEFAULT<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv4;172.16.0.0;ClusterNetwork1;172.31.255.255<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;DHCP;ClusterNetwork1<br /><br /> FAILOVERCLUSTERIPADDRESSES=IPv6;2001:db8:23:1002:20f:1fff:feff:b3a3;ClusterNetwork1<br /><br /> <br /><br /> Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).|  
|Contrôle d'installation SQL Server|/CONFIRMIPDEPENDENCYCHANGE<br /><br /> **Obligatoire**|Indique l'acceptation de définir la dépendance de ressource d'adresse IP sur OR pour les clusters de basculement de sous-réseaux multiples. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md). Valeurs prises en charge :<br /><br /> 0 = False (valeur par défaut)<br /><br /> 1 = True|  
|SQL Server Agent|/AGTSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour le service SQL Server Agent.|  
|SQL Server Agent|/AGTSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de service SQL Server Agent.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT<br /><br /> **Obligatoire**|Spécifie le compte de démarrage du service SQL Server.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe pour SQLSVCACCOUNT.|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSINSTALLMODE<br /><br /> **Disponible en mode Fichiers uniquement**|Spécifie le mode d'installation pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCPASSWORD<br /><br /> [Obligatoire](#Accounts)|Spécifie le mot de passe du compte de démarrage pour le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
##### <a name="additional-notes"></a>Remarques supplémentaires :  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont les seuls composants à prendre en charge les clusters. Les autres fonctionnalités ne prennent pas en charge les clusters et n'offrent pas de haute disponibilité par le biais du basculement. 
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour ajouter un nœud à une instance existante du cluster de basculement avec le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. 
  
```  
setup.exe /q /ACTION=AddNode /INSTANCENAME="<Insert Instance Name>" /SQLSVCACCOUNT="<SQL account that is used on other nodes>" /SQLSVCPASSWORD="<password for SQL account>" /AGTSVCACCOUNT="<SQL Server Agent account that is used on other nodes>", /AGTSVCPASSWORD="<SQL Server Agent account password>" /ASSVCACCOUNT="<AS account that is used on other nodes>" /ASSVCPASSWORD=”<password for AS account>” /INDICATEPROGRESS /IACCEPTSQLSERVERLICENSETERMS /FAILOVERCLUSTERIPADDRESSES="IPv4;xx.xxx.xx.xx;ClusterNetwork1;xxx.xxx.xxx.x" /CONFIRMIPDEPENDENCYCHANGE=0  
```  
  
#### <a name="remove-node-parameters"></a>Paramètres de suppression de nœud  
 Utilisez les paramètres répertoriés dans le tableau ci-dessous pour développer des scripts de suppression de nœud en ligne de commande. Pour désinstaller un cluster de basculement, vous devez exécuter RemoveNode sur chaque nœud de cluster de basculement. Pour plus d'informations, consultez [Instances de cluster de basculement Always On &#40;SQL Server&#41;](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md). 
  
|composant SQL Server|Paramètre|Description|  
|-----------------------------------------|---------------|-----------------|  
|Contrôle d'installation SQL Server|/ACTION<br /><br /> **Obligatoire**|Obligatoire pour indiquer le flux de travail de suppression de nœud.<br /><br /> Valeur prise en charge : **RemoveNode**|  
|Contrôle d'installation SQL Server|/CONFIGURATIONFILE<br /><br /> **Facultatif**|Spécifie le fichier [ConfigurationFile](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md) à utiliser.|  
|Contrôle d'installation SQL Server|/HELP, H, ?<br /><br /> **Facultatif**|Affiche les options d'utilisation pour les paramètres.|  
|Contrôle d'installation SQL Server|/INDICATEPROGRESS<br /><br /> **Facultatif**|Spécifie que le fichier journal d'installation en mode détaillé sera redirigé vers la console.|  
|Contrôle d'installation SQL Server|/INSTANCENAME<br /><br /> **Obligatoire**|Spécifie un nom d’instance SQL Server.<br /><br /> Pour plus d'informations, consultez [Instance Configuration](http://msdn.microsoft.com/library/5bf822fc-6dec-4806-a153-e200af28e9a5).|  
|Contrôle d'installation SQL Server|/Q<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute en mode silencieux sans interface utilisateur. Il s'agit du mode utilisé pour les installations sans assistance.|  
|Contrôle d'installation SQL Server|/QS<br /><br /> **Facultatif**|Spécifie que le programme d'installation s'exécute et affiche sa progression via l'interface utilisateur ; toutefois, aucune entrée n'est acceptée et aucun message d'erreur n'est affiché.|  
|Contrôle d'installation SQL Server|/HIDECONSOLE<br /><br /> **Facultatif**|Spécifie que la fenêtre de console est masquée ou fermée.|  
|Contrôle d'installation SQL Server|/CONFIRMIPDEPENDENCYCHANGE<br /><br /> **Obligatoire**|Indique l'acceptation de changer la dépendance de ressource d'adresse IP de OR en AND pour les clusters de basculement de sous-réseaux multiples. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md). Valeurs prises en charge :<br /><br /> 0 = False (valeur par défaut)<br /><br /> 1 = True|  
  
###### <a name="sample-syntax"></a>Exemple de syntaxe :  
 Pour supprimer un nœud d'une instance existante du cluster de basculement avec le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. 
  
```  
setup.exe /q /ACTION=RemoveNode /INSTANCENAME="<Insert Instance Name>" [/INDICATEPROGRESS] /CONFIRMIPDEPENDENCYCHANGE=0  
```  
  
##  <a name="Accounts"></a> Paramètres des comptes de service  
 Vous pouvez configurer les services SQL Server à l’aide d’un compte intégré, d’un compte local ou d’un compte de domaine. 
  
> **REMARQUE :** Quand vous utilisez un compte de service administré, un compte virtuel ou un compte intégré, vous ne devez pas spécifier les paramètres de mot de passe correspondants. Pour plus d’informations sur ces comptes de service, consultez la section **Nouveaux types de comptes disponibles avec [!INCLUDE[win7](../../includes/win7-md.md)] et [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]** dans [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md). 
  
 Pour plus d’informations sur la configuration des comptes de service, consultez [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md). 
  
|composant SQL Server|Paramètre de compte|Paramètre de mot de passe|Type de démarrage|  
|-----------------------------------------|-----------------------|------------------------|------------------|  
|SQL Server Agent|/AGTSVCACCOUNT|/AGTSVCPASSWORD|/AGTSVCSTARTUPTYPE|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|/ASSVCACCOUNT|/ASSVCPASSWORD|/ASSVCSTARTUPTYPE|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|/SQLSVCACCOUNT|/SQLSVCPASSWORD|/SQLSVCSTARTUPTYPE|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|/ISSVCACCOUNT|/ISSVCPASSWORD|/ISSVCStartupType|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|/RSSVCACCOUNT|/RSSVCPASSWORD|/RSSVCStartupType|  
  
##  <a name="Feature"></a> Paramètres de fonctionnalités  
 Pour installer des fonctionnalités spécifiques, utilisez le paramètre /FEATURES et spécifiez la fonctionnalité parent ou les valeurs de fonctionnalités répertoriées dans le tableau suivant. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de SQL Server, consultez [Éditions et fonctionnalités prises en charge de SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md). 
  
|Paramètre de fonctionnalité parent|Paramètre de fonctionnalité|Description|  
|:---|:---|:---|  
|SQL||Installe les composants du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], Replication, Fulltext et [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].|  
||SQLEngine|Installe uniquement le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
||Réplication|Installe le composant Replication avec le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
||FullText|Installe le composant FullText avec [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
||DQ|Copie les fichiers requis pour terminer l'installation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . Une fois l'installation de SQL Server terminée, vous devez exécuter le fichier DQSInstaller.exe pour terminer l'installation de [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . Pour plus d’informations, consultez [Exécuter DQSInstaller.exe pour terminer l’installation du serveur DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md). Cette commande installe également le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
||PolyBase|Installe les composants PolyBase.|  
||AdvancedAnalytics|Installe R Services (dans la base de données).|  
|AS||Installe tous les composants [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|RS||Installe tous les composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|RS_SHP||Installe des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint.|  
|RS_SHPWFE||Installe le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint. |  
|DQC||Installe [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].|  
|IS||Installe tous les composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|MDS||Installe [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].|  
|SQL_SHARED_MR||Installe Microsoft R Server.|  
|Tools*||Installe les outils clients et les composants de la documentation en ligne de SQL Server.|  
||BC|Installe les composants de compatibilité descendante.|  
||Conn|Installe les composants de connectivité.|
||DREPLAY_CTLR|Installe Distributed Replay Controller|  
||DREPLAY_CLT|Installe Distributed Replay Client|  
||SNAC_SDK|Installe le SDK pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server Native Client|  
||SDK|Installe le Kit de développement logiciel (SDK).|  
||LocalDB**|Installe LocalDB, un mode d'exécution de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] destiné aux développeurs de programmes.|  

*SQL Server Management Tools (SSMS) figure désormais dans un programme d’installation autonome distinct du programme d’installation de SQL Server. Pour plus d’informations, consultez [Installer SQL Server Management Studio à partir de la ligne de commande](https://msdn.microsoft.com/library/bb500441.aspx#Anchor_1).

 **LocalDB est une option durant l’installation d’une référence de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express. Pour plus d’informations, consultez [SQL Server 2016 Express LocalDB](../../database-engine/configure-windows/sql-server-2016-express-localdb.md). 
  
### <a name="feature-parameter-examples"></a>Exemples de paramètres de fonctionnalités :  
  
|Paramètre et valeurs|Description|  
|--------------------------|-----------------|  
|/FEATURES=SQLEngine|Installe le [!INCLUDE[ssDE](../../includes/ssde-md.md)] sans réplication et recherche en texte intégral.|  
|/FEATURES=SQLEngine, FullText|Installe le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et la recherche en texte intégral.|  
|/FEATURES=SQL, Tools|Installe l'intégralité du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et tous les outils.|  
|/FEATURES=BOL|Installe les composants de la documentation en ligne de SQL Server pour afficher et gérer le contenu d’aide.|  
|/FEATURES=SQLEngine, PolyBase|Installe le moteur PolyBase.|  
  
##  <a name="RoleParameters"></a> Paramètres de rôle  
 Le paramètre de rôle d'installation ou /Role est utilisé pour installer une sélection de fonctionnalités préconfigurées. Les rôles [!INCLUDE[ssAS_md](../../includes/ssas-md.md)] installent une instance d' [!INCLUDE[ssAS_md](../../includes/ssas-md.md)] dans une batterie de serveurs SharePoint existante ou une nouvelle batterie non configurée. Deux rôles d'installation sont fournis pour prendre en charge chaque scénario. Vous ne pouvez choisir d'utiliser qu'un seul rôle d'installation à la fois. Selon le rôle d'installation que vous choisissez, le programme d'installation installe les fonctionnalités et composants qui appartiennent à ce rôle. Vous ne pouvez pas modifier les fonctionnalités et composants désignés pour ce rôle. Pour plus d’informations sur l’utilisation du paramètre de rôle de fonctionnalité, consultez [Installer Power Pivot à partir de l’invite de commandes](http://msdn.microsoft.com/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328). 
  
 Le rôle AllFeatures_WithDefaults correspond au comportement par défaut des éditions de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] et réduit le nombre de boîtes de dialogue présentées à l'utilisateur. Il peut être spécifié à partir de la ligne de commande pendant l’installation d’une édition de SQL Server qui n’est pas [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. 
  
|Rôle|Description|Installe…|  
|----------|-----------------|---------------|  
|SPI_AS_ExistingFarm|Installe [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] comme une instance nommée [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sur une batterie [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] existante ou un serveur autonome.|Moteur de calcul[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , préconfiguré pour le stockage des données en mémoire et le traitement.<br /><br /> Packages de solution[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <br /><br /> Programme d’installation pour le [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]<br /><br /> documentation en ligne de SQL Server|  
|SPI_AS_NewFarm|Installe [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et le [!INCLUDE[ssDE](../../includes/ssde-md.md)] comme une instance nommée [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sur une batterie d'Office [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] nouvelle ou non-configurée, ou sur un serveur autonome. Le programme d’installation de SQL Server configure la batterie de serveurs pendant l’installation du rôle de fonctionnalité.|Moteur de calcul[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , préconfiguré pour le stockage des données en mémoire et le traitement.<br /><br /> Packages de solution[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <br /><br /> documentation en ligne de SQL Server<br /><br /> [!INCLUDE[ssDE](../../includes/ssde-md.md)]<br /><br /> Outils de configuration<br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|AllFeatures_WithDefaults|Installe toutes les fonctionnalités disponibles dans l'édition actuelle.<br /><br /> Ajoute l’utilisateur actuel au rôle serveur fixe **sysadmin** de SQL Server.<br /><br /> Sur [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] ou version ultérieure, lorsque le système d'exploitation n'est pas un contrôleur de domaine, le [!INCLUDE[ssDE](../../includes/ssde-md.md)]et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilisent par défaut le compte NTAUTHORITY\NETWORK SERVICE, et [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilise par défaut le compte NTAUTHORITY\NETWORK SERVICE.<br /><br /> Ce rôle est activé par défaut dans les éditions de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Pour toutes les autres éditions, ce rôle n'est pas activé mais il peut être spécifié via l'interface utilisateur ou à l'aide de paramètres de ligne de commande.|Pour les éditions de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], installe uniquement les fonctionnalités disponibles dans l'édition. Pour les autres éditions, installe toutes les fonctionnalités de SQL Server.<br /><br /> Le paramètre **AllFeatures_WithDefaults** peut être combiné avec d’autres paramètres qui remplacent les paramètres **AllFeatures_WithDefaults** . Par exemple, si les paramètres **AllFeatures_WithDefaults** et **/Features=RS** sont utilisés, la commande d'installation de l'ensemble des fonctionnalités est remplacée par l'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]uniquement ; toutefois, le paramètre **AllFeatures_WithDefaults** est respecté pour l'utilisation du compte de service par défaut de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> Quand vous utilisez le paramètre **AllFeatures_WithDefaults** avec **/ADDCURRENTUSERASSQLADMIN=FALSE** , la boîte de dialogue d’approvisionnement n’est pas remplie automatiquement pour l’utilisateur actuel. Ajoutez **/AGTSVCACCOUNT** et **/AGTSVCPASSWORD** pour spécifier un compte de service et un mot de passe pour SQL Server Agent.|  
  
##  <a name="RollOwnership"></a> Contrôle du comportement du basculement à l’aide du paramètre /FAILOVERCLUSTERROLLOWNERSHIP  
 Pour mettre à niveau un cluster de basculement SQL Server vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous devez exécuter le programme d’installation sur un nœud de cluster de basculement à la fois, en commençant par les nœuds passifs. Le programme d'installation détermine le moment du basculement vers le nœud mis à niveau, selon le nombre total de nœuds dans l'instance de cluster de basculement, et le nombre de nœuds déjà mis à niveau. Lorsqu'au moins la moitié des nœuds a déjà été mise à niveau, le programme d'installation provoque par défaut un basculement vers un nœud mis à niveau. 
  
 Pour contrôler le comportement du basculement des nœuds de cluster pendant le processus de mise à niveau, exécutez l'opération de mise à niveau à partir de l'invite de commandes et utilisez le paramètre /FAILOVERCLUSTERROLLOWNERSHIP pour contrôler le comportement du basculement avant que l'opération de mise à niveau ne place le nœud hors connexion. L'utilisation de ce paramètre est la suivante :  
  
-   /FAILOVERCLUSTERROLLOWNERSHIP=0 ne transfère pas la propriété du cluster (déplacer le groupe) vers les nœuds mis à niveau et n’ajoute pas ce nœud à la liste des propriétaires possibles du cluster SQL Server à la fin de la mise à niveau. 
  
-   /FAILOVERCLUSTERROLLOWNERSHIP=1 transfère la propriété du cluster (déplacer le groupe) vers les nœuds mis à niveau et ajoute ce nœud à la liste des propriétaires possibles du cluster SQL Server à la fin de la mise à niveau. 
  
-   /FAILOVERCLUSTERROLLOWNERSHIP=2 est le paramètre par défaut. Il sera utilisé si ce paramètre n'est pas spécifié. Ce paramètre indique que le programme d’installation de SQL Server gère la propriété du cluster (déplacer le groupe) si nécessaire. 
  
##  <a name="InstanceID"></a> Configuration de l’ID d’instance ou d’InstanceID  
 L'ID d'instance ou le paramètre /InstanceID est utilisé pour spécifier où vous pouvez installer les composants d'instance et le chemin d'accès du Registre de l'instance. La valeur de « INSTANCEID » est une chaîne et doit être unique. 
  
-   SQL Instance ID:MSSQL13.\<INSTANCEID>  
  
-   AS Instance ID:MSAS13.\<INSTANCEID>  
  
-   RS Instance ID:MSRS13.\<INSTANCEID>  
  
 Les composants qui prennent en charge les instances sont installés aux emplacements suivants :  
  
 %Program Files%\\Microsoft SQL Server\\<SQLInstanceID\>  
  
 %Program Files%\\Microsoft SQL Server\\<ASInstanceID\>  
  
 %Program Files Microsoft SQL Server\\<RSInstanceID\>  
  
> **REMARQUE :** Si INSTANCEID n’est pas spécifié sur la ligne de commande, le programme d’installation remplace par défaut \<INSTANCEID> par \<INSTANCENAME>. 
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server 2016 avec l’Assistant Installation](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)   
 [Installation d’un cluster de basculement SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)   
 [[Installer les fonctionnalités Business Intelligence de SQL Server 2016](../../sql-server/install/install-sql-server-business-intelligence-features.md)]  
  
