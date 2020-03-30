---
title: Télécharger le module PowerShell SQL Server
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: carlrab
ms.custom: ''
ms.date: 01/23/2020
ms.openlocfilehash: 99976a12ae76254da5b50c5467df9d9e42fdbbce
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "76920355"
---
# <a name="install-the-sql-server-powershell-module"></a>Installer le module SQL Server PowerShell

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Cet article fournit des instructions pour installer le module PowerShell **SqlServer**.

## <a name="powershell-modules-for-sql-server"></a>Modules PowerShell pour SQL Server

Il existe deux modules SQL Server PowerShell :

- **SqlServer** : Le module SqlServer inclut de nouvelles applets de commande pour prendre en charge les dernières fonctionnalités SQL. Le module contient également des versions mises à jour des applets de commande dans **SQLPS**. Pour télécharger le module SqlServer, accédez à [Module SqlServer dans PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver).
- **SQLPS** : Le module SQLPS fait partie de l’installation de SQL Server (à des fins de compatibilité descendante), mais il n’est plus mis à jour. Le module PowerShell le plus récent est **SqlServer**.

> [!NOTE]
> Les versions du module **SqlServer** dans PowerShell Gallery prennent en charge la gestion des versions et nécessitent PowerShell version 5.0 ou ultérieure.

Pour consulter les rubriques d’aide, accédez à :

- Applets de commande [SqlServer](https://docs.microsoft.com/powershell/module/sqlserver).
- Applets de commande [SQLPS](https://docs.microsoft.com/powershell/module/sqlps).

## <a name="sql-server-management-studio"></a>SQL Server Management Studio

SQL Server Management Studio (SSMS), à partir de la version 17,0, n’installe aucun module PowerShell. Pour utiliser PowerShell avec SSMS, installez le module **SqlServer** à partir de [PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver).

> [!NOTE]
> Avec la version 16.x de SSMS, une version antérieure du module **SqlServer** est incluse avec SQL Server Management Studio (SSMS)

## <a name="azure-data-studio"></a>Azure Data Studio

Azure Data Studio n’installe aucun module PowerShell. Pour utiliser PowerShell avec Azure Data Studio, installez le module **SqlServer** à partir de [PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver).

Vous pouvez utiliser l’[extension PowerShell](../azure-data-studio/powershell-extension.md), qui fournit une prise en charge complète de l’éditeur PowerShell dans Azure Data Studio.

## <a name="installing-or-updating-the-sqlserver-module"></a>Installation ou mise à jour du module SqlServer

Pour installer le module **SqlServer** à partir de PowerShell Gallery, démarrez une session [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting) en tant qu’administrateur. Démarrez également Azure Data Studio en tant qu’administrateur et exécutez ces commandes dans une session PowerShell du terminal intégré.

### <a name="install-the-sqlserver-module"></a>Installer le module SqlServer

Exécutez la commande suivante dans votre session PowerShell afin d’installer le module SqlServer pour tous les utilisateurs :

```powershell
Install-Module -Name SqlServer
```

### <a name="to-view-the-versions-of-the-sqlserver-module-installed"></a>Pour afficher les versions du module SqlServer installées :

Exécutez la commande suivante pour afficher les versions du module SqlServer qui ont été installées

```powershell
Get-Module SqlServer -ListAvailable
```

### <a name="install-for-the-current-user-rather-than-as-an-administrator"></a>Effectuez l’installation pour l’utilisateur actuel plutôt que comme administrateur

Si vous ne pouvez pas exécuter la session PowerShell en tant qu’administrateur, effectuez l’installation pour l’utilisateur actuel à l’aide de la commande suivante :

```powershell
Install-Module -Name SqlServer -Scope CurrentUser
```

### <a name="to-overwrite-a-previous-version-of-the-sqlserver-module"></a>Pour remplacer une version précédente du module SqlServer

Vous pouvez également utiliser la commande `Install-Module` pour remplacer une version précédente.

```powershell
Install-Module -Name SqlServer -AllowClobber
```

> [!Note]
> PowerShell utilise toujours le dernier module installé.

### <a name="update-the-installed-version-of-the-sqlserver-module"></a>Mettre à jour la version installée du module SqlServer

Quand des versions mises à jour du module **SqlServer** sont disponibles, vous pouvez installer la dernière version à l’aide de la commande suivante :

```powershell
Install-Module -Name SqlServer -AllowClobber
```

Vous pouvez utiliser la commande `Update-Module` pour installer la version la plus récente du module SQL Server PowerShell, mais cela ne supprime pas les versions antérieures. Cette commande installe la version la plus récente côte à côte pour vous permettre de tester la version la plus récente en conservant les anciens modules installés.

Toutefois, si vous ne souhaitez pas conserver les anciennes versions du module, vous pouvez utiliser la commande `Uninstall-Module` pour supprimer les versions précédentes.

Vous pouvez utiliser la commande suivante pour répertorier les différentes versions installées :

```powershell
Get-Module SqlServer -ListAvailable
```

Vous pouvez utiliser la commande suivante pour supprimer les anciennes versions :

```powershell
Uninstall-module -Name SQLServer -RequiredVersion "<version number>" -AllowClobber
```

### <a name="troubleshooting"></a>Dépannage

Si vous rencontrez des problèmes d’installation, consultez la [documentation sur Install-Module](https://www.powershellgallery.com/packages/PowerShellGet/2.2.1) et les [informations de référence sur Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module).

## <a name="using-a-specific-version-of-the-sqlserver-module"></a>Utilisation d’une version spécifique du module SqlServer

Pour utiliser une version spécifique du module, importez-la avec un numéro de version spécifique comme dans la commande suivante :

```powershell
Import-Module SqlServer -Version 21.1.18080
```

## <a name="pre-release-versions-of-the-sqlserver-module"></a>Versions préliminaires du module SqlServer

Les versions préliminaires (ou « préversions ») du module SqlServer peuvent être disponibles dans PowerShell Gallery.

> [!IMPORTANT]
> Vous pouvez découvrir et installer ces versions à l’aide des applets de commande *Find-Module* et *Install-Module* mises à jour (qui font partie du module [PowerShellGet](https://www.powershellgallery.com/packages/PowerShellGet)) en passant le commutateur *- AllowPrerelease*. Pour utiliser ces applets de commande, installez le module PowerShellGet, puis ouvrez une nouvelle session.

### <a name="to-discover-pre-release-versions-of-the-sqlserver-module"></a>Pour découvrir les versions préliminaires du module SqlServer

Pour découvrir les versions préliminaires (préversions) du module SqlServer, exécutez la commande suivante :

```powershell
Find-Module SqlServer -AllowPrerelease
```

### <a name="to-install-a-specific-pre-release-version-of-the-sqlserver-module"></a>Pour installer une version préliminaire spécifique du module SqlServer

Pour installer une version préliminaire spécifique du module, installez-la avec un numéro de version spécifique.

Vous pouvez essayer d’utiliser la commande suivante :

```powershell
Install-Module SqlServer -RequiredVersion 21.1.18040-preview -AllowPrerelease
```

## <a name="sql-server-powershell-on-linux"></a>SQL Server PowerShell sur Linux

Visitez [Gérer SQL Server sur Linux avec PowerShell Core](../linux/sql-server-linux-manage-powershell-core.md) pour savoir comment installer SQL Server PowerShell sur Linux.
