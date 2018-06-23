---
title: Rôles de sécurité nécessaires pour la réplication | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [SQL Server replication], roles
- roles [SQL Server], replication
ms.assetid: b324a80f-4319-4cb2-847b-1910c49d90e0
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7bddcd23b4da3fa95a3a73e63b6a1566b8f3a588
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154143"
---
# <a name="security-role-requirements-for-replication"></a>Rôles de sécurité nécessaires pour la réplication
  La réplication limite les actions spécifiques qu'un utilisateur peut réaliser, en fonction des rôles mappés à sa connexion d'accès. La réplication a attribué certaines autorisations au rôle serveur fixe **sysadmin** , au rôle de base de données fixe **db_owner** ainsi qu'aux connexions d'accès de la liste d'accès aux publications.  
  
## <a name="security-role-requirements-for-replication-setup"></a>Rôles de sécurité requis pour la configuration de la réplication  
 Le tableau suivant résume les niveaux d'authentification nécessaires aux tâches de configuration courantes de la réplication :  
  
|Tâche de configuration|Appartenance requise|  
|----------------|----------------------------|  
|Activer un serveur de distribution, un serveur de publication ou un Abonné|Rôle de serveur**sysadmin** sur le serveur de publication|  
|Activer une base de données pour la réplication.|Rôle de serveur**sysadmin** sur le serveur de publication|  
|Créer une publication|Rôle de base de données**db_owner** sur la base de données de publication du serveur de publication ou rôle de serveur **sysadmin** sur le serveur de publication|  
|Afficher les propriétés des publications|Membre de la liste d'accès aux publications sur le serveur de publication, rôle de base de données **db_owner** sur la base de données de publication du serveur de publication ou rôle de serveur **sysadmin** sur le serveur de publication|  
|Créer un abonnement|Rôle de base de données**db_owner** sur la base de données de publication du serveur de publication ou rôle de serveur **sysadmin** sur le serveur de publication<br /><br /> Rôle de base de données**db_owner** sur la base de données d'abonnement de l'Abonné ou rôle de serveur **sysadmin** sur l'Abonné|  
|Configurer les profils d'Agents|Rôle de serveur**sysadmin** sur le serveur de distribution|  
  
## <a name="security-role-requirements-for-replication-maintenance"></a>Rôles de sécurité requis pour la maintenance de la réplication  
 Le tableau suivant résume les niveaux d'authentification nécessaires aux tâches de maintenance courantes de la réplication :  
  
|Tâche de maintenance|Appartenance requise|  
|----------------------|----------------------------|  
|Modifier ou supprimer un serveur de publication, de distribution ou un Abonné|Rôle de serveur**sysadmin** sur le serveur approprié|  
|Modifier ou supprimer une publication|Rôle de base de données**db_owner** sur la base de données de publication du serveur de publication ou rôle de serveur **sysadmin** sur le serveur de publication|  
|Modifier ou supprimer un abonnement sur le serveur de publication|Rôle de base de données**db_owner** sur la base de données de publication du serveur de publication ou rôle de serveur **sysadmin** sur le serveur de publication|  
|Modifier ou supprimer un abonnement sur l'Abonné|Rôle de base de données**db_owner** sur la base de données d'abonnement de l'Abonné ou rôle de serveur **sysadmin** sur l'Abonné|  
|Marquer un abonnement en vue d'une réinitialisation|Abonnement par émission de données : rôle de base de données **db_owner** sur la base de données de publication du serveur de publication ou rôle serveur **sysadmin** sur le serveur de publication<br /><br /> Abonnement par extraction : rôle de base de données **db_owner** sur la base de données d'abonnement de l'Abonné ou rôle serveur **sysadmin** sur l'Abonné|  
|Afficher l'activité, les erreurs et l'historique de la réplication à l'aide du moniteur de réplication Un utilisateur ne peut pas modifier les profils, planifications et autres paramètres d'Agent s'il n'est pas membre du rôle de serveur **sysadmin** .|Rôle de base de données**replmonitor** sur la base de données de distribution du serveur de distribution ou rôle de serveur **sysadmin** sur le serveur de distribution|  
|Gérer les Agents de réplication|Rôle de base de données**db_owner** sur la base de données appropriée ou rôle de serveur **sysadmin** sur le serveur approprié<br /><br /> Si l'Agent a été créé par un utilisateur dans le rôle **sysadmin** et qu'aucun compte proxy n'a été spécifié pour l'Agent, ce dernier s'exécute sous le contexte du compte de l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Dans ce cas, un utilisateur bénéficiant du rôle **db_owner** ne peut pas modifier le travail associé à l'Agent.|  
|Démarrer ou arrêter un Agent de réplication|Propriétaire du travail de l'Agent ou rôle de serveur **sysadmin** sur le serveur approprié|  
  
## <a name="see-also"></a>Voir aussi  
 [Replication Security Best Practices](replication-security-best-practices.md)   
 [Sécurité et protection &#40;réplication&#41;](security-and-protection-replication.md)  
  
  