---
title: "Identit&#233; et contr&#244;le d&#39;acc&#232;s (r&#233;plication) | Microsoft Docs"
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
  - "contrôles d'accès [réplication SQL Server]"
  - "sécurité [réplication SQL Server], identité et contrôle d’accès"
  - "authentification [réplication SQL Server]"
  - "identité [réplication]"
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# Identit&#233; et contr&#244;le d&#39;acc&#232;s (r&#233;plication)
  L’authentification est le processus par lequel une entité (généralement un ordinateur dans ce contexte) vérifie une autre entité, également appelée un *principal*, (généralement un autre ordinateur ou utilisateur) est celui ou ce qu’il prétend être. L'autorisation est le processus selon lequel une entité principale authentifiée bénéficie de l'accès aux ressources, telles qu'un fichier du système de fichiers ou une table d'une base de données.  
  
 La sécurité de réplication fait appel à l'authentification et à l'autorisation pour contrôler l'accès aux objets de base de données répliqués, aux ordinateurs et aux agents impliqués dans le traitement de la réplication. Trois mécanismes régissent son fonctionnement :  
  
-   Sécurité de l'agent  
  
     Le modèle de sécurité de l'agent de réplication permet un contrôle fin sur les comptes sous lesquels les agents de réplication s'exécutent et établissent des connexions. Pour plus d’informations sur le modèle de sécurité de l’agent, consultez [modèle de sécurité de l’Agent de réplication](../../../relational-databases/replication/security/replication-agent-security-model.md). Pour plus d’informations sur la définition des connexions et des mots de passe pour les agents, consultez [Gérer les connexions et les mots de passe lors de la réplication](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
-   Rôles d'administration  
  
     Vérifiez que les rôles de base de données et de serveur appropriés sont utilisés pour la configuration, la maintenance et le traitement de la réplication. Pour plus d’informations, consultez [rôles de sécurité requis pour la réplication](../../../relational-databases/replication/security/security-role-requirements-for-replication.md).  
  
-   Liste d'accès à la publication  
  
     Octroyez l'accès aux publications par l'intermédiaire de cette liste. La liste d'accès à la publication fonctionne de manière similaire à une liste de contrôle d'accès [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Lorsqu'un Abonné se connecte au serveur de publication ou au serveur de distribution et souhaite accéder à une publication, les informations d'authentification passées par l'agent sont comparées à celles de la liste d'accès à la publication. Pour plus d’informations et des meilleures pratiques pour la publication, consultez [sécuriser le serveur de publication](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
## Filtrage des données publiées  
 Outre l'utilisation de l'authentification et de l'autorisation pour contrôler l'accès aux données et aux objets répliqués, la réplication comprend deux options permettant de contrôler les données disponibles sur un Abonné : filtrage des colonnes et filtrage des lignes. Pour plus d’informations sur le filtrage, consultez [filtrer les données publiées](../../../relational-databases/replication/publish/filter-published-data.md).  
  
 Lorsque vous définissez un article, vous pouvez publier uniquement les colonnes nécessaires pour la publication et omettre celles dont vous n'avez pas besoin ou qui comportent des données sensibles. Par exemple, lorsque vous publiez le **client** table à partir de la base de données Adventure Works pour les représentants commerciaux dans le champ, vous pouvez omettre le **AnnualSales** colonne, ce qui peut être uniquement aux cadres de l’entreprise.  
  
 Le filtrage des données publiées vous permet de restreindre l'accès aux données et de spécifier les données qui sont disponibles sur l'Abonné. Par exemple, vous pouvez filtrer le **client** afin que les partenaires de l’entreprise recevoir uniquement des informations sur les clients de la table dont **ShareInfo** colonne a la valeur « Oui ». Pour les réplications de fusion, vous devez tenir compte de certains points de sécurité si vous utilisez un filtre paramétré qui inclut HOST_NAME(). Pour plus d’informations, consultez la section « Filtrage avec HOST_NAME() » dans [filtres de lignes paramétrable](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
## Voir aussi  
 [Sécurité et Protection & #40 ; Réplication & #41 ;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Vue d’ensemble de la sécurité & #40 ; Réplication & #41 ;](../../../relational-databases/replication/security/security-overview-replication.md)   
 [Menaces et les risques de vulnérabilité & #40 ; Réplication & #41 ;](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
  
  