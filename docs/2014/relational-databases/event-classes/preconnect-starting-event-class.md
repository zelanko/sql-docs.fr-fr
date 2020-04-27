---
title: PreConnect:Starting, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0986e654430a47cc494bf1646c222b4888fc105b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033511"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting, classe d'événements
  La classe d'événements  PreConnect:Starting indique quand un déclencheur LOGON ou la fonction classifieur du gouverneur de ressources commence à s'exécuter.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>Colonnes de données de la classe d'événements PreConnect:Starting  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|215|27|Non|  
|SPID|`int`|ID du processus serveur qui déclenche cet événement.|12|Oui|  
|EventSubClass|`int`|1 pour la fonction classifieur définie par l'utilisateur.|21|Oui|  
|StartTime|`datetime`|Heure de démarrage de la fonction classifieur définie par l'utilisateur.|14|Oui|  
|ObjectID|`int`|ID de l'objet classifieur défini par l'utilisateur.|22|Oui|  
|ObjectName|`nvarchar(256)`|Nom en deux parties de la fonction classifieur définie par l'utilisateur. Par exemple, dbo.classifier.|34|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [PreConnect : Completed, classe d’événements](preconnect-completed-event-class.md)   
 [gouverneur de ressources](../resource-governor/resource-governor.md)  
  
  
