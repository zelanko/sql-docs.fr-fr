---
title: "Obtenir des informations concernant les notifications d’événements | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: service-broker
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1ef3efe96a38e594a945653ca08469811e813340
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="get-information-about-event-notifications"></a>Obtenir des informations concernant les notifications d'événements
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les affichages catalogue suivants vous permettent d'interroger les métadonnées concernant les notifications d'événements.  
  
 **Pour obtenir des informations sur les notifications d'événements qui ne se produisent pas au niveau du serveur**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Pour afficher les métadonnées sur une notification d’événement dans l’affichage catalogue **sys.event_notifications** créée au niveau de la base de données, vous devez au moins disposer de l’autorisation CONTROL, ALTER, TAKE OWNERSHIP ou VIEW DEFINITION sur la base de données, être propriétaire de la notification d’événement ou disposer de l’autorisation ALTER ANY DATABASE EVENT NOTIFICATION. Pour les notifications d'événements créées sur une file d'attente spécifique, vous devez au moins disposer de l'autorisation CONTROL, ALTER, TAKE OWNERSHIP ou VIEW DEFINITION sur l'objet, être propriétaire de la notification d'événement ou disposer de l'autorisation ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **Pour obtenir des informations sur les notifications d'événements qui se produisent au niveau du serveur**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Vous devez au moins disposer de l’autorisation CONTROL ou VIEW ANY DEFINITION sur le serveur, être la connexion ou le propriétaire de la notification d’événement ou disposer de l’autorisation ALTER ANY EVENT NOTIFICATION pour afficher les métadonnées concernant toute notification d’événement dans **sys.server_event_notifications**.  
  
 **Pour obtenir des informations sur tous les événements pouvant déclencher des notifications**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql.md)  
  
> [!NOTE]  
>  Cette vue de catalogue ne retourne pas de groupes d'événements.  
  
## <a name="see-also"></a> Voir aussi  
 [Notifications d'événements](../../relational-databases/service-broker/event-notifications.md)  
  
  
