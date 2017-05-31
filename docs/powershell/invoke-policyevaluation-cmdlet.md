---
title: Invoke-PolicyEvaluation (applet de commande) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, Invoke-PolicyEvaluation
- Policy-Based Management, PowerShell
- Invoke-PolicyEvaluation cmdlet
- Cmdlets [SQL Server], Invoke-PolicyEvaluation
- PowerShell [SQL Server], Invoke-PolicyEvaluation
ms.assetid: 3e6d4f5a-59b7-4203-b95a-f7e692c0f131
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f5adc3571b07e3613514525f286241add73af1a8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="invoke-policyevaluation-cmdlet"></a>Invoke-PolicyEvaluation (applet de commande)
  **Invoke-PolicyEvaluation** est une applet de commande [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui indique si un jeu cible d’objets SQL Server est conforme ou non aux conditions spécifiées dans une ou plusieurs stratégies de gestion basée sur des stratégies.  
  
## <a name="using-invoke-policyevaluation"></a>Utilisation d'Invoke-PolicyEvaluation  
 **Invoke-PolicyEvaluation** évalue une ou plusieurs stratégies par rapport à un jeu d’objets SQL Server appelé « jeu cible ». Le jeu d'objets cibles provient d'un serveur cible. Chaque stratégie définit des conditions qui représentent les états autorisés pour les objets cibles. Par exemple, la stratégie **Trustworthy Database** stipule que la propriété de base de données TRUSTWORTHY doit avoir la valeur OFF.  
  
 Le paramètre **-AdHocPolicyEvaluationMode** spécifie les actions effectuées :  
  
 Vérifier  
 Indique l'état de conformité des objets cibles à l'aide des informations d'identification de votre connexion actuelle. Ne reconfigure pas d'objets. Il s'agit du paramètre par défaut.  
  
 CheckSqlScriptAsProxy  
 Indique l’état de conformité des objets cibles à l’aide des informations d’identification de la connexion proxy **##MS_PolicyTSQLExecutionLogin##** . Ne reconfigure pas d'objets.  
  
 Configurer  
 Indique l'état de conformité des objets cibles à l'aide des informations d'identification de votre connexion actuelle. Reconfigure toutes les options définissables et déterministes qui ne sont pas conformes aux stratégies.  
  
## <a name="specifying-polices"></a>Spécification de stratégies  
 La façon dont vous spécifiez une stratégie dépend de l'emplacement de stockage de la stratégie. Les stratégies peuvent être stockées dans deux formats :  
  
-   Elles peuvent être constituées d'objets stockés dans un magasin de stratégies, par exemple une instance du moteur de base de données. Vous pouvez utiliser le dossier SQLSERVER:\SQLPolicy pour spécifier l'emplacement de stratégies dans un magasin de stratégies. Vous pouvez utiliser des applets de commande Windows PowerShell pour filtrer les stratégies d'entrée selon leurs propriétés, par exemple Where-Object pour appliquer un filtre sur la catégorie de la stratégie ou Get-Item pour appliquer un filtre sur le nom de la stratégie.  
  
-   Elles peuvent être exportées en tant que fichiers XML. Vous pouvez utiliser un lecteur du système de fichiers, tel que D:, pour spécifier l'emplacement des fichiers XML. Vous pouvez utiliser des applets de commande Windows PowerShell tels que Where-Object pour filtrer les stratégies selon les propriétés du fichier, par exemple le nom du fichier.  
  
 Si les stratégies sont stockées dans un magasin de stratégies, vous devez passer un jeu de PSObjects pointant vers les stratégies à évaluer. Pour ce faire, dirigez la sortie d’une applet de commande, telle que Get-Item, vers **Invoke-PolicyEvaluation**. Inutile de spécifier le paramètre **-Policy** . Par exemple, si vous avez importé les stratégies Recommandations de Microsoft dans votre instance du moteur de base de données, cette commande évalue la stratégie **État de la base de données** :  
  
```  
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Get-Item "Database Status" | Invoke-PolicyEvaluation -TargetServerName "MYCOMPUTER"  
```  
  
 Cet exemple montre comment utiliser Where-Object pour filtrer plusieurs stratégies d’un magasin de stratégies, en fonction de leur propriété **PolicyCategory** . Les objets de la sortie dirigée de **Where-Object** sont consommés par **Invoke-PolicyEvaluation**.  
  
```  
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
gci | Where-Object {$_.PolicyCategory -eq "Microsoft Best Practices: Maintenance"} | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
 Si les stratégies sont stockées sous la forme de fichiers XML, vous devez utiliser le paramètre **-Policy** pour fournir le chemin et le nom de chaque stratégie. Si vous ne spécifiez pas de chemin dans le paramètre **-Policy** , **Invoke-PolicyEvaluation** utilise le paramètre actuel du chemin **sqlps** . Par exemple, cette commande évalue l'une des stratégies Recommandations de Microsoft installées avec SQL Server par rapport à la base de données par défaut pour votre connexion :  
  
```  
Invoke-PolicyEvaluation -Policy "C:\Program Files\Microsoft SQL Server\130\Tools\Policies\DatabaseEngine\1033\Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 Cette commande a le même effet, sauf qu’elle utilise le chemin d’accès **sqlps** courant pour établir l’emplacement du fichier XML de la stratégie :  
  
```  
sl "C:\Program Files\Microsoft SQL Server\130\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 Cet exemple montre comment utiliser l’applet de commande **Get-ChildItem** pour récupérer plusieurs fichiers XML de stratégie et diriger les objets vers **Invoke-PolicyEvaluation**:  
  
```  
sl "C:\Program Files\Microsoft SQL Server\130\Tools\Policies\DatabaseEngine\1033"  
gci "Database Status.xml", "Trustworthy Database.xml" | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
## <a name="specifying-the-target-set"></a>Spécification du jeu de cibles  
 Utilisez trois paramètres pour spécifier le jeu d'objets cibles :  
  
-   **-TargetServerName** spécifie l’instance de SQL Server contenant les objets cibles. Vous pouvez spécifier les informations dans une chaîne qui utilise le format défini pour la propriété ConnectionString de la classe <xref:System.Data.SqlClient.SqlConnection>. Vous pouvez utiliser la classe <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour générer une chaîne de connexion correctement mise en forme. Vous pouvez également créer un objet <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> et le passer à **-TargetServer**. Si vous spécifiez une chaîne qui ne contient que le nom du serveur, **Invoke-PolicyEvaluation** utilise l’authentification Windows pour se connecter au serveur.  
  
-   **-TargetObjects** accepte un objet ou un tableau d’objets représentant les objets SQL Server dans le jeu cible. Par exemple, vous pouvez créer un tableau d’objets de classe <xref:Microsoft.SqlServer.Management.Smo.Database> à passer à **-TargetObjects**.  
  
-   **-TargetExpressions** accepte une chaîne contenant une expression de requête qui spécifie les objets dans le jeu cible. L'expression de requête se présente sous la forme de nœuds séparés par le caractère « / ». Chaque nœud se présente sous la forme ObjectType[Filter]. Le type d'objet est l'un des objets dans une hiérarchie d'objets SMO (SQL Server Management Objects). Le filtre est une expression qui filtre les objets au niveau de ce nœud. Pour plus d’informations, consultez [Expressions de requête et noms URN](../powershell/query-expressions-and-uniform-resource-names.md).  
  
 Spécifiez **-TargetObjects** ou **-TargetExpression**, mais pas les deux.  
  
 Cet exemple utilise un objet Sfc.SqlStoreConnection pour spécifier le serveur cible :  
  
```  
sl "C:\Program Files\Microsoft SQL Server\130\Tools\Policies\DatabaseEngine\1033"  
$conn = New-Object Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection("server='MYCOMPUTER';Trusted_Connection=True")  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName $conn  
```  
  
 Cet exemple utilise **-TargetExpression** pour identifier la base de données à évaluer :  
  
```  
sl "C:\Program Files\Microsoft SQL Server\130\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MyComputer" -TargetExpression "Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']"  
```  
  
## <a name="evaluating-analysis-services-policies"></a>Évaluation de stratégies Analysis Services  
 Pour évaluer des stratégies par rapport à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous devez charger et inscrire un assembly dans PowerShell, créer une variable avec un objet de connexion Analysis Services, puis transmettre la variable au paramètre **-TargetObject** . Cet exemple montre comment évaluer la stratégie de configuration de la surface d'exposition des Recommandations pour [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:  
  
```  
sl "C:\Program Files\Microsoft SQL Server\130\Tools\Policies\AnalysisServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.AnalysisServices")  
$SSASsvr = new-object Microsoft.AnalysisServices.Server  
$SSASsvr.Connect("Data Source=Localhost")  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Analysis Services Features.xml" -TargetObject $SSASsvr  
```  
  
## <a name="evaluating-reporting-services-policies"></a>Évaluation de stratégies Reporting Services  
 Pour évaluer des stratégies [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , vous devez charger et inscrire un assembly dans PowerShell, créer une variable avec un objet de connexion [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , puis transmettre la variable au paramètre **-TargetObject** . Cet exemple montre comment évaluer la stratégie de configuration de la surface d'exposition des Recommandations pour [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:  
  
```  
sl "C:\Program Files\Microsoft SQL Server\130\Tools\Policies\ReportingServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Dmf.Adapters")  
$SSRSsvr = new-object Microsoft.SqlServer.Management.Adapters.RSContainer('MyComputer')  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Reporting Services 2008 Features.xml" -TargetObject $SSRSsvr  
```  
  
## <a name="formatting-output"></a>Mise en forme de la sortie  
 Par défaut, la sortie de **Invoke-PolicyEvaluation** s’affiche dans la fenêtre d’invite de commandes sous la forme d’un rapport concis au format explicite. Vous pouvez utiliser le paramètre **-OutputXML** pour que l’applet de commande génère plutôt un rapport détaillé sous la forme d’un fichier XML. **Invoke-PolicyEvaluation** utilise le schéma SML-IF (Systems Modeling Language Interchange Format) pour que le fichier soit lisible par les lecteurs SML-IF.  
  
```  
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Invoke-PolicyEvaluation -Policy "Datbase Status" -TargetServer "MYCOMPUTER" -OutputXML > C:\MyReports\DatabaseStatusReport.xml  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser les applets de commande du Moteur de base de données](../relational-databases/scripting/use-the-database-engine-cmdlets.md)   
  
  
