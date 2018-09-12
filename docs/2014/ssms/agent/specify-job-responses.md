---
title: Spécifier des réponses à un travail| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d914f36b216bfd49d45e22a259af8df4c781e1b
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43809485"
---
# <a name="specify-job-responses"></a>Spécifier des réponses à un travail
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
|Explique comment avertir un opérateur de l'état d'un travail.|[Notifier l’état d’un travail à un opérateur](notify-an-operator-of-job-status.md)|  
|Explique comment écrire l'état du travail dans le journal des applications Windows.|[Écrire l'état du travail dans le journal des applications Windows](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et répondre aux événements](monitor-and-respond-to-events.md)  
  
  
