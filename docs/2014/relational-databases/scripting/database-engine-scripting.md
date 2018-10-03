---
title: Scripts du moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7bf36beb01ee7d31b78e6bdf06921bc460bcbbad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199209"
---
# <a name="database-engine-scripting"></a>Scripts du moteur de base de données
  Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] prend en charge l'environnement de script [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell pour gérer les instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et leurs objets. Vous pouvez également générer et exécuter des requêtes de [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui contiennent des éléments [!INCLUDE[tsql](../../includes/tsql-md.md)] et XQuery dans des environnements très similaires aux environnements de script.  
  
## <a name="sql-server-powershell"></a>SQL Server PowerShell  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut deux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composants logiciels enfichables PowerShell qui implémentent :  
  
-   Un fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell qui expose les hiérarchies du modèle objet de gestion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que chemins d'accès PowerShell semblables aux chemins d'accès de système de fichiers. Vous pouvez utiliser les classes du modèle objet de gestion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour gérer les objets représentés à chaque nœud du chemin d'accès.  
  
-   Un jeu d'applets de commande [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui implémentent des commandes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L’une des applets de commande est **Invoke-Sqlcmd**. Cela est utilisé pour exécuter [!INCLUDE[ssDE](../../includes/ssde-md.md)] interroger les scripts à exécuter avec le `sqlcmd` utilitaire.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit ces fonctionnalités pour exécuter PowerShell :  
  
-   Le module PowerShell **sqlps** qui peut être importé dans une session PowerShell. Le module charge ensuite les composants logiciels enfichables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez exécuter des commandes PowerShell appropriées de manière interactive. Vous pouvez exécuter des fichiers de script à l'aide d'une commande telle que .\MonDossier\MonScript.ps1.  
  
-   Les fichiers de script PowerShell peuvent être fournis en entrée à des étapes de travail de PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent qui exécutent les scripts selon des intervalles planifiés ou en réponse à des événements système.  
  
-   L’utilitaire **sqlps** qui démarre PowerShell et importe le module [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez ensuite effectuer toutes les actions prises en charge par le module. Vous pouvez démarrer l’utilitaire **sqlps** dans une invite de commandes ou en cliquant avec le bouton droit sur les nœuds dans l’arborescence de l’Explorateur d’objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio et en sélectionnant **Démarrer PowerShell**.  
  
## <a name="database-engine-queries"></a>Requêtes de moteur de base de données  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Les scripts de requêtes contiennent trois types d’éléments :  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] Instructions du langage  
  
-   Instructions du langage XQuery  
  
-   Commandes et variables de la `sqlcmd` utilitaire.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit trois environnements pour la génération et l’exécution de requêtes du [!INCLUDE[ssDE](../../includes/ssde-md.md)] :  
  
-   Vous pouvez, de manière interactive, exécuter et déboguer des requêtes de [!INCLUDE[ssDE](../../includes/ssde-md.md)] dans l'éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez coder et déboguer plusieurs instructions en une session, puis enregistrer toutes les instructions dans un même fichier de script.  
  
-   Le `sqlcmd` utilitaire d’invite de commandes vous permet d’exécuter de manière interactive [!INCLUDE[ssDE](../../includes/ssde-md.md)] requêtes et exécution existant aussi [!INCLUDE[ssDE](../../includes/ssde-md.md)] interroger des fichiers de script.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Les fichiers de script de requête sont en général codés de manière interactive dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en utilisant l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Le fichier peut par la suite être ouvert dans l'un de ces environnements :  
  
-   Utilisez le menu [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Ouvrir**/**de** pour ouvrir le fichier dans une nouvelle fenêtre de l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   Utilisez le **i-*** input_file* paramètre pour exécuter le fichier avec le `sqlcmd` utilitaire.  
  
-   Utilisez le paramètre **-QueryFromFile** pour exécuter le fichier avec l’applet de commande **Invoke-Sqlcmd** dans les scripts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.  
  
-   Utilisez des étapes de travail [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] pour exécuter des scripts selon des intervalles planifiés ou en réponse à des événements système.  
  
 En outre, vous pouvez utiliser l’Assistant Génération de scripts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour générer des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] . Vous pouvez cliquer avec le bouton droit sur des objets dans l’Explorateur d’objets [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , puis sélectionner l’élément de menu **Générer un script** . **Générer un script** lance l’Assistant, qui vous guide dans le processus de création d’un script.  
  
## <a name="database-engine-scripting-tasks"></a>Tâches de script du moteur de base de données  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Explique comment utiliser le code et les éditeurs de texte dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour développer, déboguer, et exécuter interactivement des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] .|[Éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|Décrit comment utiliser le `sqlcmd` afin d’exécuter [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts à partir de l’invite de commandes, y compris la possibilité de développer interactivement des scripts.|[Rubriques de procédures liées à sqlcmd](../../database-engine/sqlcmd-how-to-topics.md)|  
|Explique comment intégrer les composants SQL Server dans un environnement Windows PowerShell 2.0 et générer des scripts PowerShell pour gérer des instances et des objets SQL Server.|[SQL Server PowerShell](../../powershell/sql-server-powershell.md)|  
|Explique comment utiliser l’Assistant **Générer et publier des scripts** pour créer des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] qui recréent un ou plusieurs objets d’une base de données.|[Générer des scripts &#40;SQL Server Management Studio&#41;](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [Didacticiel : écriture d'instructions Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
