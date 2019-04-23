---
title: Gérer SQL Server sur Linux avec PowerShell | Microsoft Docs
description: Cet article fournit une vue d’ensemble de l’utilisation de PowerShell sur Windows avec SQL Server sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 903d2d89ca0d551cbb78cfb69dd305f852f62313
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158765"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Utiliser PowerShell sur Windows pour gérer SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article présente [SQL Server PowerShell](../powershell/sql-server-powershell.md) et vous présente quelques exemples sur son utilisation avec SQL Server sur Linux. Prise en charge de PowerShell pour SQL Server est actuellement disponible sur Windows, vous pouvez l’utiliser lorsque vous avez une machine Windows pouvant se connecter à une instance distante de SQL Server sur Linux.

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Installer la dernière version de SQL PowerShell sur Windows

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) sur Windows sont conservées dans la galerie PowerShell. Lorsque vous travaillez avec SQL Server, vous devez toujours utiliser la version la plus récente du module SqlServer PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

Lire le [problèmes connus](sql-server-linux-release-notes.md) pour SQL Server sur Linux.

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>Lancez PowerShell et importez le *sqlserver* module

Nous allons commencer en lançant PowerShell sur Windows. Ouvrir un *invite de commandes* sur votre ordinateur de Windows et tapez **PowerShell** pour lancer une nouvelle session Windows PowerShell.

```
PowerShell
```

SQL Server fournit un module Windows PowerShell nommé **SqlServer** que vous pouvez utiliser pour importer les composants de SQL Server (fournisseur de SQL Server et applets de commande) dans un environnement de PowerShell ou d’un script.

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
- Afficher le *demande des informations d’identification Windows PowerShell* boîte de dialogue qui vous invite à entrer les informations d’identification (*nom d’utilisateur SQL* et *mot de passe SQL*) pour se connecter à votre serveur SQL Server instance sur Linux
- Créez une instance de la [Server](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.server.aspx) objet
- Se connecter à la **Server** et quelques propriétés d’affichage

N’oubliez pas de remplacer **\<your_server_instance\>** avec l’adresse IP ou le nom d’hôte de votre instance de SQL Server sur Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
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

## <a name="examine-sql-server-error-logs"></a>Examinez les journaux d’erreurs SQL Server

Nous allons utiliser PowerShell sur Windows pour examiner les journaux d’erreurs connect sur votre instance de SQL Server sur Linux. Nous utiliserons également le **Out-GridView** journaux de l’applet de commande pour afficher des informations à partir de l’erreur dans un affichage de la vue grille.

Copiez et collez les commandes suivantes à l’invite de PowerShell. Il peuvent prendre quelques minutes pour s’exécuter. Ces commandes procédez comme suit :
- Afficher le *demande des informations d’identification Windows PowerShell* boîte de dialogue qui vous invite à entrer les informations d’identification (*nom d’utilisateur SQL* et *mot de passe SQL*) pour se connecter à votre serveur SQL Server instance sur Linux
- Utilisez le **Get-SqlErrorLog** ouvre une applet de commande pour vous connecter à l’instance de SQL Server sur Linux et de récupérer l’erreur depuis **hier**
- Dirigez la sortie vers le **Out-GridView** applet de commande

N’oubliez pas de remplacer **\<your_server_instance\>** avec l’adresse IP ou le nom d’hôte de votre instance de SQL Server sur Linux.

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>Voir aussi
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
