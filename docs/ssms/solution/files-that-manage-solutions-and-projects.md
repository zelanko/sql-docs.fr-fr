---
title: "Fichiers gérant les solutions et les projets | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 13c811a0c616a9ef859e86c688804c829ec0d9f0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="files-that-manage-solutions-and-projects"></a>Fichiers gérant les solutions et les projets
 <a name="-this-topic-describes-the-file-types-that-are-specific-to-includemsconameincludesmsconamemdmd-includessmanstudiofullincludesssmanstudiofullmdmd-by-default-all-solutions-and-their-projects-are-created-in-my-documentssql-server-management-studio-projects"></a>- Cette rubrique décrit les types de fichiers spécifiques de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Par défaut, toutes les solutions et leurs projets sont créés dans \Mes documents\SQL Server Management Studio\Projects.  
 -  
 -## Fichiers solution de Management Studio  
 -[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] utilise d’autres types de fichiers que [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] ou que [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual Studio. Cela signifie que vous ne pouvez pas ouvrir une solution [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] ou dans Visual Studio. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] Les fichiers solutions permettent à l’Explorateur de solutions d’afficher une interface graphique pour gérer vos fichiers.  
 -  
 -|Extension|Type de fichier|Description|Créé par|  
 -|-------------|-------------|---------------|--------------|  
 -|.ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] Objet Solution|Fournit l’environnement avec des références à l’emplacement sur le disque des projets, des éléments de projets et de la solution [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]|  
 -  
 -## Fichiers projet de Management Studio  
 - À l’instar des solutions contenant des fichiers solution qui gèrent les objets d’une solution, les projets contiennent des fichiers projet. Le type de fichier projet créé par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] pour un projet dépend du modèle utilisé pour créer le projet. Le tableau ci-dessous décrit le type de fichier créé pour chaque projet.  
 -  
 -|Extension|Modèle de projet|  
 -|-------------|--------------------|  
 -|.ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Projet de script|  
 -|.ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] Projet de script|  
 -  
 -## Emplacement des fichiers de niveau solution  
 - Par défaut, les fichiers de niveau solution sont créés dans le répertoire physique du premier projet créé avec la solution. Vous pouvez spécifier un répertoire pour la solution lors de la création d'une solution ou lors de la création d'un nouveau projet.  
 -  
 - Si votre structure de répertoires est similaire à la structure logique affichée dans l’Explorateur de solutions, il est plus facile de trouver et de partager les fichiers solutions et projet avec les autres développeurs d’une équipe.  
 -  
 -## Voir aussi  
 -[Gérer des fichiers avec encodage](../../ssms/solution/manage-files-with-encoding.md)  
 -[Fichiers divers](../../ssms/solution/miscellaneous-files.md)  
 -[Explorateur de solutions](../../ssms/solution/solution-explorer.md)  
 -[Solutions &#40;SQL Server Management Studio&#41;](../../ssms/solution/solutions-sql-server-management-studio.md)  
 -[Projets &#40;SQL Server Management Studio&#41;](../../ssms/solution/projects-sql-server-management-studio.md)  
 -[Contrôle de code source de l’Explorateur de solutions](https://msdn.microsoft.com/en-us/library/ms173879.aspx)  
  
