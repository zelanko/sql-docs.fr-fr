---
title: "Prot&#233;ger le serveur de distribution | Microsoft Docs"
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
  - "sécurité [réplication SQL Server], serveurs de distribution"
  - "Serveurs de distribution [réplication SQL Server], sécurité"
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Prot&#233;ger le serveur de distribution
  Les Agents de réplication suivants se connectent au serveur de distribution : l'Agent de lecture du journal, l'Agent d'instantané, l'Agent de lecture de la file d'attente, l'Agent de distribution et l'Agent de fusion. Il est important de donner un nom d'accès approprié à chacun de ces agents tout en suivant le principe d'accorder le minimum de droits nécessaires et de protéger également le stockage de tous les mots de passe.  
  
-   Pour plus d’informations sur la gestion des connexions et des mots de passe, consultez [Gérer les connexions et les mots de passe lors de la réplication](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
-   Pour plus d’informations sur les autorisations requises pour chaque agent, consultez [modèle de sécurité de l’Agent de réplication](../../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Outre la gestion des connexions et des mots de passe correctement, il est important de comprendre le rôle de la **repl_distributor** lien du serveur distant et le **distributor_admin** compte.  
  
## Protection de la connexion du serveur de publication au serveur de distribution  
 Pour prendre en charge les communications nécessaires lorsque les procédures stockées administratives s’exécutent sur les serveur de publication et de mise à jour d’informations sur le serveur de distribution, la réplication configure automatiquement le serveur distant **repl_distributor**. Le **repl_distributor** entrée du serveur distant est utilisée pour la communication vers la base de données de distribution indépendamment de la base de données de distribution est contenue dans l’instance de l’éditeur (distributeur local) ou se trouve dans un référentiel distant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance (un serveur de distribution distant).  
  
 Lorsqu'une base de données de distribution est contenue dans une instance locale, un mot de passe aléatoire est généré et configuré automatiquement. Si la base de données de distribution est situé sur une instance distante, l’administrateur configure un mot de passe lors de l’installation de l’éditeur et le distributeur. Ce mot de passe est ensuite utilisé pour l’authentification du trafic qui traverse le **repl_distributor** lien.  
  
 Le serveur de distribution utilise le **repl_distributor** entrée du serveur distant pour vérifier que le serveur est configuré en tant que serveur de publication sur le serveur de distribution, valide le mot de passe fourni par le serveur de publication et vérifie que la procédure stockée est une réplication de procédure stockée lors de l’exécution.  
  
 Le mot de passe configuré pour le **repl_distributor** entrée lors de l’installation du serveur distant est associée à une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] connexion, **distributor_admin**, qui est ajouté à la **sysadmin** rôle serveur fixe sur le serveur de distribution. Le **distributor_admin** connexion est utilisée par des procédures stockées de réplication lors de la connexion au serveur de distribution.  
  
> [!NOTE]  
>  Ne modifiez pas le mot de passe pour la **distributor_admin** manuellement. Toujours utiliser le **sp_changedistributor_password** procédure stockée, ou la **des propriétés de serveur de distribution** ou **la réplication de mise à jour des mots de passe** boîtes de dialogue de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], car un mot de passe sont alors appliqués à local publications automatiquement.  
  
## Sécurité du répertoire d'instantanés  
 Assurez-vous que le partage de fichiers d'instantanés dispose d'une autorisation de lecture sur le compte sous lequel s'exécute l'Agent de fusion (pour la réplication de fusion) ou l'Agent de distribution (pour la réplication d'instantané ou transactionnelle), et d'une autorisation d'écriture sur le compte sous lequel s'exécute l'Agent d'instantané. Pour plus d’informations sur le dossier de capture instantanée, consultez [sécuriser le dossier de capture instantanée](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
## Voir aussi  
 [View and Modify Replication Security Settings](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Activer les connexions chiffrées dans le moteur de base de données & #40 ; Gestionnaire de Configuration SQL Server & #41 ;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [Méthodes préconisées en matière de sécurité de réplication](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sécurité et Protection & #40 ; Réplication & #41 ;](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  