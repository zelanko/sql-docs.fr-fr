---
title: Invoke-Sqlcmd (applet de commande) | Microsoft Docs
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PowerShell [SQL Server], Invoke-Sqlcmd
- Cmdlets [SQL Server], Invoke-Sqlcmd
- Invoke-Sqlcmd cmdlet
- sqlcmd utility, PowerShell
ms.assetid: 0c74d21b-84a5-4fa4-be51-90f0f7230044
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 679625527f4f29d086b50e2291af4cff14b74d3e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="invoke-sqlcmd-cmdlet"></a>Invoke-Sqlcmd (applet de commande)
  **Invoke-Sqlcmd** est une applet de commande [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui exécute des scripts contenant des instructions des langages ([!INCLUDE[tsql](../includes/tsql-md.md)] et XQuery) ainsi que les commandes prises en charge par l’utilitaire **sqlcmd** .  
  
## <a name="using-invoke-sqlcmd"></a>Utilisation d'Invoke-Sqlcmd  
 L’applet de commande **Invoke-Sqlcmd** vous permet d’exécuter vos fichiers de script **sqlcmd** dans un environnement Windows PowerShell. La plupart des fonctionnalités offertes avec **sqlcmd** sont également disponibles avec **Invoke-Sqlcmd**.  
  
 Voici un exemple d’appel d’Invoke-Sqlcmd visant à exécuter une requête simple, qui revient à spécifier **sqlcmd** avec les options **-Q** et **-S** :  
  
```  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
 Voici un exemple d’appel d’ **Invoke-Sqlcmd**qui spécifie un fichier d’entrée et dirige la sortie vers un fichier. Cette opération revient à spécifier **sqlcmd** avec les options **-i** et **-o** :  
  
```  
Invoke-Sqlcmd -InputFile "C:\MyFolder\TestSQLCmd.sql" | Out-File -filePath "C:\MyFolder\TestSQLCmd.rpt"  
```  
  
 Cet exemple montre comment utiliser un tableau Windows PowerShell pour transmettre plusieurs variables de script **sqlcmd** à **Invoke-Sqlcmd**. Les caractères « $ » qui identifient les variables de script **sqlcmd** dans l’instruction SELECT ont été placés dans une séquence d’échappement à l’aide du caractère d’échappement PowerShell « ` » (backtick) :  
  
```  
$MyArray = "MyVar1 = 'String1'", "MyVar2 = 'String2'"  
Invoke-Sqlcmd -Query "SELECT `$(MyVar1) AS Var1, `$(MyVar2) AS Var2;" -Variable $MyArray  
```  
  
 L’exemple suivant utilise le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour Windows PowerShell pour naviguer jusqu’à une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)], puis utilise l’applet de commande **Get-Item** de Windows PowerShell pour récupérer l’objet serveur SMO pour l’instance et le transmettre à **Invoke-Sqlcmd**:  
  
```  
Set-Location SQLSERVER:\SQL\MyComputer\MyInstance  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance (Get-Item .)  
```  
  
 Le paramètre -Query est positionnel et il n'est pas nécessaire de le nommer. Si la première chaîne transmise à **Invoke-Sqlcmd**est sans nom, elle est traitée comme le paramètre -Query.  
  
```  
Invoke-Sqlcmd "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
## <a name="path-context-in-invoke-sqlcmd"></a>Contexte de chemin d'accès dans Invoke-Sqlcmd  
 Si vous n'utilisez pas le paramètre -Database, le contexte de base de données pour Invoke-Sqlcmd est défini par le chemin d'accès qui est actif lors de l'appel à l'applet de commande.  
  
|Chemin d'accès|Contexte de base de données|  
|----------|----------------------|  
|Commence par un lecteur autre que SQLSERVER:|Base de données par défaut pour l'ID de connexion dans l'instance par défaut sur l'ordinateur local.|  
|SQLSERVER:\SQL|Base de données par défaut pour l'ID de connexion dans l'instance par défaut sur l'ordinateur local.|  
|SQLSERVER:\SQL\ComputerName|Base de données par défaut pour l'ID de connexion dans l'instance par défaut sur l'ordinateur spécifié.|  
|SQLSERVER:\SQL\ComputerName\InstanceName|Base de données par défaut pour l'ID de connexion dans l'instance spécifiée sur l'ordinateur spécifié.|  
|SQLSERVER:\SQL\ComputerName\InstanceName\Databases|Base de données par défaut pour l'ID de connexion dans l'instance spécifiée sur l'ordinateur spécifié.|  
|SQLSERVER:\SQL\ComputerName\InstanceName\Databases\DatabaseName|Base de données spécifiée dans l'instance spécifiée sur l'ordinateur spécifié. Ceci s'applique également aux chemins d'accès plus longs, par exemple un chemin d'accès spécifiant le nœud Tables et colonnes dans une base de données.|  
  
 Par exemple, supposons que votre compte Windows dans l'instance par défaut de l'ordinateur local a pour base de données par défaut master. Les commandes suivantes retournent donc master :  
  
```  
Set-Location SQLSERVER:\SQL  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Les commandes suivantes retournent [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]:  
  
```  
Set-Location SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Person  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Invoke-Sqlcmd affiche un avertissement lorsqu'il utilise le contexte de base de données du chemin d'accès. Vous pouvez utiliser le paramètre -SuppressProviderContextWarning pour désactiver le message d'avertissement. Vous pouvez utiliser le paramètre -IgnoreProviderContext pour indiquer à Invoke-Sqlcmd de toujours utiliser la base de données par défaut pour la connexion.  
  
## <a name="comparing-invoke-sqlcmd-and-the-sqlcmd-utility"></a>Comparaison d'Invoke-Sqlcmd et de l'utilitaire sqlcmd  
 **Invoke-Sqlcmd** peut être utilisé pour exécuter un grand nombre des scripts pris en charge par l’utilitaire **sqlcmd** . Toutefois, **Invoke-Sqlcmd** s’exécute dans un environnement Windows PowerShell différent de l’environnement d’invite de commandes dans lequel **sqlcmd** est exécuté. Le comportement d’ **Invoke-Sqlcmd** a été modifié pour permettre son fonctionnement dans un environnement Windows PowerShell.  
  
 Les commandes **sqlcmd** ne sont pas toutes implémentées dans **Invoke-Sqlcmd**. Les commandes **:!!**, **:connect**, **:error**, **:out**, **:ed**, **:list**, **:listvar**, **:reset**, **:perftrace**et **:serverlist**, par exemple, ne sont pas prises en charge.  
  
 **Invoke-Sqlcmd** n’initialise pas l’environnement **sqlcmd** ou les variables de script telles que SQLCMDDBNAME ou SQLCMDWORKSTATION.  
  
 **Invoke-Sqlcmd** n’affiche pas les messages, tels que la sortie des instructions PRINT, sauf si vous spécifiez le paramètre commun Windows PowerShell **-Verbose** . Par exemple :  
  
```  
Invoke-Sqlcmd -Query "PRINT N'abc';" -Verbose  
```  
  
 Tous les paramètres **sqlcmd** ne sont pas nécessaires dans un environnement PowerShell. Par exemple, Windows PowerShell met en forme toutes les sorties des applets de commande. Les paramètres **sqlcmd** spécifiant les options de mise en forme ne sont donc pas implémentés dans **Invoke-Sqlcmd**. Le tableau suivant illustre la relation entre les paramètres **Invoke-Sqlcmd** et les options **sqlcmd** :  
  
|Description|Option sqlcmd|Paramètre Invoke-Sqlcmd|  
|-----------------|-------------------|------------------------------|  
|Serveur et le nom de l'instance.|-S|-ServerInstance|  
|Base de données initiale à utiliser.|-d|-Database|  
|Exécuter la requête spécifiée et quitter.|-Q|-Query|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-U|-Username|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-P|-Password|  
|Définition de variable.|-v|-Variable|  
|Intervalle de délai de requête.|-t|-QueryTimeout|  
|Arrêter l'exécution en cas d'erreur|-b|-AbortOnError|  
|Connexion administrateur dédiée.|-A|-DedicatedAdministratorConnection|  
|Désactiver les commandes interactives, le script de démarrage et les variables d'environnement.|-X|-DisableCommands|  
|Désactiver la substitution de variable.|-X|-DisableVariables|  
|Niveau de gravité minimal pour le rapport.|-v|-SeverityLevel|  
|Niveau d'erreur minimal pour le rapport.|-m|-ErrorLevel|  
|Intervalle de délai de connexion.|-l|-ConnectionTimeout|  
|Nom d'hôte.|-H|-HostName|  
|Modifier le mot de passe et quitter.|-Z|-NewPassword|  
|Fichier d'entrée contenant une requête|-i|-InputFile|  
|Longueur maximale de la sortie de type caractère|-w|-MaxCharLength|  
|Longueur maximale de la sortie de type binaire|-w|-MaxBinaryLength|  
|Établir la connexion à l'aide du chiffrement SSL|Aucun paramètre|-EncryptConnection|  
|Afficher les erreurs|Aucun paramètre|-OutputSqlErrors|  
|Sortie des messages vers stderr|-r|Aucun paramètre|  
|Utiliser les paramètres régionaux du client|-r|Aucun paramètre|  
|Exécuter la requête spécifiée et rester actif|-Q|Aucun paramètre|  
|Page de codes à utiliser pour les données de sortie|-f|Aucun paramètre|  
|Modifier un mot de passe et rester actif|-Z|Aucun paramètre|  
|Taille du paquet|-A|Aucun paramètre|  
|Séparateur de colonnes|-S|Aucun paramètre|  
|En-têtes de sortie des contrôles|-H|Aucun paramètre|  
|Spécifier des caractères de contrôle|-k|Aucun paramètre|  
|Largeur d'écran de longueur fixe|-Y|Aucun paramètre|  
|Largeur d'écran de longueur variable|-Y|Aucun paramètre|  
|Entrée d'écho|-e|Aucun paramètre|  
|Activer les identificateurs entre guillemets|-i|Aucun paramètre|  
|Supprimer des espaces de fin|-w|Aucun paramètre|  
|Instances de liste|-l|Aucun paramètre|  
|Mettre en forme la sortie en Unicode|-U|Aucun paramètre|  
|Imprimer les statistiques|-P|Aucun paramètre|  
|Fin de la commande|-c|Aucun paramètre|  
|Connexion avec l'authentification Windows|-e|Aucun paramètre|  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser les applets de commande du Moteur de base de données](../relational-databases/scripting/use-the-database-engine-cmdlets.md)   
 [Utilitaire sqlcmd](../tools/sqlcmd-utility.md)   
 [Utiliser l'utilitaire sqlcmd](../relational-databases/scripting/sqlcmd-use-the-utility.md)  
  
  

