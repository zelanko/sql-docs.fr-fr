---
title: "Spécifier des réponses à un travail| Microsoft Docs"
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
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d2970e6ba2c2c3bc34436752beb7fa72834786c7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="specify-job-responses"></a>Spécifier des réponses à un travail
Les réponses à un travail spécifient les actions que le service Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] réalisera après l'achèvement d'un travail. Les réponses à un travail garantissent que les administrateurs de base de données ont connaissance de l'achèvement des travaux et de leur fréquence d'exécution. Les réponses classiques à un travail peuvent être :  
  
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
  

