---
title: "Cat&#233;gorie d&#39;&#233;v&#233;nement Verrous | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verrous (catégorie d'événement) [SQL Server]"
  - "SQL Server (classes d’événements), catégorie d’événement Locks"
  - "classes d’événements [SQL Server], catégorie d’événement Locks"
  - "escalade de verrous [SQL Server], catégorie d’événement Locks"
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# Cat&#233;gorie d&#39;&#233;v&#233;nement Verrous
  Utilisez les classes d’événements de la catégorie d’événements **Locks** pour surveiller l’activité de verrouillage dans une instance du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Ces classes d'événements facilitent la recherche de problèmes de verrouillage dus au fait que plusieurs utilisateurs lisent et modifient simultanément des données.  
  
 Du fait que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] traite souvent de nombreux verrous, la capture des classes d’événements **Locks** peut générer une surcharge importante sur le processeur et créer des tables ou des fichiers de trace volumineux.  
  
## Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événements Deadlock Graph](../../relational-databases/event-classes/deadlock-graph-event-class.md)|Fournit une description XML d'un blocage.|  
|[Classe d'événements Lock:Acquired](../../relational-databases/event-classes/lock-acquired-event-class.md)|Indique qu'un verrou a été acquis sur une ressource, par exemple une ligne d'une table.|  
|[Classe d'événements Lock:Cancel](../../relational-databases/event-classes/lock-cancel-event-class.md)|Trace les requêtes de verrous qui ont été annulées avant l'acquisition du verrou (par exemple pour empêcher un blocage).|  
|[Classe d'événements Lock:Deadlock Chain](../../relational-databases/event-classes/lock-deadlock-chain-event-class.md)|Contrôle les conditions de blocage et les objets impliqués.|  
|[Classe d'événements Lock:Deadlock](../../relational-databases/event-classes/lock-deadlock-event-class.md)|Trace à quel moment une transaction a demandé un verrou sur une ressource déjà verrouillée par une autre transaction, ce qui provoque un blocage.|  
|[Classe d'événements Lock:Escalation](../../relational-databases/event-classes/lock-escalation-event-class.md)|Indique qu'un verrouillage spécifique s'est transformé en verrouillage de plus grande ampleur.|  
|[Classe d'événements Lock:Released](../../relational-databases/event-classes/lock-released-event-class.md)|Trace la libération d'un verrou.|  
|[Classe d’événements Lock:Timeout &#40;timeout &#62; 0&#41;](../../relational-databases/event-classes/lock-timeout-timeout-0-event-class.md)|Trace à quel moment les demandes de verrous ne sont pas possibles car une autre transaction possède un verrou de blocage sur la ressource demandée. Cet événement se produit uniquement lorsque la valeur d'expiration du verrou est supérieure à zéro (0).|  
|[Classe d'événements Lock:Timeout](../../relational-databases/event-classes/lock-timeout-event-class.md)|Trace à quel moment les demandes de verrous ne sont pas possibles car une autre transaction possède un verrou de blocage sur la ressource demandée.|  
  
  