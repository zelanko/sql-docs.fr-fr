---
title: "S&#233;curit&#233; de l&#39;Agent d&#39;instantan&#233; | Microsoft Docs"
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
  - "sql13.rep.security.SSA.f1"
helpviewer_keywords: 
  - "boîte de dialogue Sécurité de l'Agent d'instantané"
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# S&#233;curit&#233; de l&#39;Agent d&#39;instantan&#233;
  Le **sécurité de l’Agent de capture instantanée** boîte de dialogue vous permet de spécifier :  
  
-   Le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent d'instantané s'exécute le serveur de distribution. Ce compte Windows est également baptisé *compte de processus*du fait que le processus agent s'exécute sous ce compte.  
  
-   Le contexte sous lequel l’Agent d’instantané établit des connexions à la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher. La connexion peut avoir lieu en empruntant l'identité du compte Windows ou dans le contexte d'un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous spécifiez.  
  
    > [!NOTE]  
    >  L'Agent d'instantané établit des connexions au serveur de publication, même si le serveur de publication et le serveur de distribution se trouvent sur le même ordinateur. L'Agent d'instantané établit également des connexions au serveur de distribution ; ces connexions sont toujours établies en imitant le compte Windows sous lequel l'Agent s'exécute.  
  
     Pour les serveurs de publication Oracle, spécifiez le contexte sous lequel l’Agent de capture instantanée se connecte au serveur de publication dans le **Propriétés de l’éditeur** boîte de dialogue (disponible à partir de la **des propriétés de serveur de distribution** boîte de dialogue). Pour plus d’informations, consultez [Afficher et modifier les paramètres de sécurité réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Tous les comptes doivent être valides, le mot de passe correct étant spécifié pour chaque compte. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## Options  
 **Compte de processus**  
 Entrez le compte Windows sous lequel l'Agent d'instantané s'exécute sur le serveur de distribution. Le compte Windows que vous définissez doit :  
  
-   Au moins être membre du **db_owner** rôle fixe de base de données dans la base de données de distribution.  
  
-   pouvoir écrire dans le partage de fichiers de instantanés.  
  
 **Mot de passe** et **Confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
 **Connexion au serveur de publication**  
 Déterminez si l’Agent d’instantané doit établir les connexions au serveur de publication en imitant le compte spécifié dans le **compte de processus** zone de texte ou en utilisant un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte. Si vous choisissez d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un nom de connexion et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Il est recommandé de choisir d'emprunter l'identité du compte Windows plutôt que d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le compte Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte utilisé pour la connexion doit être au moins un membre de la **db_owner** rôle fixe de base de données dans la base de données de publication.  
  
## Voir aussi  
 [Gérer les connexions et les mots de passe dans la réplication](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modèle de sécurité de l'Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  