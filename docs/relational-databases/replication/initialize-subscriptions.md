---
title: "Initialiser les abonnements | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.initializesubscriptions.f1"
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# Initialiser les abonnements
  Les abonnés doivent être initialisés pour pouvoir recevoir des données répliquées. Un jeu de données initial n'est pas nécessaire, mais l'abonné doit avoir au minimum le schéma de chaque objet répliqué ainsi que les tables de métadonnées et les procédures nécessaires à la réplication.  
  
## Options  
 **Propriétés de l'abonnement**  
 Activez la case à cocher dans la **initialiser** colonne pour chaque abonné qui requiert un jeu de données initial. Si vous désactivez la case à cocher, seules les métadonnées et les procédures de réplication sont initialisées. Pour plus d’informations sur l’initialisation d’un abonnement sans instantané, consultez [initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 Sélectionnez **immédiatement** dans la zone de liste déroulante dans le **initialiser lorsque** colonne pour que l’Agent de fusion ou l’Agent de Distribution transfère fichiers d’instantanés à l’abonné une fois cet Assistant est terminé. Sélectionnez **Lors de la première synchronisation** pour que l'Agent transfère les fichiers lors de la prochaine exécution planifiée de l'Agent. L'option **Immédiatement** n'est pas disponible pour les abonnements par extraction à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. L'Agent de fusion et l'Agent de distribution ne fonctionnent pas sur les instances de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]; l'abonnement doit donc être initialisé via une autre méthode.  
  
> [!NOTE]  
>  Il se peut que l'Assistant demande une connexion au serveur de distribution pour pouvoir démarrer le travail approprié pour l'Agent de distribution ou l'Agent de fusion.  
  
## Voir aussi  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Initialiser un abonnement](../../relational-databases/replication/initialize-a-subscription.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  