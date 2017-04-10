---
title: "S&#233;curit&#233; de l&#39;agent &lt;AgentName&gt; | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.agentnameagentsecurity.f1"
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# S&#233;curit&#233; de l&#39;agent &lt;AgentName&gt;
  Le **\< Nom_agent> sécurité de l’Agent** page vous permet de spécifier les comptes sous lequel l’Agent de Distribution (pour la réplication transactionnelle et de capture instantanée) ou l’Agent de fusion (pour la réplication de fusion) s’exécutent et établissent des connexions aux ordinateurs dans une topologie de réplication. Pour plus d’informations sur les autorisations requises par les agents et les meilleures pratiques pour la sécurité de la réplication, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md) et [meilleures pratiques de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## Options  
 Cliquez sur le bouton des propriétés (**...**) dans la ligne pour chaque abonné pour accéder à la **sécurité de l’Agent de Distribution** ou **sécurité de l’Agent de fusion** boîte de dialogue. Cliquez sur **Aide** dans la boîte de dialogue qui s'affiche pour fournir plus d'informations sur les autorisations indispensables pour les comptes utilisés par les agents.  
  
 Après avoir entré les paramètres dans l'une des boîtes de dialogue, les informations de connexion de l'Abonné s'affichent dans la grille.  
  
 **Agent de l'Abonné**  
 Nom de chaque Abonné.  
  
 **Connexion au serveur de distribution**  
 S'affiche pour les réplications d'instantané et transactionnelle. Le contexte dans lequel la connexion au serveur de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements envoyés, la connexion locale est la connexion au serveur de distribution, ce champ affiche toujours : **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'** pour les abonnements envoyés.  
  
-   Pour les abonnements par extraction, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ affiche l’un des éléments suivants : **utiliser la connexion ' \< connexion>'**, **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
 **Connexion au serveur de publication et serveur de distribution**  
 S'affiche pour la réplication de fusion. Le contexte des connexions aux serveurs de publication et de distribution s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements envoyés, la connexion locale est la connexion à l’éditeur et le distributeur, ce champ affiche toujours : **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'** pour les abonnements envoyés.  
  
-   Pour les abonnements par extraction, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ affiche l’un des éléments suivants : **utiliser la connexion ' \< connexion>'**, **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
 **Connexion à l'Abonné**  
 Le contexte dans lequel la connexion à l'abonné s'établit. Les connexions locales sont toujours établies en utilisant le contexte du compte Windows dans lequel s'exécute l'agent :  
  
-   Pour les abonnements par extraction de données, la connexion locale est la connexion à l’abonné, ce champ affiche toujours : **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'** pour les abonnements envoyés.  
  
-   Pour les abonnements par émission de données, la connexion peut également avoir lieu dans le contexte d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le champ affiche l’un des éléments suivants : **utiliser la connexion ' \< connexion>'**, **emprunter l’identité ' \< domaine>\\< connexion\>'** ou **emprunter l’identité ' \< ordinateur>\\< connexion\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'établir toutes les connexions dans le contexte du compte Windows.  
  
## Voir aussi  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Gérer les connexions et les mots de passe dans la réplication](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modèle de sécurité de l'Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Sécurité et Protection & #40 ; Réplication & #41 ;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  