---
title: Spécifier un type et une priorité pour la résolution des conflits (Fusion)
description: Découvrez comment spécifier le type et la stratégie de résolution des conflits utilisés par un abonnement de fusion dans SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2981f84bd2cbf6c813a4adf761ddd271c8b68fd1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737049"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Spécifier un type d’abonnement de fusion et une priorité pour la résolution des conflits
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Spécifiez un type d'abonnement de fusion et une priorité pour la résolution des conflits dans la page **Type d'abonnement** de l'Assistant Nouvel abonnement. Pour plus d'informations sur l'utilisation de cet Assistant, consultez [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) et [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
 Le type d'abonnement ne peut pas être modifié après la création d'un abonnement, mais la priorité peut être modifiée pour le type d'abonnement serveur dans la **boîte de dialogue Propriétés de l'abonnement - \<Publisher>: \<PublicationDatabase>** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) et [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Pour spécifier un type d'abonnement de fusion et une priorité pour la résolution des conflits  
  
1.  Dans la page **Type d'abonnement** de l'Assistant Nouvel abonnement, sélectionnez **Client** ou **Serveur** pour l'option **Type d'abonnement** .  
  
2.  Si vous sélectionnez le type d'abonnement **Serveur**, affectez également une valeur (0,00 à 99,99) à l'option **Priorité pour la résolution des conflits** .  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>Pour modifier la priorité pour la résolution des conflits  
  
1.  Dans la boîte de dialogue **Propriétés de l'abonnement - \<Publisher>: \<PublicationDatabase>** sur le serveur de publication, affectez une valeur (de 0,00 à 99,99) à l'option **Priorité**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Détection et résolution des conflits de réplication de fusion avancée](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
