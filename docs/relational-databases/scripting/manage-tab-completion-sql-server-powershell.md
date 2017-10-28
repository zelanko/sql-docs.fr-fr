---
title: "Gérer la saisie semi-automatique par tabulation (SQL Server PowerShell) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6296848a-890f-4ad3-8d9f-92ed6a79aa00
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 310aa99b485cedf79237f993a8ffbdcffe9d2a46
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="manage-tab-completion-sql-server-powershell"></a>Gérer la saisie semi-automatique par tabulation (SQL Server PowerShell)
  Les composants logiciels enfichables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell introduisent trois variables (**$SqlServerMaximumTabCompletion**, **$SqlServerMaximumChildItems**et **$SqlServerIncludeSystemObjects**) pour contrôler la saisie semi-automatique par tabulation de Windows PowerShell. La saisie semi-automatique par tabulation réduit la quantité de caractères que vous devez taper en renvoyant des tableaux d'éléments dont le nom commence par la chaîne que vous tapez.  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Avec la saisie semi-automatique par tabulation de Windows PowerShell, une fois que vous avez tapé une partie d'un chemin d'accès ou d'un nom d'applet de commande, vous pouvez appuyer sur la touche Tab pour obtenir la liste des éléments dont le nom correspond à ce que vous avez déjà tapé. Vous pouvez alors sélectionner l'élément souhaité dans la liste sans avoir à taper le reste du nom.  
  
 Si vous travaillez dans une base de données qui contient beaucoup d'objets, les listes de saisie semi-automatique par tabulation peuvent devenir très longues. Certains types d'objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tels que les vues, contiennent également de nombreux objets système.  
  
 Les composants logiciels enfichables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] introduisent trois variables système que vous pouvez utiliser pour contrôler la quantité d’informations présentées par le biais de la saisie semi-automatique par tabulation et de **Get-ChildItem**.  
  
 **$SqlServerMaximumTabCompletion =** *n*  
 Spécifie le nombre maximal d'objets à inclure dans une liste de saisie semi-automatique par tabulation. Si vous appuyez sur la touche Tab au niveau d’un nœud de chemin contenant plus de *n* objets, la liste de saisie semi-automatique par tabulation est tronquée au niveau *n*. *n* est un entier. Le paramètre par défaut 0 signifie que le nombre d'objets répertoriés est illimité.  
  
 **$SqlServerMaximumChildItems =** *n*  
 Spécifie le nombre maximal d’objets affichés par **Get-ChildItem**. Si **Get-ChildItem** est exécuté sur un nœud de chemin contenant plus de *n* objets, la liste est tronquée au niveau *n*. *n* est un entier. Le paramètre par défaut 0 signifie que le nombre d'objets répertoriés est illimité.  
  
 **$SqlServerIncludeSystemObjects =** { **$True** | **$False** }  
 Si cette variable est définie sur **$True**, les objets système sont affichés par le biais de la saisie semi-automatique par tabulation et de **Get-ChildItem**. Si cette variable est définie sur **$False**, aucun objet système n’est affiché. La valeur par défaut est **$False**.  
  
## <a name="set-the-sql-server-tab-completion-variables"></a>Définir les variables de la saisie semi-automatique par tabulation de SQL Server  
 Pour chacune des variables pour lesquelles vous souhaitez utiliser une valeur autre que la valeur par défaut, définissez la nouvelle valeur de la variable.  
  
### <a name="example-powershell"></a>Exemple (PowerShell)  
 L'exemple suivant définit les trois variables et répertorie leurs paramètres :  
  
```  
$SqlServerMaximumTabCompletion = 20  
$SqlServerMaximumChildItems = 10  
$SqlServerIncludeSystemObjects = $False  
dir variable:sqlserver*  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  

