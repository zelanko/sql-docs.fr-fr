---
title: Installer SQL Server 2014 sur Server Core | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 1dd294cc-5b69-4d0c-9005-3e307b75678b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5235f19b1d85282d7c66ffa64f4dcdc1a43a0fc1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48225889"
---
# <a name="install-sql-server-2014-on-server-core"></a>Installer SQL Server 2014 sur Server Core
  Vous pouvez installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur une installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)]. Cette rubrique fournit des détails spécifiques à l'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur Server Core.  
  
 L'option d'installation de Server Core pour le système d'exploitation [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)] offre l'environnement minimal requis pour l'exécution de certains rôles de serveurs spécifiques. Cela permet de réduire les besoins en maintenance et gestion et l'exposition aux attaques de ces rôles de serveur. Pour plus d’informations sur Server Core implémenté sur [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], consultez [Server Core pour Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=202439) (http://go.microsoft.com/fwlink/?LinkId=202439). Pour plus d’informations sur Server Core implémenté sur [!INCLUDE[win8srv](../../includes/win8srv-md.md)], consultez [Server Core for Windows Server 2012](http://msdn.microsoft.com/library/hh846323\(VS.85\).aspx) (http://msdn.microsoft.com/library/hh846323(VS.85).aspx).  
  
## <a name="prerequisites"></a>Prérequis  
  
|Condition requise|Procédure d'installation|  
|-----------------|--------------------|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 2.0 SP2|Inclus dans l'installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 et de [!INCLUDE[win8srv](../../includes/win8srv-md.md)]. S'il n'est pas activé, le programme d'installation l'active par défaut.<br /><br /> Il n'est pas possible d'exécuter les versions 2.0, 3.0 et 3.5 côte à côte sur un ordinateur. Lorsque vous installez le .NET Framework 3.5 SP1, vous obtenez les couches 2.0 et 3.0 automatiquement.|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Profil 3.5 SP1 complet|Inclus dans l'installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1. S'il n'est pas activé, le programme d'installation l'active par défaut.<br /><br /> Sur un ordinateur disposant du système d'exploitation Windows Server, vous devez télécharger et installer le .NET Framework 3.5 SP1 avant d'exécuter le programme d'installation, pour installer les composants qui dépendent du NET 3.5 SP1.<br /><br /> Pour plus d’informations sur les recommandations et des instructions sur la façon d’obtenir et activer le .NET Framework 3.5 dans [!INCLUDE[win8srv](../../includes/win8srv-md.md)], consultez [considérations relatives au déploiement de Microsoft .NET Framework 3.5](http://msdn.microsoft.com/library/windows/hardware/hh975396) (http://msdn.microsoft.com/library/windows/hardware/hh975396).|  
|[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Profil 4 Server Core|Pour toutes les éditions de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sauf [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], le programme d'installation installe le profil 4 Server Core [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] comme condition préalable.<br /><br /> Pour [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)], téléchargez le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] profil 4 Server Core à partir de [Microsoft .NET Framework 4 (programme d’installation autonome) pour Server Core](http://go.microsoft.com/fwlink/?LinkId=220467) (http://go.microsoft.com/fwlink/?LinkId=220467)et l’installer avant de poursuivre l’installation.|  
|Windows Installer 4.5|Inclus dans l'installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 et de [!INCLUDE[win8srv](../../includes/win8srv-md.md)].|  
|Windows PowerShell 2.0|Inclus dans l'installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 et de [!INCLUDE[win8srv](../../includes/win8srv-md.md)].|  
  
##  <a name="BK_SupportedFeatures"></a> Fonctionnalités prises en charge  
 Utilisez le tableau suivant pour rechercher les fonctionnalités prises en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur une installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 et [!INCLUDE[win8srv](../../includes/win8srv-md.md)].  
  
|Fonctionnalité|Pris en charge|  
|-------------|---------------|  
|du[!INCLUDE[ssDE](../../includes/ssde-md.md)] |Oui|  
|Réplication[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] |Oui|  
|Recherche en texte intégral|Oui|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Oui|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|non|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Tools (SSDT)|non|  
|Connectivité des outils clients|Oui|  
|Serveur Integration Services<sup>[1]</sup>|Oui|  
|Compatibilité descendante des outils clients|non|  
|Kit de développement logiciel (SDK) des outils clients|non|  
|Documentation en ligne[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] |non|  
|Outils de gestion - Base|À distance uniquement<sup>[2]</sup>|  
|Outils d'administration – Complets|À distance uniquement<sup>[2]</sup>|  
|Distributed Replay Controller|non|  
|Distributed Replay Client|À distance uniquement<sup>[2]</sup>|  
|Kit de développement logiciel (SDK) de l'option Connectivité client de SQL|Oui|  
|Microsoft Sync Framework|Oui<sup>[3]</sup>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|non|  
|[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]|non|  
  
 <sup>[1] </sup>Pour plus d’informations sur le nouveau serveur Integration Services et ses fonctionnalités dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez [Integration Services &#40;SSIS&#41; Server](../../integration-services/catalog/integration-services-ssis-server-and-catalog.md).  
  
 <sup>[2] </sup>Installation de ces fonctionnalités sur Server Core n’est pas pris en charge. Ces composants peuvent être installés sur un serveur autre que [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core et être connectés aux services de [!INCLUDE[ssDE](../../includes/ssde-md.md)] installés sur Server Core.  
  
 <sup>[3] </sup>Microsoft Sync Framework n’est pas inclus dans le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] package d’installation. Vous pouvez télécharger la version appropriée de Sync Framework à partir de ce [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=221788) (http://go.microsoft.com/fwlink/?LinkId=221788) page et l’installer sur un ordinateur exécutant une installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)].  
  
## <a name="supported-scenario-matrix"></a>Matrice de scénario prise en charge  
 Le tableau suivant indique la matrice de scénario prise en charge pour l'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur une installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 et [!INCLUDE[win8srv](../../includes/win8srv-md.md)].  
  
|||  
|-|-|  
|Éditions de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] |Tous les [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] éditions 64 bits<sup>[1]</sup>|  
|Langue de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] |Tous les langages|  
|Langage[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le langage du système d'exploitation/paramètres régionaux (combinaison)|ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows JPN (japonais)<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows GER (allemand)<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows CHS (chinois-Chine)<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows ARA (Arabe (Arabie-Saoudite))<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows THA (thaïlandais)<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows TRK (turque)<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows pt-PT (portugais Portugal)<br /><br /> ENG [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Windows ENG (anglais)|  
|Édition Windows|[!INCLUDE[win8srv](../../includes/win8srv-md.md)] 64-bit x64 Datacenter<br /><br /> [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 64-bit x64 Standard<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-bit x64 Data Center Server Core<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-bit x64 Enterprise Server Core<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-bit x64 Standard Server Core<br /><br /> [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 64-bit x64 Web Server Core|  
  
 <sup>[1] </sup>L’installation de la version 32 bits de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] éditions n’est pas pris en charge sur Server Core.  
  
## <a name="upgrading"></a>Mise à niveau  
 Sur les installations Server Core, la mise à niveau depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] n'est pas prise en charge.  
  
## <a name="installation"></a>Installation  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne prend pas en charge l'installation avec l'Assistant d'installation sur le système d'exploitation de Server Core. Lors de l'installation sous Server Core, le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge le mode silencieux complet via le paramètre /Q ou le mode silencieux simple via le paramètre /QS. Pour plus d’informations, consultez [Installer SQL Server 2014 à partir de l’invite de commandes](install-sql-server-from-the-command-prompt.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne peut pas être installé côte à côte avec des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur qui exécute [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core.  
  
 Indépendamment de la méthode d'installation, vous êtes invité à confirmer l'acceptation des termes de la licence de logiciel en tant que personne physique ou pour le compte d'une entité, sauf si votre utilisation du logiciel est régie par un accord distinct, tel qu'un accord de concession de licence en volume de [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou un accord tiers avec un éditeur de logiciels ou un fabricant OEM.  
  
 Les termes du contrat de licence sont affichés afin que vous puissiez les consulter et les accepter dans l'interface utilisateur du programme d'installation. Les installations sans assistance (à l'aide du paramètre /Q ou /QS) doivent inclure le paramètre /IACCEPTSQLSERVERLICENSETERMS. Vous pouvez consulter les termes du contrat de licence séparément sur la page [Termes du contrat de licence logiciel Microsoft](http://go.microsoft.com/fwlink/?LinkId=148209).  
  
> [!NOTE]  
>  Selon la façon dont vous avez reçu le logiciel (par exemple, via le programme de licence en volume [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), votre utilisation du logiciel peut être soumise à des termes et conditions supplémentaires.  
  
 Pour installer des fonctionnalités spécifiques, utilisez le paramètre /FEATURES et spécifiez la fonctionnalité parent ou les valeurs de fonctionnalités. Pour plus d'informations sur les paramètres de fonctionnalités et leur utilisation, consultez les sections suivantes.  
  
### <a name="feature-parameters"></a>Paramètres de fonctionnalités  
  
|Paramètre de fonctionnalité|Description|  
|-----------------------|-----------------|  
|SQLENGINE|Installe uniquement [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|REPLICATION|Installe le composant Replication avec le [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|FULLTEXT|Installe le composant FullText avec [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|AS|Installe tous les composants [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|IS|Installe tous les composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|CONN|Installe les composants de connectivité.|  
  
 Consultez les exemples suivants de l'utilisation de paramètres de fonctionnalités :  
  
|Paramètre et valeurs|Description|  
|--------------------------|-----------------|  
|/FEATURES=SQLEngine|Installe uniquement [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|/FEATURES=SQLEngine,FullText|Installe le [!INCLUDE[ssDE](../../includes/ssde-md.md)] et la recherche en texte intégral.|  
|/FEATURES=SQLEngine,Conn|Installe les [!INCLUDE[ssDE](../../includes/ssde-md.md)] et composants de connectivité.|  
|/FEATURES=SQLEngine,AS,IS,Conn|Installe les [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et composants de connectivité.|  
  
### <a name="installation-options"></a>Options d'installation  
 L'installation prend en charge les options d'installation suivantes lors de l'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur un système d'exploitation Server Core :  
  
1.  **Installation à partir de la ligne de commande**  
  
     Pour installer des fonctionnalités spécifiques à l'aide de l'option d'installation de l'invite de commande, utilisez le paramètre /FEATURES et spécifiez la fonctionnalité parent ou les valeurs de fonctionnalités répertoriées dans le tableau suivant. Voici un exemple d'utilisation des paramètres de la ligne de commande :  
  
    ```  
    Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /TCPENABLED=1 /IACCEPTSQLSERVERLICENSETERMS  
    ```  
  
2.  **Installation à l’aide du fichier de configuration**  
  
     Le programme d'installation prend en charge l'utilisation du fichier de configuration uniquement via l'invite de commandes. Le fichier de configuration est un fichier texte avec une structure de base d'un paramètre (paire nom/valeur) et d'un commentaire descriptif. Le fichier de configuration spécifié à l'invite de commande doit avoir une extension de nom de fichier .INI. Consultez les exemples suivants de ConfigurationFile.INI :  
  
    -   Installation de [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
         L’exemple suivant montre comment installer une nouvelle instance autonome qui inclut le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]:  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine, and Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Accept the License agreement to continue with Installation  
  
        IAcceptSQLServerLicenseTerms="True"  
  
        ```  
  
    -   Installation des composants de connectivité  
  
         L'exemple suivant montre comment installer les composants de connectivité :  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=Conn  
  
        ; Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True  
  
        ```  
  
    -   Installation de toutes les fonctionnalités prises en charge  
  
         L'exemple suivant montre comment installer toutes les fonctionnalités prises en charge de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur Server Core :  
  
        ```  
        ; ssNoVersion Configuration File  
        [OPTIONS]  
        ; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE. This is a required parameter.   
  
        ACTION="Install"  
  
        ; Specifies features to install, uninstall, or upgrade. The lists of features include SQLEngine, FullText, Replication, AS, IS, and Conn.   
  
        FEATURES=SQLENGINE,FullText,Replication,AS,IS,Conn  
  
        ; Specify a default or named instance. MSSQLSERVER is the default instance for non-Express editions and SQLExpress for Express editions. This parameter is required when installing the ssNoVersion Database Engine (SQL), or Analysis Services (AS).  
  
        INSTANCENAME="MSSQLSERVER"  
  
        ; Specify the Instance ID for the ssNoVersion features you have specified. ssNoVersion directory structure, registry structure, and service names will incorporate the instance ID of the ssNoVersion instance.   
  
        INSTANCEID="MSSQLSERVER"  
  
        ; Account for ssNoVersion service: Domain\User or system account.   
  
        SQLSVCACCOUNT="NT Service\MSSQLSERVER"  
  
        ; Windows account(s) to provision as ssNoVersion system administrators.   
  
        SQLSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; The name of the account that the Analysis Services service runs under.   
  
        ASSVCACCOUNT= "NT Service\MSSQLServerOLAPService"  
  
        ; Specifies the list of administrator accounts that need to be provisioned.   
  
        ASSYSADMINACCOUNTS="<DomainName\UserName>"  
  
        ; Specifies the server mode of the Analysis Services instance. Valid values are MULTIDIMENSIONAL, POWERPIVOT or TABULAR. ASSERVERMODE is case-sensitive. All values must be expressed in upper case.   
  
        ASSERVERMODE="MULTIDIMENSIONAL"  
  
        ; Optional value, which specifies the state of the TCP protocol for the ssNoVersion service. Supported values are: 0 to disable the TCP protocol, and 1 to enable the TCP protocol.  
  
        TCPENABLED=1  
  
        ;Specifies acceptance of License Terms  
  
        IAcceptSQLServerLicenseTerms="True"  
        ```  
  
     Les exemples suivants montrent comment lancer l’installation à l’aide d’un fichier de configuration.  
  
    -   Fichier de configuration  
  
         Voici quelques exemples qui illustrent l’utilisation du fichier de configuration :  
  
        -   Pour spécifier le fichier de configuration à l'invite de commandes :  
  
        ```  
        Setup.exe /QS /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
        -   Pour spécifier des mots de passe à l'invite de commandes plutôt que dans le fichier de configuration :  
  
        ```  
        Setup.exe /QS /SQLSVCPASSWORD="************" /ASSVCPASSWORD="************"  /ConfigurationFile=MyConfigurationFile.INI  
        ```  
  
    -   DefaultSetup.ini  
  
         Si vous le fichier DefaultSetup.ini figure dans les dossiers \x86 et \x64 au niveau de la racine du média source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ouvrez le fichier DefaultSetup.ini, puis ajoutez le paramètre *Features* au fichier.  
  
         Si le fichier DefaultSetup.ini n'existe pas, vous pouvez le créer et le copier dans les dossiers \x86 et \x64 au niveau de la racine du média source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="configuring-remote-access-of-includessnoversionincludesssnoversion-mdmd-running-on-server-core"></a>Configuration de l'accès à distance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutant sur Server Core  
 Effectuez les actions décrites ci-dessous pour configurer l'accès à distance d'une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] qui s'exécute sur une installation Server Core de [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)].  
  
### <a name="enable-remote-connections-on-the-instance-of-includessnoversionincludesssnoversion-mdmd"></a>Activer les connexions distantes sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Pour activer les connexions distantes, utilisez SQLCMD.exe localement et exécutez les instructions suivantes sur l'instance de Server Core :  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-includessnoversionincludesssnoversion-mdmd-browser-service"></a>Activer et démarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser  
 Par défaut, le service Browser est désactivé.  Si elle est désactivée sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécutant sur Server Core, exécutez la commande suivante à partir de l'invite de commandes pour l'activer :  
  
 `sc config SQLBROWSER start= auto`  
  
 Après activation, exécutez la commande suivante à partir de l'invite de commandes pour démarrer le service :  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a>Créer des exceptions dans le pare-feu Windows  
 Pour créer des exceptions pour l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le Pare-feu Windows, suivez les étapes spécifiées dans [Configurer le Pare-feu Windows pour autoriser l’accès à SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
### <a name="enable-tcpip-on-the-instance-of-includessnoversionincludesssnoversion-mdmd"></a>Activer TCP/IP sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Le protocole TCP/IP peut être activé via Windows PowerShell pour une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Server Core. Procédez comme suit :  
  
1.  Sur un ordinateur qui exécute [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, lancez le Gestionnaire des tâches.  
  
2.  Dans l'onglet **Applications** , cliquez sur **Nouvelle tâche**.  
  
3.  Dans la boîte de dialogue **Créer une nouvelle tâche** , tapez **sqlps.exe** dans le champ **Ouvrir** , puis cliquez sur **OK**. Cela ouvre la fenêtre **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell**.  
  
4.  Dans la fenêtre **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell**, exécutez le script suivant pour activer le protocole TCP/IP :  
  
```  
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = new-object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
## <a name="uninstallation"></a>Désinstallation  
 Après avoir ouvert une session sur un ordinateur qui exécute [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1 ou [!INCLUDE[win8srv](../../includes/win8srv-md.md)] Server Core, vous disposez d'un environnement de bureau limité avec une invite de commandes d'administrateur. Vous pouvez utiliser cette invite de commandes pour lancer la désinstallation d'une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour désinstaller une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], lancez la désinstallation à partir de l'invite de commandes en mode silencieux complet à l'aide du paramètre /Q ou en mode silencieux simple à l'aide du paramètre /QS. Le paramètre /QS indique la progression via l'interface utilisateur, mais n'accepte aucune entrée. /Q s'exécute en mode silencieux sans interface utilisateur.  
  
 Pour désinstaller une instance existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
Setup.exe /Q /Action=Uninstall /FEATURES=SQLEngine,AS,IS /INSTANCENAME=MSSQLSERVER  
```  
  
 Pour supprimer une instance nommée, spécifiez le nom de l'instance au lieu de « MSSQLSERVER » dans l'exemple précédent.  
  
> [!WARNING]  
>  Si vous fermez accidentellement l'invite de commandes, vous pouvez démarrer une nouvelle invite de commandes en suivant ces étapes :  
>   
>  1.  Appuyez sur Ctrl+Shift+Esc pour afficher le Gestionnaire des tâches.  
> 2.  Dans l'onglet **Applications** , cliquez sur **Nouvelle tâche**.  
> 3.  Dans la boîte de dialogue **Créer une nouvelle tâche** , tapez **cmd** dans le champ **Ouvrir** , [!INCLUDE[clickOK](../../includes/clickok-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server 2014 à l’aide d’un fichier de Configuration](install-sql-server-using-a-configuration-file.md)   
 [Installer SQL Server 2014 à partir de l’invite de commandes](install-sql-server-from-the-command-prompt.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Guide pas à pas de l’option d’installation Server Core de Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=221422)   
 [Configuration d’une installation Server Core : présentation](http://go.microsoft.com/fwlink/?LinkId=221423)   
 [Applets de commande de cluster de basculement dans Windows PowerShell répertoriées par tâche](http://go.microsoft.com/fwlink/?LinkId=221419)   
 [Mappage des commandes Cluster.exe aux applets de commande Windows PowerShell pour les clusters de basculement](http://go.microsoft.com/fwlink/?LinkId=221421)  
  
  
