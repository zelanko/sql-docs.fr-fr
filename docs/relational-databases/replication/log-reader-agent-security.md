---
title: "S&#233;curit&#233; de l&#39;Agent de lecture du journal | Microsoft Docs"
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
  - "sql13.rep.security.LRA.f1"
helpviewer_keywords: 
  - "boîte de dialogue Sécurité de l'Agent de lecture du journal"
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# S&#233;curit&#233; de l&#39;Agent de lecture du journal
  Le **sécurité de l’Agent de lecture du journal** boîte de dialogue vous permet de spécifier :  
  
-   Le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent de lecture du journal s'exécute dans le serveur de distribution. Ce compte Windows est également baptisé *compte de processus*du fait que le processus agent s'exécute sous ce compte.  
  
-   Le contexte sous lequel l’Agent de lecture du journal établit des connexions à la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher. La connexion peut avoir lieu en empruntant l'identité du compte Windows ou dans le contexte d'un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous spécifiez.  
  
    > [!NOTE]  
    >  L'Agent de lecture du journal établit des connexions avec le serveur de publication même si celui-ci et le serveur de publication se trouvent sur le même ordinateur. L'Agent de lecture du journal établit également des connexions avec le serveur de distribution ; ces connexions ont toujours lieu en empruntant l'identité du compte Windows sous lequel s'exécute l'agent.  
  
     Pour les serveurs de publication Oracle, spécifiez le contexte sous lequel l’Agent de lecture du journal se connecte au serveur de publication dans le **Propriétés de l’éditeur** boîte de dialogue (disponible à partir de la **des propriétés de serveur de distribution** boîte de dialogue). Pour plus d’informations, consultez [Afficher et modifier les paramètres de sécurité réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Tous les comptes doivent être valides, le mot de passe correct étant spécifié pour chaque compte. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## Options  
 **Compte de processus**  
 Entrez le compte Windows sous lequel l'Agent de lecture du journal s'exécute dans le serveur de distribution. Le compte Windows que vous spécifiez doit être au minimum être membre de la **db_owner** rôle fixe de base de données dans la base de données de distribution.  
  
 **Mot de passe** et **Confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
 **Connexion au serveur de publication**  
 Déterminez si l’Agent de lecture du journal doit établir les connexions au serveur de publication en imitant le compte spécifié dans le **compte de processus** zone de texte ou en utilisant un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte. Si vous choisissez d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un nom de connexion et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande de choisir d’emprunter l’identité du compte Windows plutôt que d’utiliser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte.  
  
 Le compte Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte utilisé pour la connexion doit être au moins un membre de la **db_owner** rôle fixe de base de données dans la base de données de publication.  
  
## Voir aussi  
 [Gérer les connexions et les mots de passe dans la réplication](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modèle de sécurité de l'Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  