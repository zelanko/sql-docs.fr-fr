---
title: Gérer plusieurs étapes de travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- ordering job steps [SQL Server]
- multiple job steps
- SQL Server Agent jobs, job steps
- control of flow for jobs [SQL Server]
ms.assetid: 7aba19ff-72b3-45f6-8e54-23f4988d63a8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 379877d3a08c60a293b96c5c57d55a2894ba0a79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63074049"
---
# <a name="handle-multiple-job-steps"></a>Gérer plusieurs étapes de travail
  Si votre travail est composé de plusieurs étapes, vous devez spécifier l'ordre dans lequel celles-ci sont exécutées. C’est ce que l’on appelle *le contrôle du Flow * *.* Vous pouvez ajouter de nouvelles étapes de travail et réorganiser le flux des étapes de travail à tout moment ; les modifications prennent effet lors de l'exécution suivante du travail. Cette illustration montre le contrôle de flux pour un travail de sauvegarde de base de données.  
  
 ![Contrôle du flux des étapes du travail de SQL Server Agent](../../database-engine/media/dbflow01.gif "Contrôle du flux des étapes du travail de SQL Server Agent")  
  
 La première étape est la sauvegarde de la base de données. Si cette étape échoue, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] signale l'échec à l'opérateur destinataire des notifications. Si l'étape de la sauvegarde de la base de données réussit, le travail se poursuit avec l'étape suivante, en l'occurrence la purge des données client. Si cette étape échoue, l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] passe à l'étape de restauration de la base de données. Si la purge des données client réussit, le travail se poursuit avec l'étape suivante, en l'occurrence la mise à jour des statistiques, et ainsi de suite jusqu'à la dernière étape, qui se solde par la réussite ou par l'échec du rapport.  
  
 Vous définissez une action de contrôle de flux pour la réussite ou l'échec de chaque étape de travail. Vous devez préciser l'action à exécuter lors de la réussite ou de l'échec d'une étape de travail. Vous pouvez également définir le nombre de tentatives de reprises pour les étapes de travail ayant échoué ainsi que leurs intervalles.  
  
> [!NOTE]  
>  Lorsque vous utilisez l'interface graphique utilisateur de l'agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et que vous supprimez une ou plusieurs étapes à partir d'un travail multitâches, l'interface supprime toutes les étapes de travail puis rajoute les étapes restantes avec les références correctes en cas de réussite ou en cas d'échec. Par exemple, supposons que vous avez un travail comportant cinq étapes, et que la première étape est configurée pour passer à l'étape 4 si elle aboutit. Si vous supprimez l'étape 3, l'interface utilisateur graphique supprime toutes les étapes de ce travail et ajoute les quatre étapes restantes (1, 2, 4 et 5) avec les références corrigées. Dans ce cas, la référence de l'étape 1 est configurée pour passer à l'étape 3 si l'étape 1 aboutit.  
  
 Les étapes de travail doivent être autonomes. En d'autres termes, un travail ne peut pas passer des valeurs booléennes, des données ou des valeurs numériques entre des étapes de travail. Toutefois, vous pouvez passer des valeurs d'une étape de travail [!INCLUDE[tsql](../../includes/tsql-md.md)] à une autre en utilisant des tables permanentes ou des tables temporaires globales. À partir des étapes de travail, vous pouvez transmettre des valeurs afin d'exécuter, d'une étape à l'autre, des programmes qui effectuent des opérations sur des fichiers. Par exemple, le programme exécuté par une étape de travail écrit un fichier, tandis que celui exécuté par une étape de travail ultérieure le lit.  
  
> [!NOTE]  
>  Si vous créez des étapes de travail en boucle, (l'étape de travail 1 est suivie par l'étape de travail 2, puis l'étape de travail 2 revient à l'étape de travail 1), un message d'avertissement apparaît lors de la création du travail avec [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent enregistre dans l’historique des travaux les informations relatives aux travaux et aux étapes de travail.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)   
 [dbo. sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)   
 [dbo. sysjobs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql)   
 [dbo. sysjobsteps &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql)   
 [Implémenter des travaux](implement-jobs.md)   
 [Gérer les étapes de travail](manage-job-steps.md)  
  
  
