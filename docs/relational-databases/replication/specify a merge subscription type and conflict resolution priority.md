---
title: "sp&#233;cifier un type d&#39;abonnement de fusion et une priorit&#233; pour la r&#233;solution des conflits (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "résolution des conflits de réplication de fusion [réplication SQL Server], résolveurs d’abonnements de fusion"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# sp&#233;cifier un type d&#39;abonnement de fusion et une priorit&#233; pour la r&#233;solution des conflits (SQL Server Management Studio)
  Spécifiez un type d'abonnement de fusion et une priorité pour la résolution des conflits dans la page **Type d'abonnement** de l'Assistant Nouvel abonnement. Pour plus d'informations sur l'utilisation de cet Assistant, consultez [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) et [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
 Type d’abonnement ne peut pas être modifié après la création d’un abonnement, mais la priorité peut être modifiée pour le type d’abonnement serveur dans le **Propriétés de l’abonnement - \< serveur de publication>: \< Basedonnéespublication>** boîte de dialogue. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) et [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
### Pour spécifier un type d'abonnement de fusion et une priorité pour la résolution des conflits  
  
1.  Dans la page **Type d'abonnement** de l'Assistant Nouvel abonnement, sélectionnez **Client** ou **Serveur** pour l'option **Type d'abonnement** .  
  
2.  Si vous sélectionnez un type d’abonnement de **Server**, également entrer une valeur (0,00 à 99,99) pour le **priorité pour la résolution de conflit** option.  
  
### Pour modifier la priorité pour la résolution des conflits  
  
1.  Dans la **Propriétés de l’abonnement - \< serveur de publication>: \< Basedonnéespublication>** sur le serveur de publication, entrez une valeur (0,00 à 99,99) pour le **priorité** option.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  