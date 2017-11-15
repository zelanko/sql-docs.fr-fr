---
title: SQL Server PowerShell | Microsoft Docs
ms.custom: 
ms.date: 08/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89b70725-bbe7-4ffe-a27d-2a40005a97e7
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 2007b572b659f5fe9371618b667bb27a43bc70c8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-powershell"></a>SQL Server PowerShell
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge Windows PowerShell, un environnement de script puissant qui permet aux administrateurs et aux développeurs d'automatiser l'administration de serveurs et le déploiement d'applications. Le langage Windows PowerShell prend en charge une logique plus complexe que les scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] , ce qui permet aux administrateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de générer des scripts d'administration fiables. Les scripts Windows PowerShell peuvent également être utilisés pour administrer d'autres produits serveur [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Cela fournit aux administrateurs un langage de script commun entre les serveurs.  
  
## <a name="sql-server-powershell-components"></a>Composants de SQL Server PowerShell  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit un module Windows PowerShell nommé **sqlps** utilisé pour importer les composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un environnement ou un script Windows PowerShell. Le module **sqlps** charge deux composants logiciels enfichables Windows PowerShell qui implémentent les éléments suivants :  
  
-   Un fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , qui active un mécanisme de navigation simple semblable aux chemins d'accès de système de fichiers. Vous pouvez générer des chemins d'accès semblables aux chemins d'accès de système de fichiers, où le lecteur est associé à un modèle SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object) et les nœuds sont basés sur les classes du modèle objet. Vous pouvez ensuite utiliser des commandes familières telles que **cd** et **dir** pour naviguer parmi les chemins d’accès de la même façon que vous naviguez parmi des dossiers dans une fenêtre d’invite de commandes. Vous pouvez utiliser d’autres commandes, telles que **ren** ou **del**, pour exécuter des actions sur les nœuds du chemin d’accès.  
  
-   Un jeu d'applets de commande, qui sont des commandes utilisées dans les scripts Windows PowerShell pour spécifier une action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les applets de commande [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prennent en charge des actions telles que l’exécution d’un script **sqlcmd** contenant des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ou XQuery.  
  
 Pour en savoir plus sur Windows PowerShell, consultez [Prise en main de Windows PowerShell](https://msdn.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell).  
  
## <a name="sql-server-versions"></a>versions SQL Server  
 Les composants [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] PowerShell permettent de gérer des instances de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ou version ultérieure. Les instances de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] doivent exécuter SP2 ou ultérieur. Les instances de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] doivent exécuter SP4 ou ultérieur. Lorsque les composants [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] PowerShell sont utilisés avec des versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ils sont limités aux fonctionnalités disponible dans ces versions.  
     
## <a name="sql-server-powershell-tasks"></a>Tâches de SQL Server PowerShell  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------| 
|Installation des extensions Microsoft® Windows PowerShell pour Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  Les modules PowerShell sont installés par défaut lors de l’installation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Vous pouvez installer manuellement les extensions PowerShell pour SQL Server 2016 en installant les composants suivants à partir de Microsoft® SQL Server® 2016 Feature Pack :<br/>     Microsoft® System CLR Types pour Microsoft SQL Server® 2016 (SQLSysClrTypes.msi)<br/>Microsoft® SQL Server® 2016 Shared Management Objects (SharedManagementObjects.msi)<br/> Extensions Microsoft® Windows PowerShell pour Microsoft SQL Server® 2016 (PowerShellTools.msi)|[Microsoft® SQL Server® 2016 Feature Pack](https://www.microsoft.com/en-us/download/details.aspx?id=52676).   | 
|Décrit le mécanisme par défaut pour exécuter les composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, ouvrir une session PowerShell et charger le module **sqlps** . Le module **sqlps** charge le fournisseur et les applets de commande [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, ainsi que les assemblys SMO (SQL Server Management Object) utilisés par le fournisseur et les applets de commande.|[Importer le module SQLPS](../../relational-databases/scripting/import-the-sqlps-module.md)|  
|Explique comment charger uniquement les assemblys SMO sans fournisseur ni applet de commande.|[Charger les assemblys SMO dans Windows PowerShell](../../relational-databases/scripting/load-the-smo-assemblies-in-windows-powershell.md)|  
|Explique comment exécuter une session Windows PowerShell en cliquant avec le bouton droit sur un nœud dans l’ **Explorateur d’objets**. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] lance une session Windows Powershell, charge le module **sqlps** et affecte au chemin du fournisseur SQL Server l’objet sélectionné.|[Exécuter Windows PowerShell à partir de SQL Server Management Studio](../../relational-databases/scripting/run-windows-powershell-from-sql-server-management-studio.md)|  
|Explique comment créer les étapes d'un travail de l'Agent SQL Server qui exécutent un script Windows PowerShell. Les travaux peuvent ensuite être planifiés de manière à s'exécuter à des heures spécifiques ou en réponse à des événements.|[Utiliser Windows PowerShell dans les étapes de travail de l'Agent SQL Server](../../relational-databases/scripting/run-windows-powershell-steps-in-sql-server-agent.md)|  
|Explique comment utiliser le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour naviguer dans une hiérarchie d'objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[fournisseur PowerShell SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)|  
|Explique comment utiliser les applets de commande [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui spécifient des actions du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , telles que l'exécution d'un script [!INCLUDE[tsql](../../includes/tsql-md.md)] .|[Utiliser les applets de commande du Moteur de base de données](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)|  
|Explique comment spécifier des identificateurs délimités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui contiennent des caractères non pris en charge par Windows PowerShell.|[Identificateurs SQL Server dans PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)|  
|Explique comment établir des connexions d'authentification SQL Server. Par défaut, les composants SQL Server PowerShell utilisent des connexions d'authentification Windows à l'aide des informations d'identification Windows du processus exécutant Windows PowerShell.|[Gérer l'authentification dans le moteur de base de données PowerShell](../../relational-databases/scripting/manage-authentication-in-database-engine-powershell.md)|  
|Explique comment utiliser des variables implémentées par le fournisseur SQL Server PowerShell pour contrôler le nombre d'objets répertoriés lors de l'utilisation de la saisie semi-automatique par tabulation Windows PowerShell. Cela est particulièrement utile lorsque vous travaillez sur des bases de données qui contiennent un grand nombre d'objets.|[Gérer la saisie semi-automatique par tabulation &#40;SQL Server PowerShell&#41;](../../relational-databases/scripting/manage-tab-completion-sql-server-powershell.md)|  
|Explique comment utiliser Get-Help pour obtenir des informations sur les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l'environnement Windows PowerShell.|[Obtenir de l'aide sur SQL Server PowerShell](../../relational-databases/scripting/get-help-sql-server-powershell.md)|  
  
  
