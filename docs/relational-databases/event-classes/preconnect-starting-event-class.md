---
title: PreConnect:Starting, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 8e7ebac1a39218aaa8aa962bba8fb038a5694d62
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39532939"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting, classe d'événements
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La classe d'événements  PreConnect:Starting indique quand un déclencheur LOGON ou la fonction classifieur du gouverneur de ressources commence à s'exécuter.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>Colonnes de données de la classe d'événements PreConnect:Starting  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**Int**|215|27|non|  
|SPID|**Int**|ID du processus serveur qui déclenche cet événement.|12|Oui|  
|EventSubClass|**Int**|1 pour la fonction classifieur définie par l'utilisateur.|21|Oui|  
|StartTime|**datetime**|Heure de démarrage de la fonction classifieur définie par l'utilisateur.|14|Oui|  
|ObjectID|**Int**|ID de l'objet classifieur défini par l'utilisateur.|22|Oui|  
|ObjectName|**nvarchar (256)**|Nom en deux parties de la fonction classifieur définie par l'utilisateur. Par exemple, dbo.classifier.|34|Oui|  
  
## <a name="see-also"></a> Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)   
 [Classe d'événements PreConnect:Completed](../../relational-databases/event-classes/preconnect-completed-event-class.md)   
 [gouverneur de ressources](../../relational-databases/resource-governor/resource-governor.md)  
  
  
