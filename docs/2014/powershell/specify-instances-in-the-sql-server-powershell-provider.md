---
title: Spécifier des instances dans le fournisseur SQL Server PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
author: stevestein
ms.author: sstein
ms.openlocfilehash: b23c2f331c681862f7b871521937847eec2d9419
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960090"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a>Spécifier des instances dans le fournisseur SQL Server PowerShell
  Les chemins d'accès spécifiés pour le fournisseur PowerShell SQL Server doivent identifier l'instance du [!INCLUDE[ssDE](../includes/ssde-md.md)] et de l'ordinateur sur lequel elle s'exécute. La syntaxe pour spécifier l'ordinateur et l'instance doit être conforme aux règles relatives aux identificateurs SQL Server et aux chemins d'accès Windows PowerShell.  
  
1.  **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions)  
  
2.  **Pour spécifier une instance :**  [Exemples](#Examples)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Le premier nœud venant après SQLSERVER:\SQL dans un chemin d'accès de fournisseur SQL Server est le nom de l'ordinateur qui exécute l'instance du [!INCLUDE[ssDE](../includes/ssde-md.md)]; par exemple :  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 Si vous exécutez Windows PowerShell sur le même ordinateur que l'instance du [!INCLUDE[ssDE](../includes/ssde-md.md)], vous pouvez utiliser localhost ou (local) à la place du nom de l'ordinateur. Les scripts utilisant localhost ou (local) peuvent être exécutés sur n'importe quel ordinateur, sans qu'il soit nécessaire de les modifier pour refléter différents noms d'ordinateur.  
  
 Vous pouvez exécuter plusieurs instances du programme exécutable du [!INCLUDE[ssDE](../includes/ssde-md.md)] sur le même ordinateur. Le nœud venant après le nom de l'ordinateur dans un chemin d'accès de fournisseur SQL Server identifie l'instance ; par exemple :  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 Chaque ordinateur peut avoir une instance par défaut du [!INCLUDE[ssDE](../includes/ssde-md.md)]. Vous ne spécifiez pas de nom pour l'instance par défaut lorsque vous l'installez. Si vous spécifiez seulement un nom d'ordinateur dans une chaîne de connexion, vous êtes connecté à l'instance par défaut sur cet ordinateur. Toutes les autres instances sur l'ordinateur doivent être des instances nommées. Vous spécifiez le nom de l'instance pendant l'installation, et les chaînes de connexion doivent spécifier à la fois le nom d'ordinateur et le nom de l'instance.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Vous ne pouvez pas utiliser de point (.) pour spécifier l'ordinateur local dans les scripts PowerShell. Le point n'est pas pris en charge car PowerShell l'interprète comme une commande.  
  
 Les parenthèses contenues dans (local) sont normalement traitées comme des commandes par Windows PowerShell. Vous devez les encoder ou les placer dans une séquence d'échappement pour une utilisation dans un chemin d'accès, ou mettre le chemin d'accès entre guillemets doubles. Pour plus d'informations, consultez Encoder et décoder des identificateurs SQL Server.  
  
 Le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requiert que vous spécifiiez toujours un nom d'instance. Pour les instances par défaut, vous devez spécifier le nom de l'instance DEFAULT.  
  
##  <a name="examples-computer-and-instance-names"></a><a name="Examples"></a> Exemples : noms d'ordinateur et d'instance  
 Cet exemple utilise localhost et DEFAULT pour spécifier l'instance par défaut sur l'ordinateur local :  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT
```  
  
 Les parenthèses contenues dans (local) sont normalement traitées comme des commandes par Windows PowerShell. Vous devez effectuer l'une des opérations suivantes :  
  
-   Mettre la chaîne de chemin d'accès entre guillemets :  
  
    ```powershell
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   Placer la parenthèse dans une séquence d'échappement à l'aide du caractère « ` » (backtick) :  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   Encoder la parenthèse à l'aide de sa représentation hexadécimale :  
  
    ```powershell
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Identificateurs de SQL Server dans PowerShell](sql-server-identifiers-in-powershell.md)   
 [Fournisseur SQL Server PowerShell](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
