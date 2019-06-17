---
title: Créer des planifications et les attacher à des travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server]
- scheduling jobs [SQL Server]
- jobs [SQL Server], scheduling
- CPU [SQL Server], idle conditions
- automatic job processing
- SQL Server Agent jobs, scheduling
- idle time [SQL Server]
ms.assetid: 079c2984-0052-4a37-a2b8-4ece56e6b6b5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 414ff334139919e08b06291ec910f8531c70cd55
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63136285"
---
# <a name="create-and-attach-schedules-to-jobs"></a>Créer des planifications et les attacher à des travaux
  La planification des travaux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent consiste à définir la ou les conditions qui déclenchent leur exécution sans intervention de l'utilisateur. Vous pouvez planifier l'exécution automatique d'un travail en lui créant une planification ou en lui attachant une planification existante.  
  
 Il existe deux méthodes pour créer une planification :  
  
-   Créez la planification en même temps que vous créez un travail.  
  
-   Créez la planification dans l'Explorateur d'objets.  
  
 Une fois la planification créée, vous pouvez l'attacher à plusieurs travaux, même si elle a été conçue pour un travail spécifique. Vous pouvez également détacher une planification d'un travail.  
  
 Une planification peut être définie par rapport à une heure ou un événement. Par exemple, vous pouvez planifier l'exécution d'un travail aux moments suivants :  
  
-   au moment où l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre ;  
  
-   au moment où l'utilisation de l'UC atteint le niveau d'inactivité que vous avez défini ;  
  
-   ponctuellement, à une date et une heure spécifiques ;  
  
-   Selon une planification récurrente.  
  
 Vous pouvez remplacer vos planifications du travail par des alertes qui répondent à un événement par l'exécution d'un travail.  
  
> [!NOTE]  
>  Une seule instance du travail peut être exécutée à la fois. Si vous exécutez un travail manuellement alors qu'il est en train de s'exécuter d'après une planification, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] refuse la demande.  
  
 Pour empêcher l'exécution d'un travail planifié, vous devez effectuer l'une des opérations suivantes :  
  
-   désactiver la planification ;  
  
-   désactiver le travail ;  
  
-   détacher la planification du travail ;  
  
-   arrêter le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ;  
  
-   supprimer la planification.  
  
 Si la planification n'est pas activée, le travail peut toujours s'exécuter en réponse à une alerte ou lorsqu'un utilisateur l'exécute manuellement. Lorsqu'une planification du travail n'est pas activée, elle ne l'est pas pour aucun travail qui l'utilise normalement.  
  
 Une planification désactivée doit être réactivée de manière explicite. Le simple fait de modifier une planification ne la réactive pas automatiquement.  
  
## <a name="scheduling-start-dates"></a>Planification de dates de début  
 La date de début d'une planification doit être supérieure ou égale à 19900101.  
  
 Lorsque vous attachez une planification à un travail, vous devez examiner la date de début utilisée par la planification la première fois qu'elle exécute le travail. La date de début dépend du jour et de l'heure auxquels vous attachez la planification au travail. Par exemple, supposons que vous créez une planification qui s'exécute un lundi sur deux à 8h00. Si vous créez un travail à 10h00 le lundi 3 mars 2008, la date de début de la planification est le lundi 17 mars 2008. Si vous créez un autre travail le mardi 4 mars 2008, la date de début de la planification est le lundi 10 mars 2008.  
  
 Une fois la planification attachée à un travail, vous pouvez modifier sa date de début.  
  
## <a name="cpu-idle-schedules"></a>Planifications pendant l'inactivité de l'UC  
 Pour augmenter les ressources de l'UC, vous pouvez définir une condition d'inactivité de l'UC pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent utilise ce paramètre pour déterminer le meilleur moment pour l’exécution des travaux. Par exemple, vous pouvez planifier un travail de reconstruction des index lorsque l'UC est inactive et pendant des périodes de production moins chargées.  
  
 Avant de définir des travaux à exécuter pendant l'inactivité de l'UC, déterminez la charge de l'UC en situation d'utilisation normale. Pour ce faire, utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ou l'Analyseur de performances pour surveiller le trafic serveur et rassembler les statistiques. Ensuite, à l'aide des informations rassemblées, déterminez le pourcentage et la durée d'inactivité de l'UC.  
  
 Définissez l'inactivité de l'UC comme un pourcentage en dessous duquel l'utilisation de l'UC doit se maintenir pendant une période donnée. Définissez ensuite la durée. Lorsque le taux d'utilisation de l'UC reste inférieur au pourcentage spécifié pendant un certain temps (défini par l'utilisateur), l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] démarre tous les travaux dont l'exécution est planifiée aux moments d'inactivité de l'UC. Pour plus d’informations sur l’utilisation de [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ou de l’Analyseur de performances pour surveiller l’utilisation du processeur, consultez [analyse l’utilisation du processeur](../../relational-databases/performance-monitor/monitor-cpu-usage.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Description**|**Rubrique**|  
|Décrit la méthode à suivre pour créer la planification d'un travail [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|[Créer une planification](create-a-schedule.md)|  
|Décrit la méthode à suivre pour planifier un travail [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|[Planifier un travail](schedule-a-job.md)|  
|Indique comment définir la condition d'inactivité de l'UC pour votre serveur.|[Définir le seuil et la durée d’inactivité de l’UC &#40;SQL Server Management Studio&#41;](set-cpu-idle-time-and-duration-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_help_jobschedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql)   
 [dbo.sysjobschedules &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobschedules-transact-sql)  
  
  
