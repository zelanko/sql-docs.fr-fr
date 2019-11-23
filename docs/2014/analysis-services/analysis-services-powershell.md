---
title: Analysis Services PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f75298a4701f15a1fc0f3f471bf7628f4a7030c1
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72782650"
---
# <a name="analysis-services-powershell"></a>PowerShell Analysis Services
  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] inclut un fournisseur et des applets de commande PowerShell Analysis Services (SQLAS) afin que vous puissiez utiliser Windows PowerShell pour parcourir, administrer et interroger des objets Analysis Services.  
  
 PowerShell Analysis Services se compose des éléments suivants :  
  
-   Fournisseur `SQLAS` utilisé pour naviguer dans la hiérarchie AMO (Analysis Management Object).  
  
-   Applet de commande `Invoke-ASCmd` utilisé pour exécuter un script MDX, DMX ou XMLA.  
  
-   Applets de commande spécifiques aux tâches pour les opérations courantes, telles que le traitement, la gestion des rôles, la gestion des partitions, la sauvegarde et la restauration.  
  
## <a name="in-this-article"></a>Contenu de cet article  
 [Prérequis](#bkmk_prereq)  
  
 [Versions et modes de Analysis Services pris en charge](#bkmk_vers)  
  
 [Exigences en matière d’authentification et considérations relatives à la sécurité](#bkmk_auth)  
  
 [Tâches Analysis Services PowerShell](#bkmk_tasks)  

Pour plus d’informations sur la syntaxe et des exemples, consultez [Analysis Services de référence PowerShell](/sql/analysis-services/powershell/analysis-services-powershell-reference).

##  <a name="bkmk_prereq"></a> Conditions préalables requises  
 Windows PowerShell 2.0 doit être installé. Il est installé par défaut sur les versions plus récentes des systèmes d'exploitation Windows. Pour plus d’informations, consultez [installer Windows PowerShell 2,0](https://msdn.microsoft.com/library/ff637750.aspx)

<!-- ff637750.aspx above is linked to by:  (https://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 Vous devez installer une fonctionnalité SQL Server qui inclut les bibliothèques de module et clients SQL Server PowerShell (SQLPS). La façon la plus simple consiste à installer SQL Server Management Studio, qui inclut automatiquement la fonctionnalité PowerShell et les bibliothèques clientes. Le module SQLPS (SQL Server PowerShell) contient les fournisseurs et applets de commande PowerShell pour toutes les fonctionnalités SQL Server, y compris le module SQLASCmdlets et le fournisseur SQLAS qui ajoute la prise en charge de la navigation dans la hiérarchie d'objets Analysis Services.  
  
 Vous devez importer le module **sqlps** avant de pouvoir utiliser les applets de commande et le fournisseur `SQLAS`. Le fournisseur SQLAS est une extension du fournisseur `SQLServer`. Il existe plusieurs façons d'importer le module SQLPS. Pour plus d’informations, consultez [Importer le module SQLPS](../../2014/database-engine/import-the-sqlps-module.md).  
  
 L'accès à distance à une instance Analysis Services requiert l'activation de l'administration à distance et du partage de fichiers. Pour plus d’informations, consultez [activer l’administration à distance](#bkmk_remote) dans cette rubrique.  
  
##  <a name="bkmk_vers"></a> Versions et modes d'Analysis Services pris en charge  
 Actuellement, PowerShell Analysis Services est pris en charge sur n'importe quelle édition de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services s'exécutant sur Windows Server 2008 R2, Windows Server 2008 SP1 ou Windows 7.  
  
 Le tableau suivant montre la disponibilité de PowerShell Analysis Services dans différents contextes.  
  
|Contexte|Disponibilité des fonctionnalités PowerShell|  
|-------------|-------------------------------------|  
|Bases de données et instances multidimensionnelles|Prise en charge pour l'administration locale et à distance.<br /><br /> La fusion-partition requiert une connexion locale.|  
|Bases de données et instances tabulaires|Prise en charge pour l'administration locale et à distance.<br /><br /> Pour plus d’informations, consultez le blog d’août 2011 sur la [gestion des modèles tabulaires à l’aide de PowerShell](https://go.microsoft.com/fwlink/?linkID=227685).|  
|Bases de données et instances PowerPivot pour SharePoint|Prise en charge limitée. Vous pouvez utiliser des connexions HTTP et le fournisseur SQLAS pour afficher des informations d'instance et de base de données.<br /><br /> Toutefois, l'utilisation des applets de commande n'est pas prise en charge. Vous ne devez pas utiliser Analysis Services PowerShell pour sauvegarder et restaurer la base de données PowerPivot en mémoire, et vous ne devez pas ajouter ou supprimer des rôles, des données de processus ni exécuter un script XMLA aléatoire.<br /><br /> À des fins de configuration, PowerPivot pour SharePoint a une prise en charge PowerShell intégrée qui est fournie séparément. Pour plus d’informations, consultez informations [de référence sur PowerShell pour PowerPivot pour SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).|  
|Connexions natives à des cubes locaux<br /><br /> « Data source = c:\backup\test.CUB »|Non pris en charge.|  
|Connexions HTTP aux fichiers de connexion de modèle sémantique BI (.bism) dans SharePoint<br /><br /> « Data source =http://server/shared_docs/name.bism»|Non pris en charge.|  
|Connexions incorporées aux bases de données PowerPivot<br /><br /> "Data source = $Embedded $"|Non pris en charge.|  
|Contexte de serveur local dans les procédures stockées Analysis Services<br /><br /> « Source de données = * »|Non pris en charge.|  
  
##  <a name="bkmk_auth"></a>Exigences en matière d’authentification et considérations relatives à la sécurité  
 Lors de la connexion à Analysis Services, vous devez utiliser une identité d'utilisateur Windows. Dans la plupart des cas, la connexion se fait via la sécurité intégrée Windows, où l'identité de l'utilisateur actuel définit le contexte de sécurité selon lequel les opérations du serveur sont effectuées. Toutefois, des méthodes d'authentification supplémentaires sont à votre disposition lorsque vous configurez un accès HTTP à Analysis Services. Cette section explique de quelle façon le type de connexion détermine les options d'authentification que vous pouvez utiliser.  
  
 Les connexions à Analysis Services sont caractérisées en tant que connexions natives ou connexions HTTP. Une connexion native est une connexion directe entre une application cliente et le serveur. Dans une session PowerShell, le client PowerShell utilise le fournisseur OLE DB pour Analysis Services pour la connexion directe à une instance d'Analysis Services. Une connexion native s'effectue toujours via la sécurité intégrée Windows, où Analysis Services PowerShell s'exécute en tant qu'utilisateur actuel. Analysis Services ne prend pas en charge l'emprunt d'identité. Si vous souhaitez effectuer une opération en tant qu'utilisateur spécifique, vous devez démarrer la session PowerShell via cet utilisateur.  
  
 Les connexions HTTP se font indirectement via IIS, avec des options d'authentification supplémentaires, comme l'authentification de base, pour la connexion à une instance d'Analysis Services. Étant donné qu'IIS prend en charge l'emprunt d'identité, vous pouvez fournir une chaîne de connexion incluant les informations d'identification qu'IIS utilisera pour l'emprunt d'identité lors de la connexion. Pour fournir des informations d’identification, vous pouvez utiliser le paramètre-Credential.  
  
 **Utilisation du paramètre-Credential dans PowerShell**  
  
 Le paramètre-Credential prend un objet PSCredential qui spécifie un nom d’utilisateur et un mot de passe. Dans Analysis Services PowerShell, le paramètre-Credential est disponible pour les applets de commande qui font une demande de connexion à Analysis Services, par opposition aux cmdlets qui s’exécutent dans le contexte d’une connexion existante. Les applets de commande qui créent une requête de connexion incluent Invoke-ASCmd, Backup-ASDatabase et Restore-ASDatabase. Pour ces applets de commande, le paramètre-Credential peut être utilisé, en supposant que les critères suivants sont satisfaits :  
  
1.  Le serveur est configuré pour l'accès HTTP, ce qui signifie qu'IIS gère la connexion, lit le nom d'utilisateur et le mot de passe et emprunte l'identité de l'utilisateur lors de la connexion à Analysis Services. Pour plus d’informations, voir [Configurer l’accès HTTP à Analysis Services sur Internet Information Services (IIS) 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
2.  Le répertoire virtuel IIS qui a été créé pour l'accès HTTP à Analysis Services est configuré pour l'authentification de base.  
  
3.  Le nom d'utilisateur et le mot de passe fournis par l'objet contenant les informations d'identification retournent une identité d'utilisateur Windows. Analysis Services utilise cette identité pour l'utilisateur actuel. Si l'utilisateur n'est pas un utilisateur Windows, ou ne dispose pas d'autorisations suffisantes pour effectuer l'opération demandée, la requête échouera.  
  
 Pour créer un objet contenant des informations d'identification, vous pouvez utiliser l'applet de commande Get-Credential pour collecter des informations auprès de l'opérateur. Vous pouvez ensuite utiliser l'objet contenant les informations d'identification sur une commande qui se connecte à Analysis Services. L'exemple suivant illustre une approche. Dans cet exemple, la connexion se fait à une instance locale (`SQLSERVER:\SQLAS\HTTP_DS`) configurée pour l’accès HTTP.  
  
```powershell
$cred = Get-Credential adventureworks\dbadmin  
Invoke-ASCmd -Inputfile:"c:\discoverconnections.xmla" -Credential:$cred  
```  
  
 Lorsque vous utilisez l'authentification de base, vous devez toujours utiliser HTTPS avec SSL afin que le nom d'utilisateur et mot de passe soient envoyés sur une connexion chiffrée. Pour plus d’informations, consultez [configurer des protocole SSL dans iis 7,0](https://go.microsoft.com/fwlink/?linkID=184299) et [configurer l’authentification de base (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=230776).  
  
 Souvenez-vous que les informations d'identification, les requêtes et les commandes que vous fournissez dans PowerShell sont transmises sans modification à la couche de transport. Notamment, le contenu sensible dans vos scripts augmente le risque d'une attaque par injection malveillante.  
  
 **Fournir un mot de passe en tant qu’objet Microsoft. Secure. String**  
  
 Certaines opérations, comme la sauvegarde et la restauration, prennent en charge des options de chiffrement qui sont activées lorsque vous fournissez un mot de passe dans la commande. Le mot de passe fourni indique à Analysis Services de chiffrer ou déchiffrer le fichier de sauvegarde. Dans Analysis Services, le mot de passe est instancié en tant qu'objet de chaîne sécurisée. L'exemple suivant illustre l'utilisation de ce paramètre pour collecter un mot de passe de l'opérateur à l'exécution.  
  
```powershell
$pwd = read-host -AsSecureString -Prompt "Password"  
$pwd -is [System.IDisposable]  
```  
  
 Vous pouvez maintenant sauvegarder ou restaurer un fichier de base de données chiffré, en passant la variable $pwd au paramètre de mot de passe. Pour afficher un exemple complet qui combine cette illustration avec d’autres applets de commande, consultez applet de commande [Backup-ASDatabase](/powershell/module/sqlserver/backup-asdatabase) et applet de commande [Restore-ASDatabase](/powershell/module/sqlserver/restore-asdatabase).
  
 Comme étape finale, supprimez le mot de passe et la variable de la session.  
  
```powershell
$pwd.Dispose()  
Remove-Variable -Name pwd  
```  
  
##  <a name="bkmk_tasks"></a>Tâches Analysis Services PowerShell  
 Vous pouvez exécuter PowerShell Analysis Services à partir du shell de gestion Windows PowerShell ou d'une invite de commandes Windows. L'exécution d'Analysis Services PowerShell à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] n'est pas prise en charge.  
  
 Cette section décrit les tâches courantes pour l'utilisation de PowerShell Analysis Services.  
  
-   [Charger le fournisseur et les applets de commande Analysis Services](#bkmk_load)  
  
-   [Activer l’administration à distance](#bkmk_remote)  
  
-   [Se connecter à un objet Analysis Services](#bkmk_connect)  
  
-   [Administrer le service](#bkmk_admin)  
  
-   [Obtenir de l’aide pour Analysis Services PowerShell](#bkmk_help)  
  
###  <a name="bkmk_load"></a>Charger le fournisseur et les applets de commande Analysis Services  
 Le fournisseur Analysis Services est une extension du fournisseur racine SQL Server qui devient disponible lorsque vous importez le module SQLPS. Les applets de commande Analysis Services sont chargés simultanément ; vous pouvez également les charger indépendamment si vous souhaitez les utiliser sans le fournisseur.  
  
-   Exécutez l'applet de commande Import-module pour charger SQLPS qui inclut toutes les fonctionnalités PowerShell Analysis Services. Si vous ne pouvez pas importer le module, vous pouvez temporairement utiliser une stratégie d'exécution sans restriction afin de charger le module. Pour plus d’informations, consultez [Importer le module SQLPS](../../2014/database-engine/import-the-sqlps-module.md).  
  
    ```powershell
    Import-Module "sqlps"  
    ```  
  
     Sinon, utilisez `import-module "sqlps" -disablenamechecking` pour supprimer l'avertissement concernant les noms de verbe non approuvés.  
  
-   Pour charger uniquement les applets de commande Analysis Services spécifiques à une tâche, sans le fournisseur Analysis Services ou l'applet de commande Invoke-ASCmd, vous pouvez charger le module SQLASCmdlets comme opération indépendante.  
  
    ```powershell
    Import-Module "sqlascmdlets"  
    ```  
  
###  <a name="bkmk_remote"></a>Activer l’administration à distance  
 Avant de pouvoir utiliser PowerShell Analysis Services avec une instance Analysis Services distante, vous devez d'abord activer l'administration à distance et le partage de fichiers. L’erreur suivante indique un problème de configuration du pare-feu : «le serveur RPC n’est pas disponible. (Exception de HRESULT : 0x800706BA) ».  
  
1.  Vérifiez que les ordinateurs local et distant ont tous deux les versions [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] des outils clients et serveur.  
  
2.  Sur le serveur distant qui héberge une instance Analysis Services, ouvrez le port TCP 2383 dans le Pare-feu Windows. Si vous avez installé Analysis Services comme instance nommée ou utilisez un port personnalisé, le numéro de port sera différent. Pour plus d’informations, consultez [Configurer le pare-feu Windows pour autoriser l’accès à Analysis Services](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
3.  Sur le serveur distant, vérifiez que les services suivants sont démarrés : service d'appel de procédure distante (RPC), service d'assistance TCP/IP NetBIOS, service WMI (Windows Management Instrumentation), service Gestion à distance de Windows (Gestion WSM).  
  
4.  Sur le serveur distant, démarrez le composant logiciel enfichable Éditeur d'objets de stratégie de groupe (gpedit.msc).  
  
5.  Ouvrez Configuration ordinateur, Modèles d'administration, Réseau, Connexions réseau, Pare-feu Windows, puis Profil de domaine.  
  
6.  Double-cliquez sur **pare-feu Windows : autoriser l’exception d’administration à distance entrante**, sélectionnez **activé**, puis cliquez sur **OK**.  
  
7.  Double-cliquez sur **pare-feu Windows : autoriser l’exception de partage de fichiers entrants et d’imprimantes**, sélectionnez **activé**, puis cliquez sur **OK**.  
  
8.  Sur l’ordinateur local qui contient les outils clients, utilisez les applets de commande suivantes pour vérifier l’administration à distance, en remplaçant le nom de serveur réel de l’espace réservé de *nom de serveur distant* . Omettez le nom de l'instance si Analysis Services est installé comme instance par défaut. Vous devez avoir déjà importé le module SQLPS pour que la commande fonctionne.  
  
    ```
    PS SQLSERVER:\> cd sqlas
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 Dans certains cas, une configuration supplémentaire peut être nécessaire. Vous devrez peut-être taper ce qui suit sur le serveur distant avant de pouvoir lui fournir des commandes à partir d'un autre ordinateur :  
  
```powershell
Enable-PSRemoting  
```  
  
  
###  <a name="bkmk_connect"></a>Se connecter à un objet Analysis Services  
 Le fournisseur PowerShell Analysis Services prend en charge la navigation de la hiérarchie d'objets Analysis Services et définit le contexte pour l'exécution de commandes. Le fournisseur est une extension du fournisseur racine SQLSERVER disponible par le module SQLPS. Après avoir chargé le module SQLPS, vous pouvez naviguer dans le chemin d'accès.  
  
 Vous pouvez vous connecter à une instance locale ou distante, mais certains applets de commande sont exécutés uniquement sur une instance locale (à savoir, merge-partition). Vous pouvez utiliser une connexion native ou une connexion HTTP pour les serveurs Analysis Services que vous avez configurés pour l'accès HTTP. Les illustrations suivantes montrent le chemin de navigation pour les connexions native et HTTP. Les illustrations suivantes montrent le chemin de navigation pour les connexions native et HTTP.  
  
 **Connexions natives à Analysis Services**  
  
 ![Connexion native à Analysis Services](media/ssas-powershell-nativeconnection.gif "Connexion native à Analysis Services")  
  
 L'exemple suivant montre comment utiliser une connexion native pour naviguer dans la hiérarchie d'objets. À partir du fournisseur, vous pouvez émettre `dir` pour afficher les informations d'instance. Vous pouvez utiliser `cd` pour afficher les objets de cette instance.  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 Vous devez voir les collections suivantes : Assemblies, Databases, Roles et Traces. En continuant à utiliser `cd` et `dir`, vous pouvez afficher le contenu de chaque collection.  
  
 **Connexions HTTP à Analysis Services**  
  
 ![Connexion HTTP à Analysis Services](media/ssas-powershell-httpconnection.gif "Connexion HTTP à Analysis Services")  
  
 Les connexions HTTP sont utiles si vous avez configuré votre serveur pour l’accès HTTP à l’aide des instructions de cette rubrique : [configurer l' &#40;accès&#41; http à Analysis Services sur Internet Information Services IIS 8,0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
 En supposant une URL de serveur de http://localhost/olap/msmdpump.dll, une connexion peut se présenter comme suit :  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName "http://localhost/olap/msmdpump.dll"  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 Vous devez voir les collections suivantes : Assemblies, Databases, Roles et Traces. Si vous ne pouvez pas afficher le contenu de ces collections, vérifiez les paramètres d'authentification dans le répertoire virtuel OLAP. Vérifiez que l'accès anonyme est désactivé. Si vous utilisez l'authentification Windows, assurez-vous que votre compte d'utilisateur Windows dispose d'autorisations d'administrateur sur l'instance Analysis Services.  
  
###  <a name="bkmk_admin"></a>Administrer le service  
 Vérifiez que le service est en cours d'exécution. Retourne l'état, le nom et le nom complet pour les services SQL Server, notamment Analysis Services (MSSQLServerOLAPService) et le moteur de base de données.  
  
```powershell
Get-Service mssql*  
```  
  
 Retourne les propriétés d'un processus, y compris l'ID de processus, le nombre de handles et l'utilisation de la mémoire :  
  
```powershell
Get-Process msmdsrv  
```  
  
 Redémarre le service lorsque vous émettez l'applet de commande suivant à partir du shell d'administrateur :  
  
```powershell
Restart-Service mssqlserverolapservice  
```  
  
###  <a name="bkmk_help"></a>Obtenir de l’aide pour Analysis Services PowerShell  
 Utilisez l'un des applets de commande suivants pour vérifier la disponibilité des applets de commande et pour obtenir plus d'informations sur les services, processus et objets.  
  
1.  `Get-Help` retourne l'aide intégrée pour un applet de commande Analysis Services, notamment des exemples :  
  
    ```powershell
    Get-Help invoke-ascmd -Examples  
    ```  
  
2.  `Get-Command` retourne une liste des onze applets de commande PowerShell Analysis Services :  
  
    ```powershell
    Get-Command -module SQLASCmdlets  
    ```  
  
3.  `Get-Member` retourne des propriétés ou des méthodes d'un service ou processus.  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Property  
    ```  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Method  
    ```  
  
    ```powershell
    Get-Process msmdsrv | Get-Member -Type Property  
    ```  
  
4.  `Get-Member` peut également être utilisé pour retourner des propriétés ou des méthodes d'un objet (par exemple, les méthodes AMO sur l'objet serveur) à l'aide du fournisseur SQLAS pour spécifier l'instance de serveur.  
  
    ```
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | Get-Member -Type Method  
    ```  
  
5.  `Get-PSdrive` retourne la liste des fournisseurs qui sont actuellement installés. Si vous avez importé le module SQLPS, le fournisseur `SQLServer` s'affiche dans la liste (SQLAS fait partie du fournisseur SQLServer et n'apparaît jamais séparément dans la liste) :  
  
    ```powershell
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md)   
 [Gérer les modèles tabulaires à l’aide de PowerShell (blog)](https://go.microsoft.com/fwlink/?linkID=227685)   
 [Configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
