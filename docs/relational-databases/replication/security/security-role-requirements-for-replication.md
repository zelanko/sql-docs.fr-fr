---
title: "R&#244;les de s&#233;curit&#233; requis pour la r&#233;plication | Microsoft Docs"
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
  - "sécurité [réplication SQL Server], rôles"
  - "rôles [réplication SQL Server], réplication"
ms.assetid: b324a80f-4319-4cb2-847b-1910c49d90e0
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# R&#244;les de s&#233;curit&#233; requis pour la r&#233;plication
  La réplication limite les actions spécifiques qu'un utilisateur peut réaliser, en fonction des rôles mappés à sa connexion d'accès. La réplication a attribué certaines autorisations pour le **sysadmin** rôle serveur fixe le **db_owner** fixe du rôle de base de données et les connexions dans la liste d’accès (aux publications PAL).  
  
## Rôles de sécurité requis pour la configuration de la réplication  
 Le tableau suivant résume les niveaux d'authentification nécessaires aux tâches de configuration courantes de la réplication :  
  
|Tâche de configuration|Appartenance requise|  
|----------------|----------------------------|  
|Activer un serveur de distribution, un serveur de publication ou un Abonné|**sysadmin** rôle de serveur sur le serveur de publication.|  
|Activer une base de données pour la réplication.|**sysadmin** rôle de serveur sur le serveur de publication.|  
|Créer une publication|**db_owner** rôle de base de données sur la base de données de publication sur le serveur de publication ou **sysadmin** rôle de serveur sur le serveur de publication.|  
|Afficher les propriétés des publications|Membre de la publication sur le serveur de publication **db_owner** rôle de base de données sur la base de données de publication sur le serveur de publication, ou **sysadmin** rôle de serveur sur le serveur de publication.|  
|Créer un abonnement|**db_owner** rôle de base de données sur la base de données de publication sur le serveur de publication ou **sysadmin** rôle de serveur sur le serveur de publication.<br /><br /> **db_owner** rôle de base de données sur la base de données d’abonnement sur l’abonné ou **sysadmin** rôle serveur sur l’abonné.|  
|Configurer les profils d'Agents|**sysadmin** rôle de serveur sur le serveur de distribution.|  
  
## Rôles de sécurité requis pour la maintenance de la réplication  
 Le tableau suivant résume les niveaux d'authentification nécessaires aux tâches de maintenance courantes de la réplication :  
  
|Tâche de maintenance|Appartenance requise|  
|----------------------|----------------------------|  
|Modifier ou supprimer un serveur de publication, de distribution ou un Abonné|**sysadmin** rôle de serveur sur le serveur approprié.|  
|Modifier ou supprimer une publication|**db_owner** rôle de base de données sur la base de données de publication sur le serveur de publication ou **sysadmin** rôle de serveur sur le serveur de publication.|  
|Modifier ou supprimer un abonnement sur le serveur de publication|**db_owner** rôle de base de données sur la base de données de publication sur le serveur de publication ou **sysadmin** rôle de serveur sur le serveur de publication.|  
|Modifier ou supprimer un abonnement sur l'Abonné|**db_owner** rôle de base de données sur la base de données d’abonnement sur l’abonné ou **sysadmin** rôle serveur sur l’abonné.|  
|Marquer un abonnement en vue d'une réinitialisation|Envoyer un abonnement : **db_owner** rôle de base de données dans la base de données de publication sur le serveur de publication ou **sysadmin** rôle de serveur sur le serveur de publication.<br /><br /> Abonnement par extraction : **db_owner** rôle de base de données dans la base de données d’abonnement sur l’abonné ou **sysadmin** rôle serveur sur l’abonné.|  
|Afficher l'activité, les erreurs et l'historique de la réplication à l'aide du moniteur de réplication Un utilisateur ne peut modifier les profils d’agent, planifications et ainsi de suite, à moins que l’utilisateur est un membre de la **sysadmin** rôle de serveur.|**replmonitor** rôle de base de données sur la base de données de distribution sur le distributeur ou **sysadmin** rôle de serveur sur le serveur de distribution.|  
|Gérer les Agents de réplication|**db_owner** rôle de base de données dans la base de données appropriée ou **sysadmin** rôle de serveur sur le serveur approprié.<br /><br /> Si l’agent a été créé par un utilisateur dans le **sysadmin** rôle et un compte proxy n'a pas été spécifié pour l’agent, l’agent s’exécute sous le contexte de le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] compte de l’Agent. Dans ce cas, un utilisateur dans le **db_owner** rôle ne peut pas modifier le travail associé à l’agent.|  
|Démarrer ou arrêter un Agent de réplication|Propriétaire de la tâche de l’agent ou **sysadmin** rôle de serveur sur le serveur approprié.|  
  
## Voir aussi  
 [Méthodes préconisées en matière de sécurité de réplication](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sécurité et Protection & #40 ; Réplication & #41 ;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  