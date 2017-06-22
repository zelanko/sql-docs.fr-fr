---
title: "Enlever ou supprimer un élément ou un projet | Microsoft Docs"
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
- deleting project items
- projects [SQL Server Management Studio], item removal
- removing project items
ms.assetid: 3fd92434-70f5-466e-bef0-7e0fd73ddb1c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b09e3ba21b75c91b4ceb5deb70379d60b644e49d
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="remove-or-delete-an-item-or-project"></a>Enlever ou supprimer un élément ou un projet
Les éléments de projet des projets [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] sont les requêtes, les connexions et les fichiers divers. Vous pouvez enlever des requêtes et des fichiers divers de projet d'une solution sans effacer du support de stockage les fichiers. Supprimez un projet ou un élément lorsqu'il n'est plus utile dans la solution en cours mais que vous souhaitez l'insérer dans une autre solution.  
  
### <a name="to-remove-a-project-item"></a>Pour supprimer un élément de projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez l'élément de projet à enlever.  
  
2.  Dans le menu **Edition** , cliquez sur **Enlever**.  
  
3.  Dans la boîte de dialogue de confirmation, cliquez sur **Enlever** pour enlever l’élément du projet.  
  
Un élément enlevé existe toujours dans le système de fichiers. Par conséquent, après avoir enlevé un élément, vous pouvez toujours l'ajouter à sa solution initiale ou à une autre solution.  
  
#### <a name="to-remove-a-project"></a>Pour enlever un projet  
  
1.  Dans l'Explorateur de solutions, sélectionnez le projet à enlever.  
  
2.  Dans le menu **Edition** , cliquez sur **Enlever**.  
  
3.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**pour enlever le projet de la solution.  
  
Vous pouvez supprimer de façon permanente un projet, mais vous devez d'abord enlever les références au projet des solutions [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] , puis utiliser l'Explorateur [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows pour supprimer définitivement du système de stockage les fichiers associés.  
  
#### <a name="to-delete-a-project"></a>Pour supprimer un projet  
  
1.  Dans l'Explorateur de solutions, enlevez le projet que vous souhaitez supprimer de la solution.  
  
2.  Dans l'Explorateur Windows, recherchez et sélectionnez les fichiers associés au projet ou à l'élément que vous souhaitez supprimer.  
  
3.  Dans le menu **Fichier** , cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
[Explorateur de solutions](../../ssms/solution/solution-explorer.md)  
[Ajouter de nouveaux éléments à un projet](../../ssms/solution/add-new-items-to-a-project.md)  
[Ajouter des éléments existants à un projet](../../ssms/solution/add-existing-items-to-a-project.md)  
  

