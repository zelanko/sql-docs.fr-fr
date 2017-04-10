---
title: "Propri&#233;t&#233;s de la base de donn&#233;es de distribution | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.distdbproperties.f1"
helpviewer_keywords: 
  - "boîte de dialogue Propriétés de la base de données de distribution"
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Propri&#233;t&#233;s de la base de donn&#233;es de distribution
  Le **Propriétés de base de données de Distribution** boîte de dialogue permet d’afficher un nombre de propriétés et de définir la période de rétention des transactions et la période de rétention de l’historique de la base de données.  
  
## Options  
 **Nom   **  
 Nom de la base de données de distribution, dont la valeur par défaut est « distribution » (en lecture seule).  
  
 **Emplacements des fichiers**  
 Emplacement du fichier de base de données et du fichier journal (en lecture seule).  
  
 **Période de rétention des transactions**  
 Également appelée période de rétention de distribution. Durée de stockage des transactions pour une réplication transactionnelle. Pour plus d'informations, voir [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Période de rétention de l'historique**  
 Durée de stockage des métadonnées de l'historique pour tous les types de réplications.  
  
 **Sécurité de l'Agent de lecture de la file d'attente**  
 L'Agent de lecture de la file d'attente est utilisé par la réplication transactionnelle avec les abonnements mis à jour en file d'attente. Un Agent de lecture de file d’attente est créé automatiquement si vous sélectionnez **publication transactionnelle avec abonnements mis à jour** sur la **Type de Publication** page de l’Assistant Nouvelle Publication. Cliquez sur **les paramètres de sécurité...** Pour modifier le compte sous lequel l’agent s’exécute et établit des connexions au serveur de distribution.  
  
 Un Agent de lecture de file d’attente peut également être créé en sélectionnant **créer un Agent de lecture de file d’attente** sur cette page (cette option est désactivée si l’agent a déjà été créé).  
  
 Des informations de connexion supplémentaires pour l'Agent de lecture de la file d'attente sont spécifiées dans deux endroits :  
  
-   L’agent se connecte au serveur de publication à l’aide des informations d’identification spécifiées dans le **Propriétés de l’éditeur** boîte de dialogue, qui est disponible à partir de la **éditeurs** page de la **des propriétés de serveur de distribution** boîte de dialogue.  
  
-   L'Agent se connecte à l'Abonné à l'aide des informations d'identification spécifiées pour l'Agent de distribution dans l'Assistant Nouvel abonnement.  
  
 Pour plus d’informations, consultez  \\[modèle de sécurité de l’Agent de réplication](../Topic/Replication%20Agent%20Security%20Model.md).  
  
## Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  