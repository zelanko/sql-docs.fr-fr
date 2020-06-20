---
title: Audit de sécurité, catégorie d’événements (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Security Audit event category [SQL Server]
- event classes [SQL Server], Security Audit event category
- SQL Server event classes, Security Audit event category
ms.assetid: e64f7695-2f23-4adb-b83d-52f147cc1a2f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81b07c1eb33176533cedbf0d02a71a264419b11e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85052557"
---
# <a name="security-audit-event-category-sql-server-profiler"></a>Audit de sécurité, catégorie d'événements (SQL Server Profiler)
  La catégorie d’événements d’ **audit de sécurité** contient, comme son nom l’indique, les événements liés à l’activité d’audit de la sécurité.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Audit Add DB User, classe d’événements](audit-add-db-user-event-class.md)|Indique qu'une connexion en tant qu'utilisateur de la base de données a été ajoutée à la base de données ou supprimée de celle-ci.|  
|[Classe d'événements Audit Add Login to Server Role](audit-add-login-to-server-role-event-class.md)|Indique qu'une connexion a été ajoutée à un rôle serveur fixe ou en a été supprimée.|  
|[Classe d'événements Audit Add Member to DB Role](audit-add-member-to-db-role-event-class.md)|Indique qu'une connexion a été ajoutée à un rôle ou en a été supprimée.|  
|[Classe d'événements Audit Add Role](audit-add-role-event-class.md)|Indique qu'un rôle de base de données a été ajouté à une base de données ou en a été supprimé.|  
|[Classe d'événements Audit Addlogin](audit-addlogin-event-class.md)|Indique qu'une connexion a été ajoutée ou supprimée.|  
|[Classe d'événements Audit App Role Change Password](audit-app-role-change-password-event-class.md)|Indique qu'un mot de passe a été modifié pour un rôle d'application.|  
|[Classe d’événements Audit Backup/Restore](audit-backup-and-restore-event-class.md)|Indique qu'une instruction de sauvegarde ou de restauration a été émise.|  
|[Classe d'événement Audit Broker Conversation](broker-conversation-event-class.md)|Crée un rapport de messages d'audit associés à la sécurité de boîte de dialogue Service Broker.|  
|[Classe d'événements Audit Broker Login](audit-broker-login-event-class.md)|Crée un rapport de messages d'audit associés à la sécurité de transport Service Broker.|  
|[Classe d'événements Audit Change Audit](audit-change-audit-event-class.md)|Indique qu'une modification de trace d'audit a été effectuée.|  
|[Classe d'événements Audit Change Database Owner](audit-change-database-owner-event-class.md)|Indique que les autorisations de modification du propriétaire d'une base de données ont été vérifiées.|  
|[Audit Database Management, classe d’événements](audit-database-management-event-class.md)|Indique qu'une base de données a été créée, modifiée ou supprimée.|  
|[Audit Database Mirroring Login, classe d’événements](audit-database-mirroring-login-event-class.md)|Crée un rapport de messages d'audit associés à la sécurité de transport de la mise en miroir de bases de données.|  
|[Audit Database Object Access, classe d’événements](audit-database-object-access-event-class.md)|Indique qu'un objet de base de données tel qu'un schéma, a été utilisé.|  
|[Classe d'événements Audit Database Object GDR](audit-database-object-gdr-event-class.md)|Indique qu'un événement GDR pour un objet de base de données s'est produit.|  
|[Classe d'événements Audit Database Object Management](audit-database-object-management-event-class.md)|Indique qu'une instruction CREATE, ALTER ou DROP a été exécutée sur un objet de base de données.|  
|[Classe d'événements Audit Database Object Take Ownership](audit-database-object-take-ownership-event-class.md)|Indique qu'une modification de propriétaire d'objets a eu lieu dans l'étendue de la base de données.|  
|[Classe d'événements Audit Database Operation](audit-database-operation-event-class.md)|Indique que plusieurs opérations telles qu'un point de contrôle ou une notification de requête d'abonnement se sont produites.|  
|[Classe d'événements Audit Database Principal Impersonation](audit-database-principal-impersonation-event-class.md)|Indique qu'un emprunt d'identité s'est produit dans l'étendue de la base de données.|  
|[Classe d'événements Audit Database Principal Management](audit-database-principal-management-event-class.md)|Indique que des principaux ont été créés, modifiés ou supprimés d'une base de données.|  
|[Classe d'événements Audit Database Scope GDR](audit-database-scope-gdr-event-class.md)|Indique qu’une instruction GRANT, REVOKE ou DENY a été émise pour une autorisation d’instruction par un utilisateur dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Audit DBCC, classe d’événements](audit-dbcc-event-class.md)|Indique qu'une commande DBCC a été émise.|  
|[Audit Fulltext, classe d’événements](audit-fulltext-event-class.md)|Indique qu'un événement de texte intégral s'est produit.|  
|[Audit Login Change Password, classe d’événements](audit-login-change-password-event-class.md)|Indique qu'un utilisateur a modifié son mot de passe d'ouverture de session [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[Classe d'événements Audit Login Change Property](audit-login-change-property-event-class.md)|Indique que la procédure **sp_defaultdb**, **sp_defaultlanguage**ou ALTER LOGIN a été utilisée pour modifier une propriété d’une connexion.|  
|[Classe d'événements Audit Login](audit-login-event-class.md)|Indique qu'un utilisateur s'est connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Classe d'événements Audit Login Failed](audit-login-failed-event-class.md)|Indique qu'un utilisateur a tenté de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et a échoué.|  
|[Classe d'événements Audit Login GDR](audit-login-gdr-event-class.md)|Indique qu'un droit de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows a été ajouté ou supprimé.|  
|[Classe d'événements Audit Logout](audit-logout-event-class.md)|Indique qu'un utilisateur s'est déconnecté de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Classe d'événements Audit Object Derived Permission](audit-object-derived-permission-event-class.md)|Indique qu'un événement CREATE, ALTER ou DROP a été émis pour un objet.|  
|[Classe d'événements Audit Schema Object Access](audit-schema-object-access-event-class.md)|Indique qu'une autorisation relative aux objets (telle que SELECT) a été utilisée.|  
|[Classe d'événements Audit Schema Object GDR](audit-schema-object-gdr-event-class.md)|Indique qu'un événement GRANT, REVOKE ou DENY a été émis pour une autorisation relative aux objets de schéma par un utilisateur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Classe d'événements Audit Schema Object Management](audit-schema-object-management-event-class.md)|Indique qu'un objet de serveur a été créé, modifié ou supprimé.|  
|[Classe d'événements Audit Schema Object Take Ownership](audit-schema-object-take-ownership-event-class.md)|Indique que les autorisations relatives à la modification du propriétaire de l'objet de schéma ont été vérifiées.|  
|[Classe d'événements Audit Server Alter Trace](audit-server-alter-trace-event-class.md)|Indique que l'autorisation ALTER TRACE a été vérifiée.|  
|[Classe d'événements Audit Server Object GDR](audit-server-object-gdr-event-class.md)|Indique qu'un événement GDR pour un objet de schéma s'est produit.|  
|[Classe d'événements Audit Server Object Management](audit-server-object-management-event-class.md)|Indique qu'un événement CREATE, ALTER ou DROP s'est produit pour un objet de serveur.|  
|[Classe d'événements Audit Server Object Take Ownership](audit-server-object-take-ownership-event-class.md)|Indique que le propriétaire d'un objet de serveur a été modifié.|  
|[Classe d'événements Audit Server Operation](audit-server-operation-event-class.md)|Indique que des opérations d'audit se sont produites sur le serveur.|  
|[Classe d'événements Audit Server Principal Impersonation](audit-server-principal-impersonation-event-class.md)|Indique qu'un emprunt d'identité s'est produit dans l'étendue du serveur.|  
|[Classe d'événements Audit Server Principal Management](audit-server-principal-management-event-class.md)|Indique qu'un événement CREATE, ALTER ou DROP s'est produit pour un principal de serveur.|  
|[Classe d'événements Audit Server Scope GDR](audit-server-scope-gdr-event-class.md)|Indique qu'un événement GDR s'est produit pour les autorisations de serveur.|  
|[Classe d'événements Audit Server Starts and Stops](audit-server-starts-and-stops-event-class.md)|Indique que l'état du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été modifié.|  
|[Audit Statement Permission, classe d’événements](audit-statement-permission-event-class.md)|Indique qu'une autorisation relative aux instructions a été utilisée.|  
  
## <a name="related-content"></a>Contenu associé  
 [Événements étendus](../extended-events/extended-events.md)  
  
  
