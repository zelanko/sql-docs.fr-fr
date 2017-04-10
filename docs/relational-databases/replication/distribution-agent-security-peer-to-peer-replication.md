---
title: "S&#233;curit&#233; de l&#39;Agent de distribution (r&#233;plication d&#39;&#233;gal &#224; &#233;gal) | Microsoft Docs"
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
  - "sql13.rep.p2pwizard.DA.f1"
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# S&#233;curit&#233; de l&#39;Agent de distribution (r&#233;plication d&#39;&#233;gal &#224; &#233;gal)
  Le **sécurité de l’Agent de Distribution** page vous permet de spécifier les comptes sous lequel l’Agent de Distribution s’exécute et établit des connexions aux ordinateurs dans une topologie d’égal à égal. Pour plus d’informations sur les autorisations requises par les agents et les meilleures pratiques pour la sécurité de la réplication, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md) et [meilleures pratiques de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Si l'Agent de distribution d'un abonnement a déjà été configuré lors d'une précédente exécution de cet Assistant, vous ne pouvez pas modifier les informations d'identification qu'il utilise dans cet Assistant. Si vous spécifiez de nouvelles informations d'identification, elles sont ignorées. Pour modifier ces informations, utilisez la boîte de dialogue **Propriétés de l'abonnement** . Pour plus d’informations, consultez [Afficher et modifier les paramètres de sécurité réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## Options  
 Cliquez sur le bouton des propriétés (**...**) dans la ligne pour chaque abonné pour accéder à la **sécurité de l’Agent de Distribution** boîte de dialogue. Cliquez sur **Aide** dans la boîte de dialogue **Sécurité de l'Agent de distribution** qui s'affiche pour obtenir plus d'informations sur les autorisations indispensables pour les comptes utilisés par les agents.  
  
 Après avoir entré les paramètres dans l'une des boîtes de dialogue, les informations de connexion de l'Abonné s'affichent dans la grille.  
  
 **Agent de l'Abonné**  
 Nom de chaque homologue.  
  
 **Base de données d'homologues**  
 Base de données de l'homologue utilisée à la fois comme base de données de publication et d'abonnement.  
  
 **Connexion au serveur de distribution**  
 Le contexte dans lequel la connexion au serveur de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent. Cet Assistant crée des abonnements (la connexion locale est la connexion au serveur de distribution), afin que ce champ affiche toujours : **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'**.  
  
 **Connexion à l'Abonné**  
 Le contexte dans lequel la connexion à l'abonné s'établit. Il est possible d'établir la connexion en utilisant le contexte du compte Windows sous lequel s'exécute l'agent ou le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ affiche l’un des éléments suivants : **utiliser la connexion ' \< connexion>'**, **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
## Voir aussi  
 [Administrer une topologie d’égal à égal & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Réplication transactionnelle d'égal à égal](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  