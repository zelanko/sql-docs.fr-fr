---
title: "Propri&#233;t&#233;s de l&#39;abonnement - Serveur de publication | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.subproperties.publisher.f1"
helpviewer_keywords: 
  - "boîte de dialogue Propriétés de l'abonnement"
ms.assetid: d4b2bc8b-0431-4331-8305-8992c96d0d34
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Propri&#233;t&#233;s de l&#39;abonnement - Serveur de publication
  Le **Propriétés d’un abonnement** boîte de dialogue de l’éditeur vous permet d’afficher et définir des propriétés pour les abonnements envoyés. Vous pouvez également afficher des propriétés pour les abonnements extraits, mais le **les propriétés des abonnements** boîte de dialogue sur l’abonné affiche des propriétés supplémentaires et permet des propriétés à modifier.  
  
 Chaque propriété de la **Propriétés d’un abonnement** boîte de dialogue comporte une description. Cliquez sur une propriété pour afficher sa description au bas de la boîte de dialogue. Cette rubrique fournit des informations supplémentaires sur diverses propriétés, dont la plupart sont affichées dans le serveur de publication uniquement pour les abonnements par envoi de données. Les propriétés sont regroupées selon les catégories suivantes :  
  
-   Propriétés appliquées à tous les abonnements.  
  
-   Propriétés appliquées aux abonnements transactionnels.  
  
-   Propriétés appliquées aux abonnements de fusion.  
  
 Si une option est affichée en lecture seule, vous pouvez la configurer uniquement lorsque l'abonnement est créé. Si vous voulez configurer des options non disponibles dans l'Assistant Nouvel abonnement, créez l'abonnement avec des procédures stockées. Pour plus d'informations, consultez [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) et [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
## Options pour tous les abonnements  
 **Sécurité**  
 Cliquez sur le **compte de processus de l’Agent** de ligne, puis cliquez sur le bouton des propriétés (**...**) pour modifier le compte sous lequel l’Agent de Distribution ou l’Agent de fusion s’exécute sur le serveur de distribution. Pour modifier le compte sous lequel l’Agent de Distribution ou l’Agent de fusion établit des connexions à l’abonné, cliquez sur **connexion de l’abonné**, puis cliquez sur le bouton des propriétés (**...**).  
  
 Pour plus d’informations sur les autorisations requises pour chaque agent, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Options des abonnements transactionnels  
 **Empêcher le bouclage de la transaction**  
 Détermine si l'Agent de distribution retourne à l'Abonné les transactions créées sur ce dernier. Cette option est utilisée pour la réplication transactionnelle bidirectionnelle. Pour plus d’informations, consultez [la réplication transactionnelle bidirectionnelle](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).  
  
 **Abonnement pouvant être mis à jour**  
 Détermine si les modifications de l'Abonné sont répliquées dans le serveur de publication. Vous pouvez répliquer les modifications en utilisant la mise à jour immédiate ou en file d'attente. L’option **méthode de mise à jour d’abonnés** détermine la méthode à utiliser. Pour plus d’informations, consultez la page [à des abonnements pour la réplication transactionnelle](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
## Options des abonnements de fusion  
 **Définition de la partition (HOST_NAME)**  
 Pour une publication qui utilise des filtres paramétrés, la réplication de fusion évalue une des deux fonctions système (ou les deux si le filtre fait référence aux deux) pendant la synchronisation pour déterminer les données qu’un abonné doit recevoir : **SUSER_SNAME()** ou **HOST_NAME()**. Par défaut, **HOST_NAME()** retourne le nom de l’ordinateur sur lequel l’Agent de fusion est en cours d’exécution, mais vous pouvez remplacer cette valeur dans l’Assistant Nouvel abonnement. Pour plus d’informations sur les filtres paramétrés et en remplaçant **HOST_NAME()**, consultez la page [les filtres de lignes paramétrable](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Type d’abonnement** et **priorité**  
 Indique si l'abonnement est un abonnement de client ou de serveur (cette option n'est pas modifiable après la création de l'abonnement). Les abonnements de serveur peuvent republier les données vers d'autres abonnés. Il est possible de leur affecter une priorité pour la résolution des conflits.  
  
 Si vous avez sélectionné un abonnement de type serveur dans l'Assistant Nouvel abonnement, l'abonné a la priorité utilisée lors de la résolution des conflits.  
  
 **Résoudre les conflits interactivement**  
 Détermine s'il faut utiliser l'interface utilisateur du Résolveur interactif pour résoudre les conflits pendant la synchronisation de fusion. Cela requiert une valeur de **Activer** pour **utiliser le Gestionnaire de synchronisation Windows**. Pour plus d’informations, consultez [Interactive Conflict Resolution](../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
## Voir aussi  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  