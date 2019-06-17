---
title: Télécharger le module PowerShell SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
keywords:
- installer powershell sql server, télécharger powershell sql server
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0f14a3cee050fff07c7fe5bc2467bcb8209a53c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62672576"
---
# <a name="install-sql-server-powershell-module"></a>Installer le module SQL Server PowerShell
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Cet article fournit des instructions pour installer le module PowerShell **SqlServer**.
> [!NOTE]
> Il existe deux modules SQL Server PowerShell : 
> * **SQLPS** : ce module est inclus avec l’installation de SQL Server (à des fins de compatibilité descendante), mais il n’est plus mis à jour. Le module PowerShell le plus récent est **SqlServer**.
> * **SqlServer** : ce module inclut de nouvelles applets de commande pour prendre en charge les dernières fonctionnalités SQL. Le module contient également des versions mises à jour des applets de commande dans **SQLPS**. 

Des versions précédentes du module **SqlServer** *étaient* fournies avec SQL Server Management Studio (SSMS), mais uniquement avec les versions 16.x de SSMS. Pour utiliser PowerShell avec SSMS 17.0 et ultérieur, vous devez installer le module **SqlServer** à partir de [PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver).
La version actuelle du module **SqlServer** est 21.1.18080. Il est basé sur la version v150 de Microsoft.SQLServer.SMO et prend en charge la prochaine version de SQL Server. La dernière version du module basé sur la version v140 de Microsoft.SQLServer.SMO) est 21.0.17279.

Il se peut que les préversions du module soient mises à disposition de manière plus fréquente : consultez la section au bas de cette page pour savoir comment obtenir ces versions du module.

Pour installer le module **SqlServer** à partir de PowerShell Gallery, démarrez une session [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting) et utilisez les commandes suivantes. Si vous rencontrez des problèmes d’installation, consultez la [documentation sur Install-Module](https://docs.microsoft.com/powershell/gallery/psget/module/psget_install-module) et les [informations de référence sur Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module).

Pour installer le module **SqlServer** :

```Install-Module -Name SqlServer```

Si des versions précédentes du module **SqlServer** sont présentes sur l’ordinateur, vous pouvez peut-être utiliser `Update-Module` (traité plus loin dans cet article) ou fournir le paramètre `-AllowClobber` :  

```Install-Module -Name SqlServer -AllowClobber```

Si vous ne pouvez pas exécuter la session PowerShell en tant qu’administrateur, vous pouvez effectuer l’installation pour l’utilisateur actuel :

```Install-Module -Name SqlServer -Scope CurrentUser```

Quand des versions mises à jour du module **SqlServer** sont disponibles, vous pouvez mettre à jour la version en utilisant `Update-Module` :

```Update-Module -Name SqlServer```

Pour afficher les versions du module installées :

```Get-Module SqlServer -ListAvailable```

Pour utiliser une version spécifique du module, vous pouvez l’importer avec un numéro de version spécifique comme dans l’exemple suivant :

```Import-Module SqlServer -Version 21.1.18080```

> [!NOTE]
> Les versions préliminaires (ou « préversions ») du module peuvent être disponibles dans PowerShell Gallery. Vous pouvez les découvrir et les installer à l’aide des applets de commande *Find-Module* et *Install-Module* mises à jour (qui font partie du module [PowerShellGet](https://www.powershellgallery.com/packages/PowerShellGet)) en passant le commutateur *- AllowPrerelease*.
>
> Pour découvrir la version préliminaire/préversion du module, vous pouvez exécuter la commande suivante :
>
> ```Find-Module SqlServer -AllowPrerelease```
>
> Pour installer une version préliminaire/préversion spécifique du module, vous pouvez l’installer avec un numéro de version spécifique comme dans l’exemple suivant :
>
> ```Install-Module SqlServer -RequiredVersion 21.1.18040-preview -AllowPrerelease```
> 

Les versions du module **SqlServer** dans PowerShell Gallery prennent en charge la gestion des versions et nécessitent PowerShell version 5.0 ou ultérieure. 

* [Module SqlServer dans PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver) 
* [Applets de commande SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)
* [Applets de commande SQLPS](https://docs.microsoft.com/powershell/module/sqlps)
