---
title: PreConnect:Starting, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8e309d3783dab58e42f0be76badfa293d7ce872f
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67940684"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting, classe d'événements
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
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
  
  
