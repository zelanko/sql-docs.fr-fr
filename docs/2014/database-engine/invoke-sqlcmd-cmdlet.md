---
title: Invoke-Sqlcmd (applet de commande) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], Invoke-Sqlcmd
- Cmdlets [SQL Server], Invoke-Sqlcmd
- Invoke-Sqlcmd cmdlet
- sqlcmd utility, PowerShell
ms.assetid: 0c74d21b-84a5-4fa4-be51-90f0f7230044
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: beee2fa576387eadb75ee5ab1bfefcb66453acc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "76928027"
---
# <a name="invoke-sqlcmd-cmdlet"></a>Invoke-Sqlcmd (applet de commande)
  **Invoke-Sqlcmd** est une [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] applet de commande qui exécute des scripts contenant des instructions des[!INCLUDE[tsql](../includes/tsql-md.md)] langages (et XQuery) et des commandes prises en charge par l’utilitaire **sqlcmd** .  
  
## <a name="using-invoke-sqlcmd"></a>Utilisation d'Invoke-Sqlcmd  
 L’applet de commande **Invoke-Sqlcmd** vous permet d’exécuter vos fichiers de script **sqlcmd** dans un environnement Windows PowerShell. La plupart des fonctionnalités offertes avec **sqlcmd** sont également disponibles avec **Invoke-Sqlcmd**.  
  
 Voici un exemple d’appel d’Invoke-Sqlcmd visant à exécuter une requête simple, qui revient à spécifier **sqlcmd** avec les options **-Q** et **-S** :  
  
```powershell
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
 Voici un exemple d’appel d’ **Invoke-Sqlcmd**qui spécifie un fichier d’entrée et dirige la sortie vers un fichier. Cette opération revient à spécifier **sqlcmd** avec les options **-i** et **-o** :  
  
```powershell
Invoke-Sqlcmd -InputFile "C:\MyFolder\TestSQLCmd.sql" | Out-File -FilePath "C:\MyFolder\TestSQLCmd.rpt"  
```  
  
 Cet exemple montre comment utiliser un tableau Windows PowerShell pour transmettre plusieurs variables de script **sqlcmd** à **Invoke-Sqlcmd**. Les caractères « $ » qui identifient les variables de script **sqlcmd** dans l’instruction SELECT ont été placés dans une séquence d’échappement à l’aide du caractère d’échappement PowerShell « ` » (backtick) :  
  
```powershell
$MyArray = "MyVar1 = 'String1'", "MyVar2 = 'String2'"  
Invoke-Sqlcmd -Query "SELECT `$(MyVar1) AS Var1, `$(MyVar2) AS Var2;" -Variable $MyArray  
```  
  
 L’exemple suivant utilise le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour Windows PowerShell pour naviguer jusqu’à une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)], puis utilise l’applet de commande **Get-Item** de Windows PowerShell pour récupérer l’objet serveur SMO pour l’instance et le transmettre à **Invoke-Sqlcmd**:  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\MyInstance  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance (Get-Item .)  
```  
  
 Le paramètre -Query est positionnel et il n'est pas nécessaire de le nommer. Si la première chaîne transmise à **Invoke-Sqlcmd**est sans nom, elle est traitée comme le paramètre -Query.  
  
```powershell
Invoke-Sqlcmd "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance"  
```  
  
## <a name="path-context-in-invoke-sqlcmd"></a>Contexte de chemin d'accès dans Invoke-Sqlcmd  
 Si vous n'utilisez pas le paramètre -Database, le contexte de base de données pour Invoke-Sqlcmd est défini par le chemin d'accès qui est actif lors de l'appel à l'applet de commande.  
  
|Path|Contexte de base de données|  
|----------|----------------------|  
|Commence par un lecteur autre que SQLSERVER:|Base de données par défaut pour l'ID de connexion dans l'instance par défaut sur l'ordinateur local.|  
|SQLSERVER:\SQL|Base de données par défaut pour l'ID de connexion dans l'instance par défaut sur l'ordinateur local.|  
|SQLSERVER:\SQL\ComputerName|Base de données par défaut pour l'ID de connexion dans l'instance par défaut sur l'ordinateur spécifié.|  
|SQLSERVER:\SQL\ComputerName\InstanceName|Base de données par défaut pour l'ID de connexion dans l'instance spécifiée sur l'ordinateur spécifié.|  
|SQLSERVER:\SQL\ComputerName\InstanceName\Databases|Base de données par défaut pour l'ID de connexion dans l'instance spécifiée sur l'ordinateur spécifié.|  
|SQLSERVER:\SQL\ComputerName\InstanceName\Databases\DatabaseName|Base de données spécifiée dans l'instance spécifiée sur l'ordinateur spécifié. Ceci s'applique également aux chemins d'accès plus longs, par exemple un chemin d'accès spécifiant le nœud Tables et colonnes dans une base de données.|  
  
 Par exemple, supposons que votre compte Windows dans l'instance par défaut de l'ordinateur local a pour base de données par défaut master. Les commandes suivantes retournent donc master :  
  
```powershell
Set-Location SQLSERVER:\SQL  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Les commandes suivantes retournent [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]:  
  
```powershell
Set-Location SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Person  
Invoke-Sqlcmd "SELECT DB_NAME() AS DatabaseName;"  
```  
  
 Invoke-Sqlcmd affiche un avertissement lorsqu'il utilise le contexte de base de données du chemin d'accès. Vous pouvez utiliser le paramètre -SuppressProviderContextWarning pour désactiver le message d'avertissement. Vous pouvez utiliser le paramètre -IgnoreProviderContext pour indiquer à Invoke-Sqlcmd de toujours utiliser la base de données par défaut pour la connexion.  
  
## <a name="comparing-invoke-sqlcmd-and-the-sqlcmd-utility"></a>Comparaison d'Invoke-Sqlcmd et de l'utilitaire sqlcmd  
 **Invoke-Sqlcmd** peut être utilisé pour exécuter un grand nombre des scripts qui peuvent être exécutés à l’aide de l’utilitaire **sqlcmd** . Toutefois, **Invoke-Sqlcmd** s’exécute dans un environnement Windows PowerShell différent de l’environnement d’invite de commandes dans lequel **sqlcmd** est exécuté. Le comportement d’ **Invoke-Sqlcmd** a été modifié pour permettre son fonctionnement dans un environnement Windows PowerShell.  
  
 Les commandes **sqlcmd** ne sont pas toutes implémentées dans **Invoke-Sqlcmd**. Les commandes **:!!**, **:connect**, **:error**, **:out**, **:ed**, **:list**, **:listvar**, **:reset**, **:perftrace**et **:serverlist**, par exemple, ne sont pas prises en charge.  
  
 **Invoke-Sqlcmd** n’initialise pas l’environnement **sqlcmd** ou les variables de script telles que SQLCMDDBNAME ou SQLCMDWORKSTATION.  
  
 **Invoke-Sqlcmd** n’affiche pas les messages, tels que la sortie des instructions print, sauf si vous spécifiez le paramètre commun Windows PowerShell **-Verbose** . Par exemple :  
  
```powershell
Invoke-Sqlcmd -Query "PRINT N'abc';" -Verbose  
```  
  
 Tous les paramètres **sqlcmd** ne sont pas nécessaires dans un environnement PowerShell. Par exemple, Windows PowerShell met en forme toutes les sorties des applets de commande. Les paramètres **sqlcmd** spécifiant les options de mise en forme ne sont donc pas implémentés dans **Invoke-Sqlcmd**. Le tableau suivant montre la relation entre les paramètres **Invoke-Sqlcmd** et les options **sqlcmd** :  
  
|Description|Option sqlcmd|Paramètre Invoke-Sqlcmd|  
|-----------------|-------------------|------------------------------|  
|Serveur et le nom de l'instance.|-S|-ServerInstance|  
|Base de données initiale à utiliser.|-d|-Database|  
|Exécuter la requête spécifiée et quitter.|-Q|-Query|  
|
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-U|-Username|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Mot de passe d’authentification.|-P|-Mot de passe|  
|Définition de variable.|-v|-Variable|  
|Intervalle de délai de requête.|-t|-QueryTimeout|  
|Arrêter l'exécution en cas d'erreur|-b|-AbortOnError|  
|Connexion administrateur dédiée.|-A|-DedicatedAdministratorConnection|  
|Désactiver les commandes interactives, le script de démarrage et les variables d'environnement.|-X|-DisableCommands|  
|Désactiver la substitution de variable.|-X|-DisableVariables|  
|Niveau de gravité minimal pour le rapport.|-v|-SeverityLevel|  
|Niveau d'erreur minimal pour le rapport.|-M|-ErrorLevel|  
|Intervalle de délai de connexion.|-l|-ConnectionTimeout|  
|Nom d'hôte.|-H|-HostName|  
|Modifier le mot de passe et quitter.|-Z|-NewPassword|  
|Fichier d'entrée contenant une requête|-i|-InputFile|  
|Longueur maximale de la sortie de type caractère|-w|-MaxCharLength|  
|Longueur maximale de la sortie de type binaire|-w|-MaxBinaryLength|  
|Établir la connexion à l'aide du chiffrement SSL|Aucun paramètre|-EncryptConnection|  
|Afficher les erreurs|Aucun paramètre|-OutputSqlErrors|  
|Sortie des messages vers stderr|-r|Aucun paramètre|  
|Utiliser les paramètres régionaux du client|-R|Aucun paramètre|  
|Exécuter la requête spécifiée et rester actif|-q|Aucun paramètre|  
|Page de codes à utiliser pour les données de sortie|-f|Aucun paramètre|  
|Modifier un mot de passe et rester actif|-Z|Aucun paramètre|  
|Taille du paquet|-a|Aucun paramètre|  
|Séparateur de colonnes|-s|Aucun paramètre|  
|En-têtes de sortie des contrôles|-h|Aucun paramètre|  
|Spécifier des caractères de contrôle|-k|Aucun paramètre|  
|Largeur d'écran de longueur fixe|-y|Aucun paramètre|  
|Largeur d'écran de longueur variable|-y|Aucun paramètre|  
|Entrée d'écho|-e|Aucun paramètre|  
|Activer les identificateurs entre guillemets|-I|Aucun paramètre|  
|Supprimer des espaces de fin|-w|Aucun paramètre|  
|Instances de liste|-l|Aucun paramètre|  
|Mettre en forme la sortie en Unicode|-U|Aucun paramètre|  
|Imprimer les statistiques|-p|Aucun paramètre|  
|Fin de la commande|-c|Aucun paramètre|  
|Connexion avec l'authentification Windows|-E|Aucun paramètre|  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser les applets de commande Moteur de base de données](../../2014/database-engine/use-the-database-engine-cmdlets.md)   
 [Utilitaire sqlcmd](../tools/sqlcmd-utility.md)   
 [Utiliser l'utilitaire sqlcmd](../relational-databases/scripting/sqlcmd-use-the-utility.md)  
