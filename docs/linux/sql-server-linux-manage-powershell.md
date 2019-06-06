---
title: Gérer SQL Server sur Linux avec PowerShell | Microsoft Docs
description: Cet article fournit une vue d’ensemble de l’utilisation de PowerShell sur Windows avec SQL Server sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 8398db9e03aabf6863bd770f8be6657b58be1591
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718077"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Utiliser PowerShell sur Windows pour gérer SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article présente [SQL Server PowerShell](../powershell/sql-server-powershell.md) et vous présente quelques exemples sur son utilisation avec SQL Server sur Linux. Prise en charge de PowerShell pour SQL Server est actuellement disponible sur Windows, MacOS et Linux. Cet article vous guide tout au long d’à l’aide d’un ordinateur Windows pour se connecter à une instance distante de SQL Server sur Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Installer la dernière version de SQL PowerShell sur Windows

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) sur Windows sont conservées dans la galerie PowerShell. Lorsque vous travaillez avec SQL Server, vous devez toujours utiliser la version la plus récente du module SqlServer PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

Lire le [problèmes connus](sql-server-linux-release-notes.md) pour SQL Server sur Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Lancez PowerShell et importez le *sqlserver* module

Nous allons commencer en lançant PowerShell sur Windows. Utilisez <kbd>Win</kbd>+<kbd>R</kbd>, sur votre ordinateur de Windows et tapez **PowerShell** pour lancer une nouvelle session Windows PowerShell.

```
PowerShell
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

Nous allons utiliser PowerShell sur Windows pour se connecter à votre instance de SQL Server sur Linux et afficher les deux propriétés de serveur.

Copiez et collez les commandes suivantes à l’invite de PowerShell. Lorsque vous exécutez ces commandes, PowerShell sera :
- Afficher une boîte de dialogue qui vous invite à entrer le nom d’hôte ou l’adresse IP de votre instance
- Afficher le *demande des informations d’identification Windows PowerShell* boîte de dialogue qui vous invite à entrer les informations d’identification. Vous pouvez utiliser votre *nom d’utilisateur SQL* et *mot de passe SQL* pour vous connecter à votre instance de SQL Server sur Linux
- Utilisez le **Get-SqlInstance** applet de commande pour vous connecter à la **Server** et quelques propriétés d’affichage

Si vous le souhaitez, vous pouvez simplement remplacer le `$serverInstance` variable avec l’adresse IP ou le nom d’hôte de votre instance de SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Connect to the Server and get a few properties
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

Une autre option pour la connexion à votre instance SQL Server consiste à utiliser le [fournisseur PowerShell SQL Server](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider).  Ce fournisseur vous permet de naviguer d’instance de SQL Server comme dans comme si vous ont été parcours de la structure d’arborescence dans l’Explorateur d’objets, mais à la ligne de commande.  Par défaut, ce fournisseur est présenté sous la forme d’un PSDrive nommé `SQLSERVER:\` que vous pouvez utiliser pour se connecter & accédez des instances de SQL Server à laquelle votre compte de domaine a accès.  Consultez [étapes de Configuration](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps) pour plus d’informations sur la façon de configurer l’authentification d’Active Directory pour SQL Server sur Linux.

Vous pouvez également utiliser l’authentification SQL avec le fournisseur PowerShell SQL Server. Pour ce faire, utilisez le `New-PSDrive` applet de commande pour créer un nouveau PSDrive et de fournir les informations d’identification appropriées afin de vous connecter.

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

Voici à quoi peut ressembler la sortie.  Vous pouvez remarquer que la sortie est similaire à ce que SSMS affiche au niveau du nœud de bases de données.  Il affiche les bases de données utilisateur, mais pas les bases de données système.

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

Si vous avez besoin de voir toutes les bases de données sur votre instance, une option consiste à utiliser le [Get-SqlDatabase](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlDatabase) applet de commande.

## <a name="examine-sql-server-error-logs"></a>Examinez les journaux d’erreurs SQL Server

Les étapes suivantes utilisent PowerShell sur Windows pour examiner l’erreur journaux se connecter sur votre instance de SQL Server sur Linux. Nous utiliserons également le **Out-GridView** journaux de l’applet de commande pour afficher des informations à partir de l’erreur dans un affichage de la vue grille.

Copiez et collez les commandes suivantes à l’invite de PowerShell. Il peuvent prendre quelques minutes pour s’exécuter. Ces commandes procédez comme suit :
- Afficher une boîte de dialogue qui vous invite à entrer le nom d’hôte ou l’adresse IP de votre instance
- Afficher le *demande des informations d’identification Windows PowerShell* boîte de dialogue qui vous invite à entrer les informations d’identification. Vous pouvez utiliser votre *nom d’utilisateur SQL* et *mot de passe SQL* pour vous connecter à votre instance de SQL Server sur Linux
- Utilisez le **Get-SqlErrorLog** ouvre une applet de commande pour vous connecter à l’instance de SQL Server sur Linux et de récupérer l’erreur depuis **hier**
- Dirigez la sortie vers le **Out-GridView** applet de commande

Si vous le souhaitez, vous pouvez remplacer le `$serverInstance` variable avec l’adresse IP ou le nom d’hôte de votre instance de SQL Server.

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>Voir aussi
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
- [Applets de commande SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)
