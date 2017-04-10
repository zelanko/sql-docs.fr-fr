---
title: "Synchronisez les donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "synchronisation [réplication SQL Server], à propos de la synchronisation"
  - "synchronisation de la réplication de fusion [réplication SQL Server]"
  - "scripts [réplication SQL Server], synchronisation et"
  - "synchronisation [réplication SQL Server]"
  - "réplication de capture instantanée [SQL Server], synchronisation"
  - "réplication transactionnelle, synchronisation"
  - "abonnements [réplication SQL Server], synchronisation"
  - "exécution de script à la demande"
  - "réplication [SQL Server], synchronisation"
  - "scripts [réplication SQL Server]"
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Synchronisez les donn&#233;es
  La synchronisation des données est le processus de propagation des modifications de données et de schéma entre le serveur de publication et les abonnés après l'application de l'instantané initial sur les abonnés. La synchronisation peut se produire :  
  
-   En continu, ce qui est le mode normal pour la réplication transactionnelle.  
  
-   À la demande, ce qui est le mode normal pour la réplication de fusion.  
  
-   Suivant une planification, ce qui est le mode normal pour la réplication d'instantané.  
  
 Lorsqu'un abonnement est synchronisé, différents processus se produisent en fonction de votre type de réplication :  
  
-   Réplication d'instantané. La synchronisation signifie que l'Agent de distribution applique de nouveau l'instantané sur l'Abonné pour que le schéma et les données de la base de données d'abonnement soient cohérents avec ceux de la base de données de publication.  
  
     Si des modifications de données ou de schéma ont été effectuées sur le serveur de publication, un nouvel  instantané doit être généré afin de propager les modifications sur l'Abonné.  
  
-   Réplication transactionnelle. La synchronisation signifie que l'Agent de distribution transfère les mises à jour, les insertions, les suppressions et toute autre modification de la base de données de distribution sur l'Abonné.  
  
-   Réplication de fusion. La synchronisation signifie que l'Agent de distribution charge les modifications de l'Abonné sur le serveur de publication, puis télécharge les modifications du serveur de publication sur l'Abonné. S'il existe des conflits, ils sont détectés et résolus. Dès que la convergence des données est assurée, le serveur de publication et tous les abonnés disposent des mêmes valeurs de données. Si des conflits ont été détectés et corrigés, le travail validé par certains utilisateurs est modifié pour résoudre le conflit en fonction de vos stratégies définies.  
  
 Chaque fois que la synchronisation se produit, les publications d'instantanés actualisent complètement le schéma de l'Abonné, les modifications de schéma sont donc toutes appliquées sur l'Abonné. La réplication transactionnelle et la réplication de fusion prennent également en charge les modifications de schéma les plus courantes. Pour plus d’informations, consultez [apporter des modifications de schéma sur les bases de données de Publication](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
 Pour synchroniser un abonnement envoyé, consultez [synchroniser un abonnement envoyé](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
 Pour synchroniser un abonnement par extraction de données, consultez [synchroniser un abonnement par extraction de données](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
 Pour définir des planifications de synchronisation, consultez [spécifier des planifications de synchronisation](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
 **Pour afficher et résoudre les conflits de synchronisation**  
  
-   [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
## Exécution de code pendant la synchronisation  
 La réplication prend en charge deux méthodes d'exécution de code pendant la synchronisation :  
  
-   L'exécution de script à la demande est prise en charge pour la réplication transactionnelle et la réplication de fusion. Vous pouvez, lors de l'utilisation de script à la demande, spécifier un script SQL à exécuter pendant la synchronisation. Le script est copié vers l’abonné et exécutée à l’aide **sqlcmd** au début du processus de synchronisation. Le script n'a pas accès aux modifications répliquées car elles sont appliquées à l'Abonné. Pour plus d’informations, consultez [exécuter les Scripts pendant la synchronisation & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md).  
  
-   Les gestionnaires de logique métier sont pris en charge par la réplication de fusion. Vous pouvez, à l'aide de l'infrastructure du gestionnaire de logique métier, écrire un assembly de code managé qui est appelé pendant le processus de synchronisation de fusion. L'assembly comprend une logique métier qui peut répondre à un certain nombre de conditions au cours de la synchronisation : les modifications de données, les conflits et les erreurs. Pour plus d’informations, consultez [exécution logique au cours de fusion synchronisation professionnels](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
## Voir aussi  
 [Détecter et résoudre de conflits de réplication de fusion](../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md)  
  
  