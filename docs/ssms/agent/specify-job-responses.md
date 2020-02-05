---
title: Spécifier des réponses à un travail
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3208c2543292fd67ec36ad25dd5a065e08988ca6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245789"
---
# <a name="specify-job-responses"></a>Spécifier des réponses à un travail
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Les réponses à un travail spécifient les actions que le service Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réalisera après l'achèvement d'un travail. Les réponses à un travail garantissent que les administrateurs de base de données ont connaissance de l'achèvement des travaux et de leur fréquence d'exécution. Les réponses classiques à un travail peuvent être :  
  
-   Une notification de l’opérateur, à l’aide de l’e-mail, de la radiomessagerie ou d’un message **net send** .  
  
    Utilisez une de ces réponses à un travail si l'opérateur doit exécuter une action en conséquence. Par exemple, si un travail de sauvegarde se termine avec succès, l'opérateur doit être averti afin qu'il enlève la bande de sauvegarde et qu'il la mette en lieu sûr.  
  
-   L'écriture d'un message d'événement dans le journal des applications Windows.  
  
    Vous pouvez choisir d'utiliser cette réponse uniquement en cas d'échec des travaux.  
  
-   La suppression automatique du travail.  
  
    Utilisez cette réponse à un travail si vous êtes certain de ne plus avoir besoin d'exécuter ce travail à nouveau.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Description**|**Rubrique**|  
|Explique comment avertir un opérateur de l'état d'un travail.|[Notifier l’état d’un travail à un opérateur](../../ssms/agent/notify-an-operator-of-job-status.md)|  
|Explique comment écrire l'état du travail dans le journal des applications Windows.|[Écrire l'état du travail dans le journal des applications Windows](../../ssms/agent/write-the-job-status-to-the-windows-application-log.md)|  
  
## <a name="see-also"></a>Voir aussi  
[Surveiller et répondre aux événements](../../ssms/agent/monitor-and-respond-to-events.md)  
  
