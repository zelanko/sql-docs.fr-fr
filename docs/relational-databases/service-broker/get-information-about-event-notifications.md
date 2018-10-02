---
title: Obtenir des informations concernant les notifications d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f789212398759dc7daf23b1651b27c2051e961ea
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47638077"
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
  
  
