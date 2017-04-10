---
title: "S&#233;curit&#233; de l&#39;Agent de lecture du journal (r&#233;plication d&#39;&#233;gal &#224; &#233;gal) | Microsoft Docs"
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
  - "sql13.rep.p2pwizard.LRA.f1"
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# S&#233;curit&#233; de l&#39;Agent de lecture du journal (r&#233;plication d&#39;&#233;gal &#224; &#233;gal)
  La page **Sécurité de l'Agent de lecture du journal** permet de définir les comptes sous lesquels l'Agent de lecture du journal sur chaque homologue s'exécute et établit des connexions. Pour plus d’informations sur les autorisations requises par les agents et les meilleures pratiques pour la sécurité de la réplication, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md) et [meilleures pratiques de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  Il existe un Agent de lecture du journal pour chaque base de données publiée utilisant la réplication transactionnelle. Si l'Agent de lecture du journal d'une base de données est déjà configuré (pour la publication dans une exécution précédente de cet Assistant ou une autre publication transactionnelle dans la même base de données), vous ne pouvez pas modifier les informations d'identification qu'il utilise dans l'Assistant. Si vous spécifiez de nouvelles informations d'identification, elles sont ignorées. Pour changer les informations d'identification, utilisez la boîte de dialogue **Propriétés de la publication** . Pour plus d’informations, consultez [Afficher et modifier les paramètres de sécurité réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## Options  
 Cliquez sur le bouton des propriétés (**...**) dans la ligne pour chaque homologue pour accéder à la **sécurité de l’Agent de lecture du journal** boîte de dialogue. Cliquez sur **Aide** dans la boîte de dialogue **Sécurité de l'Agent de lecture du journal** qui s'ouvre pour plus d'informations sur les autorisations nécessaires aux comptes utilisés par les agents.  
  
 Après avoir défini les paramètres de la boîte de dialogue, les informations de connexion de l'Abonné s'affichent dans la grille.  
  
 **Agents du serveur de publication**  
 Nom de chaque instance de serveur homologue.  
  
 **Base de données d'homologues**  
 Base de données qui fait office de base de données de publication et de base de données d'abonnement sur chaque homologue.  
  
 **Connexion au serveur de distribution**  
 Le contexte dans lequel la connexion au serveur de distribution s'établit. La connexion au serveur de distribution locale est toujours établie à l’aide du contexte de le [!INCLUDE[msCoName](../../includes/msconame-md.md)] compte Windows sous lequel l’agent s’exécute, ce champ affiche toujours **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'**.  
  
 **Connexion au serveur de publication**  
 Contexte sous lequel la connexion au serveur de publication est établie. La connexion au serveur de publication peut être établie en utilisant une connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou le contexte du compte Windows sous lequel l'Agent s'exécute. Le champ affiche l’un des éléments suivants : **utiliser la connexion ' \< connexion>'**, **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
## Voir aussi  
 [Administrer une topologie d’égal à égal & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Réplication transactionnelle d'égal à égal](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  