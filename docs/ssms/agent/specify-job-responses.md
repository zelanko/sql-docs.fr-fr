---
description: Spécifier des réponses à un travail
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
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 24ac9bec23695d9838cf79df0b5f1ea483ee38b4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97408827"
---
# <a name="specify-job-responses"></a>Spécifier des réponses à un travail
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Les réponses à un travail spécifient les actions que le service Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réalisera après l'achèvement d'un travail. Les réponses à un travail garantissent que les administrateurs de base de données ont connaissance de l'achèvement des travaux et de leur fréquence d'exécution. Les réponses classiques à un travail peuvent être :  
  
-   Une notification de l’opérateur, à l’aide de l’e-mail, de la radiomessagerie ou d’un message **net send** .  
  
    Utilisez une de ces réponses à un travail si l'opérateur doit exécuter une action en conséquence. Par exemple, si un travail de sauvegarde se termine avec succès, l'opérateur doit être averti afin qu'il enlève la bande de sauvegarde et qu'il la mette en lieu sûr.  
  
-   L'écriture d'un message d'événement dans le journal des applications Windows.  
  
    Vous pouvez choisir d'utiliser cette réponse uniquement en cas d'échec des travaux.  
  
-   La suppression automatique du travail.  
  
    Utilisez cette réponse à un travail si vous êtes certain de ne plus avoir besoin d'exécuter ce travail à nouveau.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Description|Rubrique|  
|-|-|  
|Explique comment avertir un opérateur de l'état d'un travail.|[Notify an Operator of Job Status](../../ssms/agent/notify-an-operator-of-job-status.md)|  
|Explique comment écrire l'état du travail dans le journal des applications Windows.|[Write the Job Status to the Windows Application Log](../../ssms/agent/write-the-job-status-to-the-windows-application-log.md)|  
  
## <a name="see-also"></a>Voir aussi  
[Surveiller et répondre aux événements](../../ssms/agent/monitor-and-respond-to-events.md)  
