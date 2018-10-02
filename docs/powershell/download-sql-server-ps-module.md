---
title: Télécharger le module PowerShell SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/05/2018
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
ms.openlocfilehash: d41d03c3bba51b919a71f195de75a7ec29f51b7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621557"
---
# <a name="install-sql-server-powershell-module"></a>Installer le module SQL Server PowerShell
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Cet article fournit des instructions pour installer le module PowerShell **SqlServer**.

> [!NOTE]
> Il existe deux modules SQL Server PowerShell : **SqlServer** et **SQLPS**. Le module **SQLPS** fait partie de l’installation de SQL Server (à des fins de compatibilité descendante), mais il n’est plus mis à jour. Le module PowerShell le plus récent est **SqlServer**. Le module **SqlServer** contient les versions mises à jour des applets de commande disponibles dans **SQLPS**, ainsi que de nouvelles applets de commande pour prendre en charge les dernières fonctionnalités SQL. Des versions précédentes du module **SqlServer** *étaient* fournies avec SQL Server Management Studio (SSMS), mais uniquement avec les versions 16.x de SSMS. Pour utiliser PowerShell avec SSMS 17.0 et ultérieur, vous devez installer le module **SqlServer** à partir de PowerShell Gallery.

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

```Import-Module SqlServer -Version 21.0.17178```


Les versions du module **SqlServer** dans PowerShell Gallery prennent en charge la gestion des versions et nécessitent PowerShell version 5.0 ou ultérieure. 

* [Module SqlServer dans PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver) 
* [Applets de commande SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)
* [Applets de commande SQLPS](https://docs.microsoft.com/powershell/module/sqlps)
