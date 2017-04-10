---
title: "Didacticiel&#160;: R&#233;plication de donn&#233;es entre serveurs connect&#233;s en permanence | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "didacticiels [réplication SQL Server]"
  - "réplication [SQL Server], didacticiels"
  - "assistants [réplication SQL Server]"
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Didacticiel&#160;: R&#233;plication de donn&#233;es entre serveurs connect&#233;s en permanence
La réplication constitue une bonne solution au problème de transfert de données entre serveurs connectés en permanence. À l'aide des Assistants de réplication, vous pouvez aisément configurer et administrer une topologie de réplication. Ce didacticiel vous explique comment configurer une topologie de réplication dans le cas de serveurs connectés en permanence.  
  
## Contenu du didacticiel  
Ce didacticiel vous explique comment publier des données d'une base de données sur une autre à l'aide de la réplication transactionnelle. La première leçon montre comment utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer une publication. Les leçons suivantes expliquent comment créer et valider un abonnement et comment mesurer la latence.  
  
## Spécifications  
Ce didacticiel est destiné aux utilisateurs qui sont familiers des opérations élémentaires de base de données, mais dont l'expérience en matière de réplication est limitée. Pour suivre ce didacticiel, vous devez avoir terminé le didacticiel précédent, [Préparation du serveur pour la réplication](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Pour utiliser ce didacticiel, les composants suivants doivent être installés sur votre système :  
  
-   Sur le serveur de publication (source)  
  
    -   Toute édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sauf Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) ou [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Ces éditions ne peuvent pas constituer des serveurs de publication de réplication.  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)]  : exemple de base de données. Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.  
  
-   Serveur de l'Abonné (destination) :  
  
    -   Toute édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sauf [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] ne peut pas être un abonné dans une réplication transactionnelle.  
  
    > [!NOTE]  
    > La réplication n'est pas installée par défaut dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
> [!NOTE]  
> Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez vous connecter au serveur de publication et à l’Abonné à l’aide d’un identifiant de connexion membre du rôle serveur fixe **sysadmin**.  
  
**Durée estimée pour effectuer ce didacticiel : 30 minutes.**  
  
## Leçons du didacticiel  
  
-   [Leçon 1 : publication de données à l'aide de la réplication transactionnelle](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [Leçon 2 : Création d'un abonnement à la publication transactionnelle](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [Leçon 3 : Validation de l'abonnement et mesure de la latence](../../relational-databases/replication/lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
[Démarrer le didacticiel](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)  
  
## Voir aussi  
[Concepts de programmation en matière de réplication](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  
  
  
