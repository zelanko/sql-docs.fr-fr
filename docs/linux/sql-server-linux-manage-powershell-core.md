---
title: Gérer SQL Server sur Linux avec PowerShell Core | Microsoft Docs
description: Cet article fournit une vue d’ensemble de l’utilisation de PowerShell Core avec SQL Server sur Linux.
ms.date: 04/22/2019
ms.reviewer: jroth
ms.prod: sql
ms.technology: linux
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
manager: craigg
ms.openlocfilehash: 242e3ab70d41df4d774400034f361b31289d97c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713147"
---
# <a name="manage-sql-server-on-linux-with-powershell-core"></a>Gérer SQL Server sur Linux avec PowerShell Core

Cet article présente [SQL Server PowerShell](../powershell/sql-server-powershell.md) et vous présente quelques exemples sur son utilisation avec PowerShell Core (Core PS) sur macOS et Linux. PowerShell Core est désormais un projet Open Source sur [GitHub](https://github.com/powershell/powershell).

## <a name="cross-platform-editor-options"></a>Options de l’éditeur multiplateforme

Toutes les étapes ci-dessous à PowerShell Core fonctionne dans un terminal régulier, ou vous pouvez les exécuter à partir d’un terminal dans VS Code ou un Studio de données Azure.  VS Code et Azure Data Studio sont disponibles sur macOS et Linux.  Pour plus d’informations sur Azure Data Studio, consultez [ce démarrage rapide](https://docs.microsoft.com/sql/azure-data-studio/quickstart-sql-server).  Vous pouvez également envisager d’utiliser le [extension PowerShell](https://docs.microsoft.com/sql/azure-data-studio/powershell-extension) pour celui-ci.

## <a name="installing-powershell-core"></a>Installation de PowerShell Core

Pour plus d’informations sur l’installation de PowerShell Core sur différentes plateformes prises en charge et expérimentales, consultez les articles suivants :

- [Installation de PowerShell Core sur Windows](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6)
- [Installation de PowerShell Core sur Linux](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [Installation de PowerShell Core sur macOS](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)
- [Installation de PowerShell Core sur ARM](https://docs.microsoft.com/powershell/scripting/install/powershell-core-on-arm?view=powershell-6)

## <a name="install-the-sqlserver-module"></a>Installer le module SqlServer

Le `SqlServer` module est conservé dans le [PowerShell Gallery](https://www.powershellgallery.com/packages/SqlServer/). Lorsque vous travaillez avec SQL Server, vous devez toujours utiliser la version la plus récente du module SqlServer PowerShell.

Pour installer le module SqlServer, ouvrez une session PowerShell Core et exécutez le code suivant :

```powerhsell
Install-Module -Name SqlServer
```

Pour plus d’informations sur la façon d’installer le module SqlServer dans PowerShell Gallery, consultez ce [page](../powershell/download-sql-server-ps-module.md).

## <a name="using-the-sqlserver-module"></a>L’utilisation du module SqlServer

Nous allons commencer en lançant PowerShell Core.  Si vous êtes sur macOS ou Linux, ouvrez un *session Terminal Server* sur votre ordinateur et tapez **pwsh** pour lancer une nouvelle session PowerShell Core.  Sur Windows, utilisez <kbd>Win</kbd>+<kbd>R</kbd>et le type `pwsh` pour lancer une nouvelle session PowerShell Core.

```
pwsh
```

SQL Server fournit un module PowerShell nommé **SqlServer**. Vous pouvez utiliser la **SqlServer** module à importer les composants de SQL Server (fournisseur de SQL Server et applets de commande) dans un environnement de PowerShell ou d’un script.

Copiez et collez la commande suivante à l’invite de PowerShell pour importer le **SqlServer** module dans votre session PowerShell actuelle :

```powershell
Import-Module SqlServer
```

Tapez la commande suivante à l’invite de PowerShell pour vérifier que le **SqlServer** module a été importé correctement :

```powershell
Get-Module -Name SqlServer
```

PowerShell doit afficher des informations similaires à la sortie suivante :

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     21.1.18102 SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>Se connecter à SQL Server et obtenir des informations sur le serveur

Les étapes suivantes utilisent PowerShell Core pour vous connecter à votre instance de SQL Server sur Linux et afficher les deux propriétés de serveur.

Copiez et collez les commandes suivantes à l’invite de PowerShell. Lorsque vous exécutez ces commandes, PowerShell sera :
- Afficher une boîte de dialogue qui vous invite à entrer le nom d’hôte ou l’adresse IP de votre instance
- Afficher le *demande des informations d’identification PowerShell* boîte de dialogue qui vous invite à entrer les informations d’identification. Vous pouvez utiliser votre *nom d’utilisateur SQL* et *mot de passe SQL* pour vous connecter à votre instance de SQL Server sur Linux
- Utilisez le **Get-SqlInstance** applet de commande pour vous connecter à la **Server** et quelques propriétés d’affichage

Si vous le souhaitez, vous pouvez simplement remplacer le `$serverInstance` variable avec l’adresse IP ou le nom d’hôte de votre instance de SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Connect to the Server and return a few properties
Get-SqlInstance -ServerInstance $serverInstance -Credential $credential
# done
```

PowerShell doit afficher des informations similaires à la sortie suivante :

```
Instance Name                   Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------                   -------    ------------ -----------  ------------ ----------------
your_server_instance            14.0.3048  RTM          CU13         Linux        Ubuntu
```

> [!NOTE]
> Si rien n’est affiché pour ces valeurs, la connexion à l’instance de SQL Server cible a échoué très probablement. Assurez-vous que vous pouvez utiliser les mêmes informations de connexion pour vous connecter à partir de SQL Server Management Studio. Passez ensuite en revue les [recommandations en matière de résolution des problèmes de connexion](sql-server-linux-troubleshooting-guide.md#connection).

## <a name="using-the-sql-server-powershell-provider"></a>À l’aide du fournisseur SQL Server PowerShell

Une autre option pour la connexion à votre instance SQL Server consiste à utiliser le [fournisseur PowerShell SQL Server](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider).  L’utilisation du fournisseur vous permet de naviguer d’instance de SQL Server comme dans comme si vous ont été parcours de la structure d’arborescence dans l’Explorateur d’objets, mais à la ligne de commande.  Par défaut, ce fournisseur est présenté sous la forme d’un PSDrive nommé `SQLSERVER:\` que vous pouvez utiliser pour se connecter & accédez des instances de SQL Server à laquelle votre compte de domaine a accès.  Consultez [étapes de Configuration](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps) pour plus d’informations sur la façon de configurer l’authentification d’Active Directory pour SQL Server sur Linux.

Vous pouvez également utiliser l’authentification SQL avec le fournisseur PowerShell SQL Server. Pour ce faire, utilisez le `New-PSDrive` applet de commande pour créer un nouveau PSDrive et de fournir les informations d’identification appropriées pour vous connecter.

Dans l’exemple ci-dessous, vous verrez un exemple montrant comment créer un nouveau PSDrive à l’aide de l’authentification SQL.

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.

New-PSDrive -Name SQLonDocker -PSProvider SqlServer -Root 'SQLSERVER:\SQL\localhost,10002\Default\' -Credential $credential
```

Vous pouvez vérifier que le lecteur a été créé en exécutant la `Get-PSDrive` applet de commande.

```powershell
Get-PSDrive
```

Une fois que vous avez créé votre nouveau PSDrive, vous pouvez commencer à y accéder.

```powershell
dir SQLonDocker:\Databases
```

Voici à quoi peut ressembler la sortie.  Vous remarquerez peut-être cette sortie est similaire à ce que SSMS affiche au niveau du nœud de bases de données.  Il affiche les bases de données utilisateur, mais pas les bases de données système.

```powershell
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2016   Normal      209.63 MB    1.31 MB Simple       130 sa
AdventureWorksDW2012 Normal      167.00 MB   32.47 MB Simple       110 sa
AdventureWorksDW2014 Normal      188.00 MB   78.10 MB Simple       120 sa
AdventureWorksDW2016 Normal      172.00 MB   74.76 MB Simple       130 sa
AdventureWorksDW2017 Normal      208.00 MB   40.57 MB Simple       140 sa
```

Si vous avez besoin de voir toutes les bases de données sur votre instance, une option consiste à utiliser le `Get-SqlDatabase` applet de commande.

## <a name="get-databases"></a>Obtenir les bases de données

Est une applet de commande important de connaître le `Get-SqlDatabase`.  Pour de nombreuses opérations qui impliquent une base de données ou d’objets au sein d’une base de données, le `Get-SqlDatabase` applet de commande peut être utilisé.  Si vous fournissez des valeurs pour les deux le `-ServerInstance` et `-Database` paramètres, que cet objet d’une base de données seront récupérées.  Toutefois, si vous spécifiez uniquement le `-ServerInstance` paramètre, une liste complète de toutes les bases de données sur cette instance sera retournée.

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.

# Connect to the Instance and retrieve all databases
Get-SqlDatabase -ServerInstance ServerB -Credential $credential
```

Voici un exemple de ce qui peut être retourné par la commande Get-SqlDatabase ci-dessus :

```powershell
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2016   Normal      209.63 MB    1.31 MB Simple       130 sa
AdventureWorksDW2012 Normal      167.00 MB   32.47 MB Simple       110 sa
AdventureWorksDW2014 Normal      188.00 MB   78.10 MB Simple       120 sa
AdventureWorksDW2016 Normal      172.00 MB   74.88 MB Simple       130 sa
AdventureWorksDW2017 Normal      208.00 MB   40.63 MB Simple       140 sa
master               Normal        6.00 MB  600.00 KB Simple       140 sa
model                Normal       16.00 MB    5.70 MB Full         140 sa
msdb                 Normal       15.50 MB    1.14 MB Simple       140 sa
tempdb               Normal       16.00 MB    5.49 MB Simple       140 sa

```

## <a name="examine-sql-server-error-logs"></a>Examinez les journaux d’erreurs SQL Server

Les étapes suivantes utilisent PowerShell Core pour examiner l’erreur journaux se connecter sur votre instance de SQL Server sur Linux.

Copiez et collez les commandes suivantes à l’invite de PowerShell. Il peuvent prendre quelques minutes pour s’exécuter. Ces commandes procédez comme suit :
- Afficher une boîte de dialogue qui vous invite à entrer le nom d’hôte ou l’adresse IP de votre instance
- Afficher le *demande des informations d’identification PowerShell* boîte de dialogue qui vous invite à entrer les informations d’identification. Vous pouvez utiliser votre *nom d’utilisateur SQL* et *mot de passe SQL* pour vous connecter à votre instance de SQL Server sur Linux
- Utilisez le **Get-SqlErrorLog** ouvre une applet de commande pour vous connecter à l’instance de SQL Server sur Linux et de récupérer l’erreur depuis **hier**

Si vous le souhaitez, vous pouvez remplacer le `$serverInstance` variable avec l’adresse IP ou le nom d’hôte de votre instance de SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday
# done
```

## <a name="explore-cmdlets-currently-available-in-ps-core"></a>Explorer les applets de commande actuellement disponibles dans PS Core
Même si le module SqlServer actuellement 106 applets de commande disponibles dans Windows PowerShell, 59 uniquement de la 106 sont disponibles dans PSCore. Une liste complète des applets de 59 commande actuellement disponibles est incluse ci-dessous.  Pour obtenir une documentation détaillée de toutes les applets de commande du module SqlServer, consultez SqlServer [référence d’applet de commande](https://docs.microsoft.com/powershell/module/sqlserver/).

La commande suivante vous montrera toutes les applets de commande disponibles sur la version de PowerShell que vous utilisez.

```powershell
Get-Command -Module SqlServer -CommandType Cmdlet |
SORT -Property Noun |
SELECT Name
```

- ConvertFrom-EncodedSqlName
- ConvertTo-EncodedSqlName
- Get-SqlAgent
- Get-SqlAgentJob
- Get-SqlAgentJobHistory
- Get-SqlAgentJobSchedule
- Get-SqlAgentJobStep
- Get-SqlAgentSchedule
- Remove-SqlAvailabilityDatabase
- Resume-SqlAvailabilityDatabase
- Add-SqlAvailabilityDatabase
- Suspend-SqlAvailabilityDatabase
- New-SqlAvailabilityGroup
- Set-SqlAvailabilityGroup
- Remove-SqlAvailabilityGroup
- Switch-SqlAvailabilityGroup
- Join-SqlAvailabilityGroup
- Revoke-SqlAvailabilityGroupCreateAnyDatabase
- Grant-SqlAvailabilityGroupCreateAnyDatabase
- New-SqlAvailabilityGroupListener
- Set-SqlAvailabilityGroupListener
- Add-SqlAvailabilityGroupListenerStaticIp
- Set-SqlAvailabilityReplica
- Remove-SqlAvailabilityReplica
- New-SqlAvailabilityReplica
- Set-SqlAvailabilityReplicaRoleToSecondary
- New-SqlBackupEncryptionOption
- Get-SqlBackupHistory
- Invoke-Sqlcmd
- New-SqlCngColumnMasterKeySettings
- Remove-SqlColumnEncryptionKey
- Get-SqlColumnEncryptionKey
- Remove-SqlColumnEncryptionKeyValue
- Add-SqlColumnEncryptionKeyValue
- Get-SqlColumnMasterKey
- Remove-SqlColumnMasterKey
- New-SqlColumnMasterKey
- Get-SqlCredential
- Set-SqlCredential
- New-SqlCredential
- Remove-SqlCredential
- New-SqlCspColumnMasterKeySettings
- Get-SqlDatabase
- Restore-SqlDatabase
- Backup-SqlDatabase
- Set-SqlErrorLog
- Get-SqlErrorLog
- New-SqlHADREndpoint
- Set-SqlHADREndpoint
- Get-SqlInstance
- Add-SqlLogin
- Remove-SqlLogin
- Get-SqlLogin
- Set-SqlSmartAdmin
- Get-SqlSmartAdmin
- Read-SqlTableData
- Write-SqlTableData
- Read-SqlViewData
- Convert-UrnToPath

## <a name="see-also"></a>Voir aussi
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
