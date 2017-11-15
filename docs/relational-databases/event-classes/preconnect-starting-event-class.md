---
title: "PreConnect:Starting, classe d’événements | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6113003d6939ee0df989c0ee763e438429ffdd88
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting, classe d'événements
  La classe d'événements  PreConnect:Starting indique quand un déclencheur LOGON ou la fonction classifieur du gouverneur de ressources commence à s'exécuter.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>Colonnes de données de la classe d'événements PreConnect:Starting  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|215|27|Non|  
|SPID|**int**|ID du processus serveur qui déclenche cet événement.|12|Oui|  
|EventSubClass|**int**|1 pour la fonction classifieur définie par l'utilisateur.|21|Oui|  
|StartTime|**datetime**|Heure de démarrage de la fonction classifieur définie par l'utilisateur.|14|Oui|  
|ObjectID|**int**|ID de l'objet classifieur défini par l'utilisateur.|22|Oui|  
|ObjectName|**nvarchar (256)**|Nom en deux parties de la fonction classifieur définie par l'utilisateur. Par exemple, dbo.classifier.|34|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)   
 [Classe d'événements PreConnect:Completed](../../relational-databases/event-classes/preconnect-completed-event-class.md)   
 [gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md)  
  
  
