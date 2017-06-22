---
title: "Référence de PowerShell (Moteur de base de données) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dc3df1d697b05201ac48520c1e344c28648cdfaf
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="database-engine-powershell-reference"></a>Référence de PowerShell (Moteur de base de données)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] inclut un jeu d’applets de commande Windows PowerShell pour effectuer des actions courantes dans le [!INCLUDE[ssDE](../includes/ssde-md.md)]. En outre, les expressions de requête et les noms URN (Uniform Resource Names) peuvent être convertis en chemins d'accès SQL Server PowerShell, ou être utilisés pour spécifier un ou plusieurs objets dans le [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
## <a name="database-engine-cmdlets"></a>Applets de commande du moteur de base de données  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] inclut relativement peu d’applets de commande pour le [!INCLUDE[ssDE](../includes/ssde-md.md)]. La plupart des scripts PowerShell compatibles avec le [!INCLUDE[ssDE](../includes/ssde-md.md)] utilisent le fournisseur SQL Server PowerShell et les modèles d'objet de gestion. Pour plus d’informations, consultez [Fournisseur PowerShell SQL Server](../relational-databases/scripting/sql-server-powershell-provider.md).  
  
 Pour savoir comment obtenir de l’aide sur les applets de commande SQL Server dans un environnement Windows PowerShell, consultez [Obtenir de l’aide sur SQL Server PowerShell](../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
### <a name="in-this-section"></a>Dans cette section  
 Cette section contient des informations sur ces applets de commande.  
  
|Description|Applet de commande|  
|-----------------|------------|  
|Exécute les scripts Transact-SQL et XQuery, tels que les scripts qui peuvent être exécutés à l’aide de l’utilitaire **sqlcmd** .|[Invoke-Sqlcmd (applet de commande)](../powershell/invoke-sqlcmd-cmdlet.md)|  
|Évalue si un objet du moteur de base de données est conforme à une stratégie de gestion basée sur des stratégies.|[Invoke-PolicyEvaluation (applet de commande)](../powershell/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a>Informations sur d'autres applets de commande  
 Les applets de commande **Encode-Sqlname** et **Decode-Sqlname** vous aident à spécifier les identificateurs SQL Server qui contiennent des caractères non pris en charge dans les chemins PowerShell. Pour plus d’informations, consultez [Identificateurs SQL Server dans PowerShell](../relational-databases/scripting/sql-server-identifiers-in-powershell.md).  
  
 Utilisez l’applet de commande **Convert-UrnToPath** pour convertir un nom de ressource unique pour un objet du [!INCLUDE[ssDE](../includes/ssde-md.md)] en un chemin pour le fournisseur PowerShell SQL Server. Pour plus d’informations, consultez [Convertir des URN en chemins d’accès de fournisseur SQL Server](../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md).  
  
## <a name="query-expressions-and-unique-resource-names"></a>Expressions de requête et noms de ressource uniques  
 Les expressions de requête sont des chaînes qui utilise une syntaxe semblable à XPath pour spécifier un jeu de critères permettant d'énumérer un ou plusieurs objets dans une hiérarchie de modèle objet. Un nom de ressource unique (URN) est un type spécifique de chaîne d'expression de requête qui identifie de façon unique un objet particulier. Pour plus d’informations, consultez [Expressions de requête et noms URN](../powershell/query-expressions-and-uniform-resource-names.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  
