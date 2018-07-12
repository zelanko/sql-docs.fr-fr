---
title: CPU Threshold Exceeded, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7883dff5b548ad0b6903934c4dd8d90be8cf2423
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164683"
---
# <a name="cpu-threshold-exceeded-event-class"></a>Classe d'événements CPU Threshold Exceeded
  La classe d'événements CPU Threshold Exceeded indique que Resource Governor détecte une requête qui dépasse le seuil de l'UC spécifié pour REQUEST_MAX_CPU_TIME_SEC.  
  
> [!NOTE]  
>  L'intervalle de détection pour cet événement est cinq secondes. Il est garanti qu'un événement sera généré si une requête dépasse la limite spécifiée d'au moins cinq secondes. Toutefois, si une requête dépasse le seuil spécifié de moins de cinq secondes, sa détection peut être manquée selon le moment d'exécution de la requête et l'heure de la dernière analyse de détection.  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>Colonnes de données CPU Threshold Exceeded  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|Unité centrale|`int`|Utilisation de l'UC en millisecondes.|18|Oui|  
|EventClass|`int`|214|27|non|  
|EventSubClass|`int`|Violation de la limite de l'UC.|21|Oui|  
|GroupID|`int`|ID de groupe où la violation s'est produite.|66|Oui|  
|OwnerID|`int`|SPID du processus qui a provoqué la violation.|58|Oui|  
|SPID|`int`|ID du processus serveur qui déclenche cet événement.<br /><br /> Remarque : il peut être différent du SPID de l’utilisateur réel si un thread système valide l’utilisation de l’UC comme une tâche en arrière-plan.|12|Oui|  
|StartTime|`datetime`|Heure de déclenchement de cet événement.|14|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
