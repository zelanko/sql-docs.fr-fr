---
title: "Types de r&#233;plication | Microsoft Docs"
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
  - "réplication [SQL Server], types"
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Types de r&#233;plication
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit les types suivants de la réplication pour une utilisation dans les applications distribuées :  
  
-   Réplication transactionnelle. Pour plus d’informations, consultez [la réplication transactionnelle](../../relational-databases/replication/transactional/transactional-replication.md).  
  
-   Réplication de fusion. Pour plus d’informations, consultez [la réplication de fusion](../../relational-databases/replication/merge/merge-replication.md).  
  
-   Réplication d'instantané. Pour plus d’informations, consultez [la réplication d’instantané](../../relational-databases/replication/snapshot-replication.md).  
  
 Le type de réplication que vous choisissez pour une application dépend de nombreux facteurs, dont l'environnement physique de la réplication, le type et la quantité de données à répliquer et si les données sont ou non mises à jour sur l'Abonné. L'environnement physique comprend le nombre et l'emplacement des ordinateurs impliqués dans la réplication et le fait que ces ordinateurs sont des clients (stations de travail, ordinateurs portables ou ordinateurs de poche) ou des serveurs.  
  
 Chaque type de réplication commence par une synchronisation initiale des objets publiés entre le serveur de publication et les Abonnés. Cette synchronisation initiale peut être effectuée par la réplication avec un *instantané*, qui est une copie de tous les objets et les données spécifiées par une publication. Quand l'instantané est créé, il est remis aux Abonnés. Pour certaines applications, la réplication d'instantané est tout ce qui est requis. Pour d'autres types d'applications, il est important que les modifications de données suivantes soient transmises à l'Abonné de façon incrémentielle au fil du temps. Certaines applications requièrent aussi que les modifications transitent en sens inverse, de l'Abonné vers le serveur de publication. La réplication transactionnelle et la réplication de fusion comportent des options pour ces types d'applications.  
  
 Les modifications des données ne font pas l'objet d'un suivi dans la réplication d'instantané : chaque fois qu'un instantané est appliqué, il remplace complètement les données existantes. La réplication transactionnelle fait le suivi des modifications via le journal des transactions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; la réplication de fusion fait le suivi des modifications via des déclencheurs et des tables de métadonnées.  
  
## Voir aussi  
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  