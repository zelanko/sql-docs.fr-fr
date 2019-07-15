---
title: Fichiers gérant les solutions et les projets | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: f95bf24b01e8dde62b766f424f111c5acf7c7615
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67688266"
---
# <a name="files-that-manage-solutions-and-projects"></a>Fichiers gérant les solutions et les projets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 Cette rubrique décrit les types de fichiers propres à [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Par défaut, toutes les solutions et leurs projets sont créés dans \Mes documents\SQL Server Management Studio\Projects.  


## <a name="management-studio-solution-files"></a>Fichiers solutions Management Studio  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilise d’autres types de fichiers que [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] ou [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual Studio. Cela signifie que vous ne pouvez pas ouvrir une solution [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] ou dans Visual Studio. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Les fichiers solutions permettent à l’Explorateur de solutions d’afficher une interface graphique pour gérer vos fichiers.  
   
|Extension|Type de fichier|Description|Créé par|  
|-------------|-------------|---------------|--------------|  
|.ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Objet Solution|Fournit l’environnement avec des références à l’emplacement sur le disque des projets, des éléments de projets et de la solution [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a>Fichiers projet Management Studio  
À l'instar des solutions qui contiennent des fichiers solutions qui gèrent les objets d'une solution, les projets contiennent des fichiers projet. Le type de fichier projet créé par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour un projet dépend du modèle utilisé pour créer le projet. Le tableau ci-dessous décrit le type de fichier créé pour chaque projet.  
   
|Extension|Modèle de projet|  
|-------------|--------------------|  
|.ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Projet de script|  
|.ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] Projet de script|  
   
## <a name="location-of-solution-level-files"></a>Emplacement des fichiers de niveau solution  
Par défaut, les fichiers de niveau solution sont créés dans le répertoire physique du premier projet créé avec la solution. Vous pouvez spécifier un répertoire pour la solution lors de la création d'une solution ou lors de la création d'un nouveau projet.  
 
Si votre structure de répertoires est identique à la structure logique affichée dans l'Explorateur de solutions, il est plus facile de trouver et de partager les fichiers solutions et projet avec d'autres développeurs.  
   
## <a name="see-also"></a>Voir aussi  
[Gérer des fichiers avec encodage](../../ssms/solution/manage-files-with-encoding.md)  
[Fichiers divers](../../ssms/solution/miscellaneous-files.md)  
[Explorateur de solutions](../../ssms/solution/solution-explorer.md)  
[Solutions &#40;SQL Server Management Studio&#41;](../../ssms/solution/solutions-sql-server-management-studio.md)  
[Projets &#40;SQL Server Management Studio&#41;](../../ssms/solution/projects-sql-server-management-studio.md)  
[Contrôle de code source de l'Explorateur de solutions](https://msdn.microsoft.com/library/ms173879.aspx)  
  
