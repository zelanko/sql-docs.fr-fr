---
title: Afficher ou modifier les travaux | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d0d731d25c20597be3ac84adfacd8973e4a51cd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85001709"
---
# <a name="view-or-modify-jobs"></a>Afficher ou modifier les travaux
  Vous pouvez afficher tout travail que vous avez créé. Après avoir exécuté un travail, vous pouvez également afficher son historique. L'affichage de l'historique d'un travail vous permet de déterminer le moment de son exécution, l'état du travail dans son ensemble et l'état de chaque étape du travail. Il permet également de savoir si le travail a déjà échoué dans le passé, si sa dernière exécution s'est terminée correctement, ainsi que les résultats qu'il a générés à chaque exécution. Les membres du rôle serveur fixe **sysadmin** peuvent afficher ou modifier n’importe quel travail, quel que soit son propriétaire.  
  
> [!NOTE]  
>  Le travail doit avoir été exécuté au moins une fois pour qu'un historique des travaux existe. Vous pouvez limiter la taille totale du journal d'historique des travaux et la taille par travail.  
  
 Enfin, vous pouvez modifier un travail pour qu'il réponde aux nouvelles exigences. Vous pouvez modifier :  
  
-   les options de réponse ;  
  
-   Planifications  
  
-   Étapes de travail  
  
-   Propriété  
  
-   la catégorie du travail ;  
  
-   les serveurs cibles (travaux multiserveur uniquement).  
  
 Pour être certain que les modifications apportées aux travaux multiserveur entrent en vigueur, vous devez les publier dans la liste de téléchargement afin que les serveurs cibles puissent télécharger le travail mis à jour. Pour vérifier que les serveurs cibles possèdent les définitions des travaux les plus récentes, publiez une instruction INSERT une fois le travail multiserveur mis à jour en procédant comme suit :  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 Pour plus d’informations, consultez [sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql).  
  
 Les membres du rôle serveur fixe **sysadmin** peuvent afficher la définition ou l’historique de n’importe quel travail, ainsi que modifier tout travail.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Description**|**Rubrique**|  
|Explique comment afficher des travaux [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.|[View a Job](view-a-job.md)|  
|Explique comment afficher le journal d’historique des travaux [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.|[Afficher l’historique des travaux](view-the-job-history.md)|  
|Explique comment supprimer le contenu du journal d’historique des travaux [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.|[Effacer le journal d'historique des travaux](clear-the-job-history-log.md)|  
|Explique comment définir des limites de taille dans les journaux d’historique des travaux [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.|[Resize the Job History Log](resize-the-job-history-log.md)|  
|Explique comment modifier les propriétés des travaux [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.|[Modifier un travail](modify-a-job.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [dbo.sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql)  
  
  
