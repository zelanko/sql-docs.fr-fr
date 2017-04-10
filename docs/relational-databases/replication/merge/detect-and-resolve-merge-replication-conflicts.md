---
title: "D&#233;tecter et r&#233;soudre de conflits de r&#233;plication de fusion | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "résolution des conflits de réplication de fusion [réplication SQL Server], à propos de la résolution des conflits"
  - "résolveur de conflits par défaut"
  - "résolution de conflits [SQL Server replication]"
  - "affichage des conflits de réplication de fusion"
  - "résolution des conflits de réplication de fusion"
  - "articles [réplication SQL Server], résolution des conflits"
  - "résolution des conflits de réplication de fusion [réplication SQL Server]"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# D&#233;tecter et r&#233;soudre de conflits de r&#233;plication de fusion
  Lorsqu'un serveur de publication et un Abonné sont connectés et que la synchronisation se produit, l'Agent de fusion détecte la présence d'éventuels conflits. Si tel est le cas, l'Agent de fusion utilise un programme de résolution de conflits pour déterminer les données qui doivent être acceptées et propagées aux autres sites.  
  
> [!NOTE]  
>  Bien qu'un Abonné se synchronise avec le serveur de publication, les conflits se produisent généralement entre les mises à jour des différents Abonnés plutôt qu'entre les mises à jour de l'Abonné et du serveur de publication.  
  
 La réplication de fusion propose plusieurs méthodes de détection et de résolution des conflits. Pour la plupart des applications, la méthode par défaut est la plus adaptée :  
  
-   Si un conflit se produit entre un serveur de publication et un Abonné, la modification du serveur de publication est conservée tandis que celle de l'Abonné est annulée.  
  
-   Si un conflit se produit entre deux Abonnés utilisant des abonnements client (le type par défaut des abonnements par extraction de données), la modification provenant du premier Abonné pour se synchroniser avec le serveur de publication est conservée tandis que celle provenant du second Abonné est annulée. Pour plus d’informations sur la spécification des abonnements client et serveur, consultez [spécifier un Type d’abonnement de fusion et de priorité pour la résolution des conflits & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md).  
  
-   Si un conflit se produit entre deux Abonnés utilisant des abonnements serveur (le type par défaut des abonnements par envoi de données), la modification provenant de l'Abonné ayant la valeur de priorité la plus élevée est conservée tandis que celle provenant du second Abonné est annulée. Si les valeurs de priorité sont identiques, la modification provenant du premier Abonné pour se synchroniser avec le serveur de publication est conservée.  
  
 Pour plus d’informations sur la détection de conflit et la résolution pour la réplication de fusion, consultez [avancées de détection de conflit réplication de fusion et résolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
## Voir aussi  
 [Options d'articles pour la réplication de fusion](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [S'abonner à des publications](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  