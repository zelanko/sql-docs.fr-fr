---
title: Spécifier un type d’abonnement de fusion et une priorité pour la résolution des conflits (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a19ae6246fe59308283fbaf2f35e2c49f96b140c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055555"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a>spécifier un type d'abonnement de fusion et une priorité pour la résolution des conflits (SQL Server Management Studio)
   Spécifiez un type d’abonnement de fusion et une priorité pour la résolution des conflits dans la page **Type d’abonnement** de l’Assistant Nouvel abonnement. Pour plus d'informations sur l'utilisation de cet Assistant, consultez [Create a Pull Subscription](create-a-pull-subscription.md) et [Create a Push Subscription](create-a-push-subscription.md).  
  
 Le type d’abonnement ne peut pas être modifié après la création d’un abonnement, mais la priorité peut être modifiée pour le type d’abonnement serveur dans la boîte de dialogue **Propriétés de l’abonnement- \<Publisher> : \<PublicationDatabase> ** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) et [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Pour spécifier un type d'abonnement de fusion et une priorité pour la résolution des conflits  
  
1.  Dans la page **Type d'abonnement** de l'Assistant Nouvel abonnement, sélectionnez **Client** ou **Serveur** pour l'option **Type d'abonnement** .  
  
2.  Si vous sélectionnez le type d'abonnement **Serveur**, affectez également une valeur (0,00 à 99,99) à l'option **Priorité pour la résolution des conflits** .  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>Pour modifier la priorité pour la résolution des conflits  
  
1.  Dans les **propriétés \<Publisher> \<PublicationDatabase> de l’abonnement** : sur le serveur de publication, entrez une valeur (0,00 à 99,99) pour l’option **priorité** .  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [S’abonner aux Publications](subscribe-to-publications.md)  
  
  
