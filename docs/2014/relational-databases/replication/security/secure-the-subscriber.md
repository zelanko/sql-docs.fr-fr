---
title: Sécuriser l’abonné | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], security
- Subscribers [SQL Server replication], security
- security [SQL Server replication], Subscribers
ms.assetid: c8f0d62a-8b5d-4a21-9aec-223da52bb708
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7c8f75360bb3eb4b304c2a56a150218e8f8c8eff
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125424"
---
# <a name="secure-the-subscriber"></a>Sécuriser l'abonné
  Les Agents de fusion et les Agents de distribution se connectent à l'Abonné. Ces connexions peuvent être effectuées dans le contexte d'un nom de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou d'un nom de connexion Windows. Il est important de fournir un nom de connexion approprié à ces agents tout en respectant le principe consistant à attribuer les droits nécessaires minimaux et à protéger aussi le stockage de tous les mots de passe. Pour des informations sur les autorisations requises pour chaque agent, consultez [Replication Agent Security Model](replication-agent-security-model.md).  
  
## <a name="distribution-agent"></a>Agent de distribution  
 Il y a soit un Agent de distribution par abonnement (un agent indépendant, qui est l'agent par défaut pour les publications créées dans l'Assistant Nouvelle publication), soit un Agent de distribution par paire base de données de publication/base de données d'abonnement (un agent partagé). T  
  
 Pour spécifier des informations de connexion pour les abonnements par émission de données, consultez [Créer un abonnement par émission de données](../create-a-push-subscription.md).  
  
 Pour spécifier les informations de connexion pour les abonnements par extraction, consultez [Créer un abonnement par extraction](../create-a-pull-subscription.md).  
  
## <a name="merge-agent"></a>Agent de fusion  
 Chaque abonnement de fusion a son propre Agent de fusion qui se connecte à la fois à l'éditeur et à l'abonné et les met à jour.  
  
 Pour spécifier des informations de connexion pour les abonnements par émission de données, consultez [Créer un abonnement par émission de données](../create-a-push-subscription.md).  
  
 Pour spécifier les informations de connexion pour les abonnements par extraction, consultez [Créer un abonnement par extraction](../create-a-pull-subscription.md).  
  
## <a name="immediate-updating-subscriptions"></a>Abonnement mis à jour immédiatement  
 Quand vous configurez un abonnement mis à jour immédiatement, vous spécifiez un compte sur l'Abonné, sous lequel sont effectuées les connexions au serveur de publication. Les connexions sont utilisées par les déclencheurs qui s'exécutent pour l'abonné et propagent les modifications sur le serveur de publication. Trois options sont possibles pour le type de connexion :  
  
-   Un serveur lié qui est créé par la réplication ; la connexion est faite avec les informations d'identification que vous spécifiez au moment de la configuration.  
  
-   Un serveur lié créé par la réplication. La connexion se fait à l'aide des informations d'identification de l'utilisateur qui apporte la modification pour l'abonné.  
  
-   Un serveur lié ou distant que vous avez déjà défini.  
  
> [!IMPORTANT]  
>  Pour spécifier des informations de connexion, utilisez la procédure stockée [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql). Vous pouvez également utiliser la page **Nom d'accès aux abonnements pouvant être mis à jour** de l'Assistant Nouvel abonnement qui appelle **sp_link_publication**. Dans certaines conditions, cette procédure stockée peut échouer si l'Abonné exécute [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) ou une version ultérieure, et que le serveur de publication exécute une version antérieure. Si la procédure stockée échoue dans ce scénario, mettez à niveau le serveur de publication vers [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] SP1 ou une version ultérieure.  
  
 Pour plus d’informations, consultez [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](../publish/create-an-updatable-subscription-to-a-transactional-publication.md) et [Afficher et modifier les paramètres de sécurité de la réplication](view-and-modify-replication-security-settings.md).  
  
> [!IMPORTANT]  
>  Le compte spécifié pour la connexion doit uniquement avoir l'autorisation d'insérer, de mettre à jour et de supprimer des données sur les vues créées par la réplication dans la base de données de publication. Il ne doit pas bénéficier d'autres autorisations. Octroyez des autorisations sur les vues de la base de données de publication qui sont mentionnées dans le panneau **syncobj_**_\<Nombre_hexadécimal>_ pour le compte que vous avez configuré pour chaque abonné.  
  
## <a name="queued-updating-subscriptions"></a>Abonnements mis à jour en attente  
 Quand vous configurez des abonnements mis à jour en attente, il faut garder à l'esprit deux points relatifs à la sécurité :  
  
-   Il n'y a qu'un seul Agent de lecture de la file d'attente pour chaque serveur de distribution. Il est recommandé de configurer, pour chaque serveur de distribution, au moins une publication qui est activée pour les abonnements mis à jour en attente.  
  
-   L'Agent de lecture de la file d'attente établit des connexions avec le serveur de distribution, avec le serveur de publication et avec chaque Abonné :  
  
    -   Le compte sous lequel l'agent s'exécute et établit des connexions avec le serveur de distribution est spécifié quand vous créez l'agent (si vous utilisez l'Assistant Nouvelle publication, l'agent est créé quand vous créez une nouvelle publication qui est activée pour les abonnements mis à jour).  
  
    -   Le compte sous lequel l'agent établit des connexions avec le serveur de publication est spécifié quand vous configurez la distribution pour un serveur de publication. Spécifiez le compte Windows sous lequel l'agent s'exécute ou un compte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
    -   Le compte sous lequel l'agent établit des connexions avec l'Abonné est spécifié quand vous créez l'abonnement.  
  
    > [!IMPORTANT]  
    >  Utilisez l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour les connexions avec les Abonnés, et spécifiez un autre compte pour la connexion avec chaque Abonné. Si vous utilisez un abonnement par extraction de données (pull), la réplication définit toujours la connexion de façon à ce qu'elle utilise l'authentification Windows (pour les abonnements par extraction de données, la réplication ne peut pas accéder aux métadonnées sur l'Abonné qui doit utiliser l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ). Dans ce cas, modifiez la connexion pour qu'elle utilise l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] après la configuration de l'abonnement.  
  
     Pour plus d’informations, consultez Comment : Créer un abonnement avec mise à jour pour une Publication transactionnelle (SQL Server Management Studio) et [afficher et modifier les paramètres de sécurité de réplication](view-and-modify-replication-security-settings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Activer les connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)   
 [Replication Security Best Practices](replication-security-best-practices.md)   
 [Sécurité de la réplication SQL Server](view-and-modify-replication-security-settings.md)  
  
  
