---
title: "Ajouter un Abonn&#233; non-SQL Server | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.addnonsqlsubscriber.f1"
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# Ajouter un Abonn&#233; non-SQL Server
  La réplication prend en charge la création d'abonnement par envoi de données (push) à des publications d'instantané et transactionnelles pour les abonnés Oracle et IBM DB2.  
  
## Options  
 **Type d'Abonné à ajouter**  
 Sélectionnez un abonné Oracle ou IBM DB2. Pour plus d’informations sur la prise en charge de ces abonnés, consultez la page [les abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Nom de la source des données**  
 Nom utilisé pour localiser la base de données sur un réseau. La réplication produit une chaîne de connexion pour la base de données à l’aide du nom de source de données associé à la connexion, mot de passe et les options de connexion que vous spécifiez dans le **sécurité de l’Agent de Distribution** page de cet Assistant.  
  
> [!NOTE]  
>  La chaîne de nom et de la connexion source de données ne sont pas validées par [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jusqu'à ce que l’Agent de Distribution tente d’initialiser l’abonnement.  
  
## Voir aussi  
 [Create a Subscription for a Non-SQL Server Subscriber](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  