---
title: "CPU Threshold Exceeded, classe d’événements | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 435ae4a32337b62b2a93ea942936acf21ee35871
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="cpu-threshold-exceeded-event-class"></a>Classe d'événements CPU Threshold Exceeded
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] La classe d’événements CPU Threshold Exceeded indique que Resource Governor détecte une requête qui dépasse le seuil de l’UC spécifié pour REQUEST_MAX_CPU_TIME_SEC.  
  
> [!NOTE]  
>  L'intervalle de détection pour cet événement est cinq secondes. Il est garanti qu'un événement sera généré si une requête dépasse la limite spécifiée d'au moins cinq secondes. Toutefois, si une requête dépasse le seuil spécifié de moins de cinq secondes, sa détection peut être manquée selon le moment d'exécution de la requête et l'heure de la dernière analyse de détection.  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>Colonnes de données CPU Threshold Exceeded  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|Unité centrale|**int**|Utilisation de l'UC en millisecondes.|18|Oui|  
|EventClass|**int**|214|27|Non|  
|EventSubClass|**int**|Violation de la limite de l'UC.|21|Oui|  
|GroupID|**int**|ID de groupe où la violation s'est produite.|66|Oui|  
|OwnerID|**int**|SPID du processus qui a provoqué la violation.|58|Oui|  
|SPID|**int**|ID du processus serveur qui déclenche cet événement.<br /><br /> Remarque : il peut être différent du SPID de l’utilisateur réel si un thread système valide l’utilisation de l’UC comme une tâche en arrière-plan.|12|Oui|  
|StartTime|**datetime**|Heure de déclenchement de cet événement.|14|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
