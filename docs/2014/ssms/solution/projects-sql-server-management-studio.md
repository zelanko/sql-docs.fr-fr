---
title: Projets (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 85bc34af971db386862528ac36ea04fef33f2daa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63035671"
---
# <a name="projects-sql-server-management-studio"></a>Projets (SQL Server Management Studio)
  Un projet [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] est une collection de scripts et de fichiers associés de façon logique qui peuvent être enregistrés ensemble en vue de l'administration et du développement d'une base de données.  
  
## <a name="script-project-overview"></a>Vue d'ensemble des projets de script  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont affichés dans le composant Explorateur de solutions de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Une projet de script peut contenir aucun ou plusieurs fichiers de projet. Vous pouvez ajouter un projet à une solution ou combiner plusieurs projets dans une solution.  
  
 Les projets peuvent être les suivants :  
  
-   **Connexions**. Une connexion, si elle est persistante dans un projet, contient les informations de connexion, le nom du serveur, la base de données par défaut, le protocole préféré, le type d'authentification et les propriétés de connexion. Les informations de connexion peuvent être éventuellement stockées dans un script (voir ci-dessous).  
  
-   **SQLScripts**. Scripts SQL couramment utilisés par l'utilisateur. Un double-clic sur un fichier .sql du projet entraîne l'ouverture du script sélectionné par l'Éditeur SQL.  
  
-   **Scripts MDX, DMX et XMLA**. Scripts MDX couramment utilisés par l'utilisateur. Un double-clic sur un fichier .mdx du projet entraîne l'ouverture du script sélectionné par l'Éditeur.  
  
-   **Divers**. Ce dossier permet de stocker les fichiers qui n'entrent pas dans le cadre des autres types de nœuds par défaut, tels qu'un fichier texte qui contient les objectifs du projet.  
  
 Les projets peuvent également être intégrés à un système de contrôle de code source.  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a>Connexion à une instance de SQL Server à partir d'un projet de script  
 Un projet de script peut contenir des connexions à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un projet en cliquant sur la connexion. La fenêtre Script SQL connectée à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définie dans la connexion sélectionnée s'ouvre alors. Si vous ouvrez un script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou MDX avec une connexion qui utilise l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le système vous demande de fournir le mot de passe dans la boîte de dialogue **Connexion à SQL Server** après le lancement de l'éditeur et le chargement du script.  
  
 La connexion sera fermée dès que la fenêtre correspondante l'aura elle-même été.  
  
 Pour modifier les informations sur une connexion, utilisez la fenêtre Propriétés de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## <a name="project-tasks"></a>Tâches du projet  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Explique comment créer un projet dans une solution.|[Créer un projet](create-a-project.md)|  
|Explique comment ajouter un projet existant à une solution.|[Ajouter un projet existant à une solution](add-an-existing-project-to-a-solution.md)|  
|Explique comment modifier l'emplacement par défaut dans lequel les fichiers du projet sont enregistrés.|[Modifier l'emplacement par défaut des projets](change-the-default-location-for-projects.md)|  
|Explique comment afficher les propriétés actuelles d'un projet.|[Afficher les propriétés d'un projet](view-project-properties.md)|  
|Explique comment ajouter de nouveaux éléments, tels que des connexions ou des fichiers de script, à un projet.|[Ajouter de nouveaux éléments à un projet](add-new-items-to-a-project.md)|  
|Explique comment établir les informations de connexion d'une requête.|[Associer une requête à une connexion dans un projet](associate-a-query-with-a-connection-in-a-project.md)|  
|Explique comment modifier les informations de connexion d'une requête.|[Modifier la connexion associée à une requête](change-the-connection-associated-with-a-query.md)|  
|Explique comment modifier les propriétés de connexion.|[Afficher ou modifier les propriétés d'une connexion dans un projet](view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Explorateur de solutions](solution-explorer.md)   
 [Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [Contrôle de code source de l'Explorateur de solutions](../../database-engine/solution-explorer-source-control.md)  
  
  
