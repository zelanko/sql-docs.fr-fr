---
title: Importer le module SQLPS | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1916be8c443799fa41680341e72889bd10551b4a
ms.sourcegitcommit: 381595e990f2294dbf324ef31071e2dd2318b8dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74200429"
---
# <a name="import-the-sqlps-module"></a>Importer le module SQLPS
  La méthode recommandée pour gérer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à partir de PowerShell consiste à importer le module `sqlps` dans un environnement Windows PowerShell 2.0. Le module charge et inscrit les assemblys de facilité de gestion et les composants logiciels enfichables [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
1.  **Avant de commencer :**  [sécurité](#Security)  
  
2.  **Pour charger le module :**  [charger le module sqlps](#LoadSqlps)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Après avoir importé le module `sqlps` dans Windows PowerShell, vous pouvez :  
  
-   exécuter des commandes Windows PowerShell de façon interactive ;  
  
-   exécuter des fichiers de script Windows PowerShell ;  
  
-   exécuter des applets de commande [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ;  
  
-   utiliser les chemins d'accès du fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour naviguer dans la hiérarchie des objets [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ;  
  
-   utiliser les modèles objets de la facilité de gestion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (tels que Microsoft.SqlServer.Management.Smo) pour gérer des objets [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Les verbes utilisés dans les noms de deux applets de commande SQL Server (`Encode-Sqlname` et `Decode-Sqlname`) ne correspondent pas aux verbes approuvés pour Windows PowerShell 2.0. Cela n'a aucun effet sur leur opération, mais Windows PowerShell déclenche un avertissement lorsque le module `sqlps` est importé dans une session.  
  
###  <a name="Security"></a>Caution  
 Par défaut, Windows PowerShell s’exécute avec le niveau **Restreint**de la stratégie d’exécution de scripts, ce qui empêche l’exécution de tout script Windows PowerShell. Pour charger le module `sqlps`, vous pouvez utiliser l'applet de commande `Set-ExecutionPolicy` pour activer l'exécution de scripts signés uniquement ou de tous les scripts. Exécutez uniquement des scripts provenant de sources fiables et sécurisez tous les fichiers d'entrée et de sortie en utilisant les autorisations NTFS appropriées. Pour plus d'informations sur l'activation de scripts Windows PowerShell, consultez [Exécution de scripts Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows).  
  
##  <a name="LoadSqlps"></a>Charger le module sqlps  

### <a name="to-load-the-sqlps-module-in-windows-powershell"></a>Pour charger le module sqlps dans Windows PowerShell
  
1.  Utilisez l'applet de commande `Set-ExecutionPolicy` pour définir la stratégie d'exécution de scripts appropriée.  
  
2.  Utilisez l'applet de commande `Import-Module` pour importer le module sqlps. Spécifiez le paramètre `DisableNameChecking` si vous souhaitez supprimer l'avertissement sur `Encode-Sqlname` et `Decode-Sqlname`.  
  
### <a name="example-powershell"></a>Exemple (PowerShell)  
 Cet exemple charge le module `sqlps` avec la fonction de vérification des noms désactivée.  
  
```powershell
## Import the SQL Server Module.  
  
Import-Module "sqlps" -DisableNameChecking  
```  

## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)   
 [Fournisseur SQL Server PowerShell](../powershell/sql-server-powershell-provider.md)   
 [Utiliser les applets de commande Moteur de base de données](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
