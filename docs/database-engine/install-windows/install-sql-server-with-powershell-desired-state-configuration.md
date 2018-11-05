---
title: Installer SQL Server avec la configuration d’état souhaité PowerShell | Microsoft Docs
description: Découvrez comment installer SQL Server avec la configuration d’état souhaité PowerShell (DSC).
ms.custom: ''
ms.date: 10/26/2018
ms.devlang: PowerShell
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
author: randomnote1
ms.author: dareist
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 16d425d8eb66a950f432fa3ef9c68a8e68a78d22
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148477"
---
# <a name="install-sql-server-with-powershell-desired-state-configuration"></a>Installer SQL Server avec la configuration d’état souhaité PowerShell

À qui n’est-il pas arrivé de cliquer machinalement sur les boutons bien connus de l’Assistant d’installation SQL Server et d’y entrer les informations habituelles sans trop réfléchir ? Une fois l’installation terminée, vous vous rendez compte que vous avez oublié de spécifier le groupe DBA dans le rôle sysadmin. Vous allez donc perdre un temps précieux à passer en mode mono-utilisateur, à ajouter des utilisateurs ou des groupes, puis à revenir en mode multi-utilisateur et à effectuer des tests. Le pire, c’est que vous n’avez même plus confiance en l’installation que vous venez d’effectuer. « Ai-je oublié autre chose ? » Cela m’est arrivé bien des fois.

Passez à la [Configuration d’état souhaité (DSC) PowerShell](https://docs.microsoft.com/powershell/dsc/overview). À l’aide de DSC, je peux créer un modèle de configuration qui peut être réutilisé sur plusieurs centaines voire milliers de serveurs. En fonction de la build, j’aurai peut-être quelques paramètres d’installation à ajuster, mais rien de très important, car je peux conserver tous les paramètres standard. Le plus beau dans tout ça, c’est que je ne peux plus oublier d’entrer un paramètre important après avoir passé une nuit blanche à m’occuper de mes enfants.

Dans cet article, je vais explorer la configuration initiale d’une instance autonome de SQL Server 2017 sur Windows Server 2016 à l’aide de la ressource SqlServerDsc DSC. Si vous connaissez déjà DSC, cela vous sera utile parce que je ne vais pas aborder le fonctionnement de DSC.

Pour cette procédure pas à pas, les éléments suivants sont nécessaires :

- Un ordinateur exécutant Windows Server 2016
- Un support d’installation de SQL Server 2017
- La ressource SqlServerDsc de DSC (au moment où j’écris cet article, la version actuelle est 10.0.0.0)

## <a name="prerequisites"></a>Prérequis

Dans la plupart des cas, DSC sert à gérer les prérequis. Toutefois, pour cette démonstration, je vais gérer les prérequis manuellement.

## <a name="install-the-sqlserverdsc-dsc-resource"></a>Installer la ressource SqlServerDsc de DSC

La ressource [SqlServerDsc](https://www.powershellgallery.com/packages/SqlServerDsc) de DSC peut être téléchargée à partir de [PowerShell Gallery](https://www.powershellgallery.com/), à l’aide de l’applet de commande [Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module?view=powershell-5.1). _Remarque : Pour installer le module, vérifiez que PowerShell est exécuté « en tant qu’administrateur »._

```PowerShell
Install-Module -Name SqlServerDsc
```

Obtenir le support d’installation SQL Server 2017 Téléchargez le support d’installation SQL Server 2017 sur le serveur. J’ai téléchargé SQL Server 2017 Enterprise à partir de mon abonnement Visual Studio et j’ai copié l’image ISO à l’emplacement suivant : « C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso ».

Maintenant, l’image ISO doit être extraite dans un répertoire.

```PowerShell
New-Item -Path C:\SQL2017 -ItemType Directory
$mountResult = Mount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso' -PassThru
$volumeInfo = $mountResult | Get-Volume
$driveInfo = Get-PSDrive -Name $volumeInfo.DriveLetter
Copy-Item -Path ( Join-Path -Path $driveInfo.Root -ChildPath '*' ) -Destination C:\SQL2017\ -Recurse
Dismount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso'
```

## <a name="create-the-configuration"></a>Créer la configuration

### <a name="configuration"></a>Configuration

Créez la fonction de configuration qui sera appelée pour générer le ou les documents [MOF (Managed Object Format)](https://docs.microsoft.com/windows/desktop/WmiSdk/managed-object-format--mof-).

```PowerShell
Configuration SQLInstall
{...}
```

### <a name="modules"></a>Modules

Importez les modules dans la session active. Ces modules indiquent au document de configuration comment générer des documents MOF, et indique au moteur DSC comment appliquer les documents MOF au serveur.

```PowerShell
Import-DscResource -ModuleName SqlServerDsc
```

### <a name="resources"></a>Ressources

#### <a name="net-framework"></a>.NET Framework

SQL Server s’appuie sur .NET Framework. Nous devons donc l’installer avant d’installer SQL Server. La ressource WindowsFeature est utilisée pour installer la fonctionnalité Windows Net-Framework-45-Core.

```PowerShell
WindowsFeature 'NetFramework45'
{
     Name = 'Net-Framework-45-Core'
     Ensure = 'Present'
}
```

#### <a name="sqlsetup"></a>SqlSetup

La ressource SqlSetup est utilisée pour indiquer à DSC comment installer SQL Server. Les paramètres nécessaires à une installation de base sont les suivants :

- **InstanceName** : nom de l’instance. Utilisez MSSQLSERVER pour une instance par défaut.
- **Features** : fonctionnalités à installer. Dans cet exemple, j’installe uniquement la fonctionnalité SQLEngine.
- **SourcePath** : chemin du support d’installation SQL. Dans cet exemple, j’ai stocké le support d’installation SQL dans « C:\SQL2017 ». Vous pouvez utiliser un partage réseau pour réduire l’espace utilisé sur le serveur.
- **SQLSysAdminAccounts** : utilisateurs ou groupes qui doivent être membres du rôle sysadmin. Dans cet exemple, je vais accorder un accès sysadmin au groupe Administrateurs local. _Remarque : Cette configuration n’est pas recommandée dans un environnement hautement sécurisé._

La liste complète et la description des paramètres SqlSetup sont disponibles dans le [dépôt GitHub SqlServerDsc](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlsetup).

La ressource SqlSetup est bizarre, car elle installe uniquement SQL, sans conserver les paramètres appliqués. Par exemple, si des SQLSysAdminAccount sont spécifiés au moment de l’installation, un administrateur peut ajouter ou supprimer des connexions dans le rôle sysadmin, sans que la ressource SqlSetup ne s’en préoccupe. Si vous désirez que DSC applique l’appartenance au rôle sysadmin, la ressource [SqlServerRole](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlserverrole) doit être utilisée.

#### <a name="complete-configuration"></a>Configurer

```PowerShell
Configuration SQLInstall
{
     Import-DscResource -ModuleName SqlServerDsc

     node localhost
     {
          WindowsFeature 'NetFramework45'
          {
               Name   = 'NET-Framework-45-Core'
               Ensure = 'Present'
          }

          SqlSetup 'InstallDefaultInstance'
          {
               InstanceName        = 'MSSQLSERVER'
               Features            = 'SQLENGINE'
               SourcePath          = 'C:\SQL2017'
               SQLSysAdminAccounts = @('Administrators')
               DependsOn           = '[WindowsFeature]NetFramework45'
          }
     }
}
```

## <a name="build-and-deploy"></a>Créer et déployer

### <a name="compile-the-configuration"></a>Compiler la configuration

« Dot sourcez » le script de configuration :

```PowerShell
. .\SQLInstallConfiguration.ps1
```

Exécutez la fonction de configuration :

```PowerShell
SQLInstall
```

Un répertoire est créé dans le répertoire de travail « SQLInstall » pour contenir le fichier « localhost.mof ». Si vous regardez le contenu du fichier MOF, vous verrez la configuration DSC compilée.

### <a name="deploy-the-configuration"></a>Déployer la configuration

Pour démarrer le déploiement DSC de SQL Server, appelez l’applet de commande Start-DscConfiguration. Les paramètres fournis à l’applet de commande sont les suivants :

- **Path** : chemin du dossier contenant les documents MOF à déployer (par exemple « C:\SQLInstall »)
- **Wait** : attend la fin de la tâche de configuration.
- **Force** : remplace toutes les configurations DSC existantes.
- **Verbose** : affiche la sortie détaillée. Utile lors du premier envoi (push) d’une configuration pour faciliter le dépannage.

```PowerShell
Start-DscConfiguration -Path C:\SQLInstall -Wait -Force -Verbose
```

Lorsque la configuration est appliquée, la sortie détaillée affiche des informations sur les événements actuels et vous donne ce sentiment rassurant que quelque chose se passe. Tant qu’aucune erreur n’est signalée (en rouge), si le message « Operation 'Invoke CimMethod' complete » s’affiche à l’écran, SQL a bien été installé.

## <a name="validate-installation"></a>Valider l’installation

### <a name="dsc"></a>DSC

Les applets de commande [Test-DscConfiguration](https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration) peuvent être utilisées pour déterminer si l’état actuel du serveur (dans ce cas, l’installation SQL) correspond à l’état souhaité. Le résultat de Test-DscConfiguration doit être « True ».

```PowerShell
PS C:\> Test-DscConfiguration
True
```

### <a name="services"></a>Services

Les services proposés doivent à présent retourner les services SQL Server

```PowerShell
PS C:\> Get-Service -Name *SQL*
Status  Name           DisplayName
------  ----           -----------
Running MSSQLSERVER    SQL Server (MSSQLSERVER)
Stopped SQLBrowser     SQL Server Browser
Running SQLSERVERAGENT SQL Server Agent (MSSQLSERVER)
Running SQLTELEMETRY   SQL Server CEIP service (MSSQLSERVER)
Running SQLWriter      SQL Server VSS Writer
```

### <a name="sql-server"></a>SQL Server

```PowerShell
PS C:\> & sqlcmd -S $env:COMPUTERNAME
1> SELECT @@SERVERNAME
2> GO
1> quit
```

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la configuration d’état souhaité Windows PowerShell](https://docs.microsoft.com/powershell/dsc/overview)

[Installer SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)

[Installer SQL Server à l’aide d’un fichier de configuration](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)
