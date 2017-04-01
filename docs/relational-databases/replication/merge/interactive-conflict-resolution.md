---
title: "R&#233;solution interactive des conflits | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "résolution interactive des conflits [réplication SQL Server]"
  - "résolveur interactif [réplication SQL Server]"
  - "articles [réplication SQL Server], résolution des conflits"
  - "résolution des conflits [réplication SQL Server], réplication de fusion"
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# R&#233;solution interactive des conflits
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la réplication fournit un résolveur interactif, ce qui permet de résoudre manuellement les conflits pendant la synchronisation à la demande dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] le Gestionnaire de synchronisation Windows. Activé lors de l'exécution, le résolveur interactif est une interface graphique qui affiche des données pour chaque ligne conflictuelle et qui propose les options nécessaires à la consultation et à la modification de ces données, permettant ainsi de résoudre chaque conflit individuellement.  
  
 Le résolveur interactif ressemble à l'outil d'affichage des conflits. Cependant, l'outil d'affichage des conflits affiche les résultats des conflits déjà résolus après la synchronisation de fusion et le résolveur interactif affiche chaque conflit non résolu, ce qui vous permet de déterminer l'issue de chacun d'eux durant la synchronisation de fusion. Un opérateur doit être disponible pour analyser le résolveur interactif lorsqu'un conflit se produit.  
  
> [!NOTE]  
>  La résolution interactive nécessite le Gestionnaire de synchronisation Windows. Si une synchronisation est effectuée en dehors du Gestionnaire de synchronisation Windows (comme une synchronisation planifiée ou à la demande dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou le Moniteur de réplication), les conflits sont résolus automatiquement sans intervention de l'utilisateur, en fonction de l'outil de résolution spécifié pour l'article. Les conflits qui concernent des enregistrements logiques ne sont pas affichés dans le résolveur interactif. Pour afficher des informations sur ces conflits, utilisez des procédures stockées de réplication. Pour plus d’informations, consultez [Afficher les informations de conflit pour les Publications de fusion & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/view conflict information for merge publications.md).  
  
## Résolveurs d'articles et résolveur interactif  
 Les résolveurs de conflits (qu'il s'agisse du résolveur par défaut, d'un gestionnaire de logique métier ou d'un résolveur personnalisé) sont affectés à des articles spécifiques lors de la création d'une publication, et ils font appel à un ensemble de règles prédéterminées pour définir le dataset à utiliser lorsque des données de ligne en conflit sont entrées. Le résolveur interactif n'est pas un résolveur de conflits isolé avec des règles permettant de distinguer les vainqueurs et les perdants d'un conflit, mais un outil utilisé conjointement avec les résolveurs de fusion par défaut et personnalisés. Le résolveur d'articles détermine toujours la ligne gagnante et la ligne perdante, mais le résolveur interactif permet aux utilisateurs d'intervenir pour accepter, rejeter ou modifier les résultats.  
  
 Pour utiliser le résolveur interactif, la résolution interactive doit être activée pour chaque article et abonnement qui l'exige. Une fois qu'il est activé pour un ou plusieurs articles et abonnements, le résolveur interactif est utilisé lorsqu'un conflit est détecté durant une synchronisation de fusion.  
  
 Pour utiliser le résolveur interactif, consultez [spécifier de résolution de conflit Interactive pour les Articles de fusion](../../../relational-databases/replication/publish/specify-interactive-conflict-resolution-for-merge-articles.md) et [synchroniser Gestionnaire de synchronisation Windows utilisant un abonnement & #40 ; Le Gestionnaire de synchronisation Windows & #41 ;](../../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md).  
  
## Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  