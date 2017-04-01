---
title: "S&#233;curit&#233; de l&#39;Agent de lecture de la file d&#39;attente | Microsoft Docs"
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
  - "sql13.rep.security.QRA.f1"
helpviewer_keywords: 
  - "boîte de dialogue Sécurité de l'Agent de lecture de la file d'attente"
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# S&#233;curit&#233; de l&#39;Agent de lecture de la file d&#39;attente
  Le **sécurité de l’Agent de lecture de file d’attente** boîte de dialogue vous permet de spécifier le [!INCLUDE[msCoName](../../includes/msconame-md.md)] compte Windows sous lequel l’Agent de lecture de file d’attente s’exécute et établit des connexions locales au serveur de distribution. L’agent se connecte au serveur de publication à l’aide du compte spécifié dans le **Propriétés de l’éditeur** boîte de dialogue (disponible à partir de la **des propriétés de serveur de distribution** boîte de dialogue) ; l’agent se connecte à l’abonné en utilisant le même contexte que l’Agent de Distribution pour l’abonnement. Pour plus d’informations, consultez [Afficher et modifier les paramètres de sécurité réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Le compte doit être valide avec le mot de passe correct défini. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## Options  
 **Compte de processus**  
 Tapez un compte Windows sous lequel l'Agent de lecture de la file d'attente s'exécute sur le serveur de distribution. Le compte Windows que vous spécifiez doit être au minimum être membre de la **db_owner** rôle fixe de base de données dans la base de données de distribution.  
  
 **Mot de passe** et **Confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
## Voir aussi  
 [Gérer les connexions et les mots de passe dans la réplication](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modèle de sécurité de l'Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  