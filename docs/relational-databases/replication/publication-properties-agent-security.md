---
title: "Propri&#233;t&#233;s de la publication, page S&#233;curit&#233; de l&#39;agent | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.agentsecurity.f1"
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Propri&#233;t&#233;s de la publication, page S&#233;curit&#233; de l&#39;agent
  La page **Sécurité de l'agent** de la boîte de dialogue **Propriétés de la publication** vous permet d'accéder aux paramètres des comptes sous lesquels s'exécutent les agents ci-après. Elle vous permet également d'établir des connexions aux ordinateurs dans une topologie de réplication :  
  
-   Agent d'instantané pour toutes les publications ;  
  
-   Agent de lecture du journal pour toutes les publications transactionnelles ; Il existe un Agent de lecture du journal pour chaque base de données publiée en vue de la réplication transactionnelle. La modification des paramètres de l'Agent de lecture du journal affecte toutes les publications transactionnelles dans une base de données.  
  
-   l'Agent de lecture de la file d'attente propre aux publications transactionnelles autorisant les abonnements de mise à jour dans la file d'attente ; Il existe un Agent de lecture de la file d'attente pour chaque base de données de distribution. La modification des paramètres de l'Agent de lecture de la file d'attente affecte toutes les publications transactionnelles avec des abonnements mis à jour en attente qui utilisent la même base de données de distribution. Pour plus d’informations sur les paramètres de sécurité de l’Agent de lecture de file d’attente, consultez la page [Afficher et modifier les paramètres de sécurité réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Pour plus d'informations sur les paramètres de sécurité et les autorisations requis par chaque agent, consultez [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Options  
 **Paramètres de sécurité** ou **créer un Agent**  
 Si un travail d’agent a été créé, cliquez sur **les paramètres de sécurité** pour accéder à une boîte de dialogue qui vous permet de modifier les paramètres de sécurité pour un agent. Dans le cas contraire, cliquez sur **Créer un Agent** pour en créer un et spécifier les paramètres de sécurité.  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sécurité et Protection & #40 ; Réplication & #41 ;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  