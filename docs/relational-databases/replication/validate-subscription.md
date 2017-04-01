---
title: "Valider l&#39;abonnement | Microsoft Docs"
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
  - "sql13.rep.validate.validateandresynch.f1"
helpviewer_keywords: 
  - "boîte de dialogue Valider l'abonnement"
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Valider l&#39;abonnement
  Utilisez le **valider l’abonnement** boîte de dialogue pour spécifier qu’un abonnement à une publication de fusion doit être validé lors de la prochaine exécution de l’Agent de fusion pour l’abonnement. Le résultat de la validation figure dans le Moniteur de réplication. Pour plus d'informations, voir [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 Il est également possible de valider tous les abonnements à une publication de fusion en double-cliquant sur une publication dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et en cliquant sur **Valider tous les abonnements**.  
  
## Options  
 **Date de la dernière tentative de validation**  
 Date de la dernière session de l'Agent de fusion qui incluait la validation d'abonnement, que la validation ait abouti ou non.  
  
 **Date de la dernière validation réussie**  
 Date de la dernière session de l'Agent de fusion qui incluait une validation d'abonnement réussie.  
  
 **Valider cet abonnement**  
 Sélectionnez cette option pour valider l'abonnement.  
  
 **Options**  
 Cliquez pour accéder à la **Options de Validation d’abonnement** boîte de dialogue qui vous permet de spécifier s’il faut utiliser la validation du nombre de lignes ou de validation de somme de contrôle binaire.  
  
## Voir aussi  
 [Valider des données répliquées](../../relational-databases/replication/validate-replicated-data.md)  
  
  