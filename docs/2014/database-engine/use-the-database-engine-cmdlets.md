---
title: Utiliser les applets de commande du Moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd5575c94c9a74623efaa80c9470c54982a41d0d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783108"
---
# <a name="use-the-database-engine-cmdlets"></a>Utiliser les applets de commande du Moteur de base de données
  Les applets de commande Windows PowerShell sont des commandes à fonction unique qui utilisent généralement une convention d’affectation de noms de type verbe-nom, par exemple, **obtenir-Help** ou **Set-MachineName**. Le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour Windows PowerShell fournit des applets de commande spécifiques à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="database-engine-cmdlets"></a>Applets de commande du moteur de base de données  
 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] implémente un petit nombre d'applets de commande pour le [!INCLUDE[ssDE](../includes/ssde-md.md)]. Ces applets de commande sont principalement utilisées pour exécuter des scripts Transact-SQL existants à partir de nouveaux scripts PowerShell, pour évaluer les stratégies de gestion basée sur des stratégies et pour aider à spécifier des identificateurs SQL Server dans les chemins d'accès de fournisseur SQL Server.  
  
 La plupart des scripts Windows PowerShell travaillent avec le [!INCLUDE[ssDE](../includes/ssde-md.md)] en utilisant le fournisseur PowerShell SQL Server et les modèles d'objet de gestion SQL Server. Pour plus d’informations, consultez [SQL Server PowerShell](../powershell/sql-server-powershell.md).  
  
### <a name="get-cmdlet-help"></a>Obtenir de l'aide sur les applets de commande  
 Dans l’environnement Windows PowerShell, l’applet de commande **Get-Help** fournit des informations d’aide sur chaque applet de commande. L’applet **de commande obtenir-Help** retourne des informations telles que la syntaxe, les définitions de paramètres, les types d’entrée et de sortie, ainsi qu’une description de l’action effectuée par l’applet de commande. Pour en savoir plus, voir [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md).  
  
### <a name="partial-parameter-names"></a>Noms de paramètres partiels  
 Il n'est pas nécessaire de spécifier le nom entier d'un paramètre d'applet de commande. Il vous suffit de spécifier une partie suffisante du nom pour le distinguer des autres paramètres pris en charge par l'applet de commande. Ces exemples montrent trois façons différentes de spécifier le paramètre **Invoke-Sqlcmd -QueryTimeout** :  
  
```powershell
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a>Tâches d'applet de commande du moteur de base de données  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit l’utilisation de l’applet de commande **Invoke-Sqlcmd** pour exécuter des scripts **sqlcmd** ou des commandes qui contiennent des instructions XQuery ou [!INCLUDE[tsql](../includes/tsql-md.md)] . Elle peut accepter l’entrée **sqlcmd** sous la forme d’un paramètre d’entrée de chaîne de caractères ou sous la forme du nom d’un fichier de script à ouvrir.|[Invoke-Sqlcmd (applet de commande)](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|Décrit l’utilisation de l’applet de commande **Invoke-PolicyEvaluation** pour indiquer si un ensemble d’objets [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cible est conforme ou non aux conditions définies dans les stratégies de gestion basée sur des stratégies. Vous pouvez éventuellement utiliser cette applet de commande pour reconfigurer toutes les options définissables dans les objets cibles qui ne sont pas conformes aux conditions des stratégies.|[Invoke-PolicyEvaluation (applet de commande)](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
|Décrit l'utilisation des applets de commande `Encode-Sqlname` et `Decode-Sqlname` pour gérer les identificateurs SQL Server qui contiennent des caractères non pris en charge dans les chemins d'accès Windows PowerShell.|[Encoder et décoder des identificateurs SQL Server](../powershell/encode-and-decode-sql-server-identifiers.md)|  
|Décrit l'utilisation de l'applet de commande `Convert-UrnToPath` pour convertir l'URN (Uniform Resource Locator) d'un objet de gestion de SQL Server dans son équivalent de chemin d'accès au fournisseur SQL Server.|[Convertir des URN en chemins de fournisseur SQL Server](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [fournisseur PowerShell SQL Server](../powershell/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)   
 [Vue d’ensemble des applets de commande PowerShell pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  
