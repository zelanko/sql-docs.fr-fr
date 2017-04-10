---
title: "Abonnements pouvant &#234;tre mis &#224; jour | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.updatablesubscriptions.f1"
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Abonnements pouvant &#234;tre mis &#224; jour
  Avec la réplication transactionnelle, les données répliquées doivent être traitées en lecture seule ; Toutefois, vous pouvez modifier les données répliquées sur un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonné à l’aide à abonnements. Si vous devez modifier des données sur l'Abonné, vous pouvez choisir l'une des options suivantes selon vos besoins.  
  
|Type d'abonnement pouvant être mis à jour|Spécifications|  
|---------------------------------|------------------|  
|Mise à jour immédiate|Le serveur de publication et l'Abonné doivent être connectés pour mettre à jour les données sur l'Abonné.|  
|Mise à jour en attente|Le serveur de publication et l'Abonné n'ont pas besoin d'être connectés pour mettre à jour les données sur l'Abonné. Les mises à jour peuvent être effectuées hors ligne et synchronisées ensuite entre le serveur de publication et l'Abonné.|  
  
## Options  
 **Répliquer les modifications de l'Abonné**  
 Activez la case à cocher dans la **répliquer** colonne pour chaque abonné qui doit être en mesure d’effectuer des mises à jour. Pour les abonnés qui peuvent rendre les mises à jour, sélectionnez l’option appropriée dans la zone de liste déroulante dans le **valider sur le serveur de publication** colonne :  
  
-   Sélectionnez **Enregistrer les modifications simultanément** pour un abonnement mis à jour immédiatement.  
  
-   Sélectionnez **Mettre les modifications en file d'attente et valider dès que possible** pour un abonnement mis à jour en file d'attente.  
  
## Voir aussi  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  