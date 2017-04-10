---
title: "PowerShell scripting in Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
caps.latest.revision: 44
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 44
---
# PowerShell scripting in Analysis Services
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] inclut des composants PowerShell qui permettent de parcourir, administrer et interroger des objets serveur, tabulaires et multidimensionnels [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :  
  
-   Le fournisseur **SQLAS**, permettant de naviguer dans la hiérarchie d’objets, est disponible quand vous disposez d’une instance locale d’Analysis Services (le mode serveur n’entre pas en ligne de compte).  
  
-   Le module **SQLASCMDLETS** met à disposition des applets de commande spécifiques aux tâches, telles que la sauvegarde, la restauration, le traitement, ainsi que l’applet de commande généraliste [Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md) qui accepte n’importe quel fichier d’entrée de script ou de requête XMLA ou TMSL (Tabular Model Scripting Language).  
  
 Ces deux composants implémentent un sous-ensemble de l’interface d’administration Analysis Services Management Objects ([Microsoft.AnalysisServices Namespace](http://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx), fournissant des applets de commande pour gérer et créer des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  Tous deux sont des extensions du module racine **SQLPS** pour SQL Server. Pour utiliser des composants PowerShell [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], commencez par importer **SQLPS**. La syntaxe et des exemples de toutes les applets de commande sont accessibles dans [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md).  Pour un exemple d’utilisation des types AMO dans PowerShell afin de créer une base de données tabulaire, voir [AMO PowerShell Example](../../analysis-services/powershell/amo-powershell-example.md).  
  
##  <a name="bkmk_prereq"></a> Étape 1: Installer les composants PowerShell  
 L’approche recommandée pour obtenir les composants PowerShell consiste à installer SQL Server Management Studio (SSMS). Cette approche fournit les modules PowerShell pour SQL Server et le fournisseur de données AMO (Analysis Services Management Objects). SSMS est également un outil permettant de générer facilement des entrées en langages XMLA et TMSL à utiliser dans votre script PowerShell.  
  
 Envisagez d’installer une instance locale d’Analysis Services. Une instance locale permet de naviguer dans la hiérarchie d’objets via le fournisseur **SQLAS** , même si vous l’utilisez jamais pour héberger une base de données.  
  
1.  Pour obtenir la dernière version de Management Studio, accédez à  [Download SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx) (en anglais). La dernière version de Management Studio inclut un AMO mis à jour, qui prend en charge des définitions d’objets de métadonnées tabulaires pour les modèles tabulaires créés au niveau de compatibilité 1200.  
  
2.  Après l’installation de Management Studio, ouvrez une fenêtre PowerShell. Il ne doit nécessairement s’agit d’une fenêtre d’administration.  
  
3.  Entrez `Get-Module -ListAvailable` pour vérifier que les modules **SQLPS** et **SQLASCMDLETS** figurent dans la liste.  
  
     **SQLAS** n’apparaîtra pas tant que vous n’aurez pas également installé une instance locale d’Analysis Services (mode tabulaire ou multidimensionnel).  
  
4.  Entrez `Get-Command -Module sqlascmdlets` pour produire la liste des applets de commande utilisées dans le cadre de l’administration d’Analysis Services.  
  
     **SQLASCMDLETS** sont disponibles même lorsque le fournisseur **SQLAS** est manquant.  
  
    -   [Applet de commande Add-RoleMember](../../analysis-services/powershell/add-rolemember-cmdlet.md)  
  
    -   [Applet de commande Backup-ASDatabase](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)  
  
    -   [Applet de commande Invoke-ASCmd](../../analysis-services/powershell/invoke-ascmd-cmdlet.md) **-inputfile**  
  
    -   [Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)  
  
    -   [Applet de commande Invoke-ProcessCube](../../analysis-services/powershell/invoke-processcube-cmdlet.md)  
  
    -   [Applet de commande Invoke-ProcessDimension](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)  
  
    -   [Applet de commande Invoke-ProcessPartition](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)  
  
    -   [Applet de commande Invoke-ProcessTable](../../analysis-services/powershell/invoke-processtable-cmdlet.md)  
  
    -   [Applet de commande Merge-Partition](../../analysis-services/powershell/merge-partition-cmdlet.md)  
  
    -   [Applet de commande New-RestoreFolder](../../analysis-services/powershell/new-restorefolder-cmdlet.md)  
  
    -   [Applet de commande New-RestoreLocation](../../analysis-services/powershell/new-restorelocation-cmdlet.md)  
  
    -   [Applet de commande Remove-RoleMember](../../analysis-services/powershell/remove-rolemember-cmdlet.md)  
  
    -   [Applet de commande Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)  
  
> [!NOTE]  
>  Windows PowerShell est installé par défaut sur les versions plus récentes des systèmes d’exploitation Windows. La recommandation est 4.0 ou version ultérieure.  
  
## Étape 2 : Charger les composants pour démarrer une session interactive  
 Une fois les composants installés, leur chargement démarre une session interactive.  
  
1.  Entrez `Import-Module sqlps -DisableNameChecking`,  
  
     Charge les composants SQL Server PowerShell, dont ceux pour Analysis Services, et supprime l’avertissement relatif aux noms de verbe non valides.  
  
2.  Entrez `sqlserver:`  
  
     L’invite se présente alors ainsi : **PS SQLSERVER:\\>**.  
  
3.  Si Analysis Services est installé localement, vous pouvez parcourir la hiérarchie d’objets. Entrez `cd sqlas` pour ouvrir le fournisseur **SQLAS**.  
  
4.  Tapez `dir` pour répertorier les instances Analysis Services. Le fournisseur ne fait pas de distinction entre les instances tabulaires et multidimensionnelles.  
  
## Permissions  
 Une session PowerShell interactive s’exécute sous l’identité de sécurité de la personne qui démarre l’application. La plupart des tâches requièrent que la personne ouvrant la session soit également un administrateur du serveur Analysis Services.  
  
 Les tâches PowerShell planifiées doivent être considérées comme des opérations sans assistance. Le compte qui exécute le planificateur, par exemple le service SQL Server Agent, doit très probablement être un administrateur Analysis Services (selon la tâche).  
  
 Dossiers de données locaux, tels que les répertoires de sauvegarde et de données par défaut, sont déjà configurés avec les autorisations de système de fichiers qui permettent à une instance locale de lire et écrire dans ces emplacements.  
  
 L’administration à distance, en particulier quand elle est conduite à partir d’ordinateurs clients sur lesquels Analysis Services est installé, requiert que l’instance de serveur Analysis Services distante exécutant l’action dispose des autorisations du système de fichiers pour lire des fichiers pendant la restauration ou l’écriture de fichiers durant la sauvegarde.  
  
## Fichiers d’entrée de script : / XMLA ASSL ou TMSL  
 Si vous utilisez **invoke-ascmd** pour exécuter le script, le mode serveur, le type de base de données et le niveau de compatibilité déterminent la façon dont vous construisez le script.  
  
-   Les bases de données multidimensionnelles et tabulaires aux niveaux de compatibilité 1050-1103 répondent aux scripts écrits en XMLA (en utilisant les extensions ASSL spécifiques aux définitions d’objets Analysis Services).  
  
-   Les bases de données tabulaires SQL Server 2016 (niveau de compatibilité 1200) répondent aux scripts en langage TMSL.  
  
 Si vous utilisez des versions mixtes de modèles tabulaires sur une même instance SQL Server 2016, n’oubliez pas d’utiliser le script approprié.  
  
> [!NOTE]  
>  Les scripts peuvent être générés dans SQL Server management Studio, puis modifiés en fonction des besoins. Les bases de données tabulaires au niveau de compatibilité 1200 sont écrites en langage TMSL. Toutes les autres sont écrites en XMLA/ASSL. Une instance SQL Server 2016 en mode tabulaire prend en charge les deux langages de script.  
  
## Administration locale et à distance  
 L’administration locale d’Analysis Services via des commandes et scripts PowerShell est plus facile pour deux raisons :  
  
-   Elle permet d’utiliser le fournisseur **SQLAS** pour naviguer dans la hiérarchie d’objets.  
  
-   Les autorisations de fichiers qui permettent à Analysis Services de lire dans des dossiers de données par défaut, par exemple pour des tâches de sauvegarde et de restauration, sont déjà en place, en supposant que vous utilisez ces dossiers comme emplacement de la base de données, et que l’instance du serveur local soit utilisée pour l’opération.  
  
 La gestion d’une instance distante requiert une configuration supplémentaire. Les étapes suivantes supposent que vous avez accompli les étapes d’installation de Management Studio, mais que l’instance de service s’exécute sur un ordinateur distant. Vous devez disposer des droits d’administrateur sur le serveur Analysis Services.  
  
 Analysis Services étant distant, il n’existe aucun fournisseur **SQLAS** pour la navigation locale dans la hiérarchie d’objets. Si vous restaurez des fichiers à partir d’un dossier local plutôt que d’une instance Analysis Services, vous devez créer des partages et accorder au serveur l’accès en lecture aux fichiers.  
  
1.  Ouvrez une fenêtre PowerShell d’administrateur.  
  
2.  Entrez `Set-ExecutionPolicy RemoteUnsigned`  
  
3.  Dans l’Explorateur de fichiers, assurez-vous que tous les dossiers stockant des fichiers de données sont partagés, et que l’instance Analysis Services a des autorisations de lecture pour le contenu.  
  
##  <a name="bkmk_vers"></a> Versions et modes d'Analysis Services pris en charge  
 Le tableau suivant montre la disponibilité de PowerShell Analysis Services dans différents contextes.  
  
|Contexte|Disponibilité des fonctionnalités PowerShell|  
|-------------|-------------------------------------|  
|Bases de données et instances multidimensionnelles|Prise en charge pour l'administration locale et à distance.<br /><br /> La fusion-partition requiert une connexion locale.|  
|Bases de données et instances tabulaires|Pris en charge pour l’administration locale et à distance, à tous les niveaux de compatibilité.<br /><br /> Applets de commande SQLAS pour les modèles tabulaires au niveau de compatibilité 1200, utilisant le langage TMSL (Tabular Model Scripting Language) en JSON au lieu de XMLA.|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour instances et bases de données SharePoint|Prise en charge limitée. Vous pouvez utiliser des connexions HTTP et le fournisseur SQLAS pour afficher des informations d'instance et de base de données.<br /><br /> Toutefois, l'utilisation des applets de commande n'est pas prise en charge. Vous ne pouvez pas utiliser PowerShell Analysis Services pour sauvegarder et restaurer une base de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en mémoire. Vous ne devez pas non plus ajouter ou supprimer des rôles, traiter des données ou exécuter des script XMLA arbitraires.<br /><br /> Pour des besoins de configuration, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint offre une prise en charge intégrée de PowerShell qui est fournie séparément. Pour plus d’informations, consultez [Référence PowerShell pour Power Pivot pour SharePoint](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md).|  
|Connexions natives à des cubes locaux<br /><br /> “Data Source=c:\backup\test.cub”|Non pris en charge.|  
|Connexions HTTP aux fichiers de connexion de modèle sémantique BI (.bism) dans SharePoint<br /><br /> “Data Source=http://server/shared_docs/name.bism”|Non pris en charge.|  
|Connexions intégrées aux bases de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> “Data Source=$Embedded$”|Non pris en charge.|  
|Contexte de serveur local dans les procédures stockées Analysis Services<br /><br /> “Data Source=*”|Non pris en charge.|  
  
## Exemples de tâches d’administration de serveur avec PowerShell  
 **Afficher la liste des propriétés du serveur**  
  
 Les propriétés du serveur sont exposées de plusieurs façons.  Si vous êtes familiarisé avec les propriétés exposées dans msmdsrv. ini ou les pages de propriétés de Management Studio, vous verrez dans les exemples ci-dessous que les propriétés sont en réalité retournées à partir de différents objets.  
  
 Ce script charge un objet de serveur AMO. Si vous avez besoin d’un nom de propriété complet, vous pouvez exécuter ce script pour retourner la liste.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.connect("server-name\instance-name")  
$as.serverproperties  
  
```  
  
 Ce script retourne des propriétés et méthodes au niveau de l’instance. Dans cette liste, vous pouvez lire des valeurs telles que **ServerMode**, **Version**, **ProductName**ou **ProductLevel**.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as | get-member  
  
```  
  
 **Obtenir le mode serveur**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.ServerMode  
```  
  
 **Obtenir le niveau de compatibilité par défaut**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.DefaultCompatibilityLevel  
```  
  
 **Obtenir une liste de bases de données**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.databases  
```  
  
 **Modifier le numéro de port**  
  
 Ce script crée un objet pour une instance nommée, déclare le port, définit le port, met à jour l’instance du serveur, déconnecte l’objet et redémarre le service. En guise d’étape de vérification, vous pouvez ouvrir une nouvelle connexion et retourner le port.  
  
 Vous pouvez également vérifier le port dans le fichier msmdsrv.ini ou dans la page Propriétés générales du serveur dans Management Studio.  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.connect("server-name\instance-name")  
$port = $as.serverproperties['Port']  
$port | select *  
$port.Value = [int]55555  
$as.Update()  
$as.Disconnect()  
restart-service 'MSOLAP$TABULAR'  
$as.connect("server-name\instance-name")  
$port | select *  
  
```  
  
## Voir aussi  
 [Accorder des droits d’administrateur de serveur à une instance Analysis Services](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference [Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;]](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Installer SQL Server PowerShell](../../database-engine/install-windows/install-sql-server-powershell.md)   
 [Gérer les modèles tabulaires à l'aide de PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)   
 [Configurer l’accès HTTP à Analysis Services sur Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md)  
  
  