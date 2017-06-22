---
title: "Sécurité de l’Agent de lecture du journal | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 67f7bfd9eb599250b951f4365d3d6efe6e943a31
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="log-reader-agent-security"></a>Sécurité de l'Agent de lecture du journal
  La boîte de dialogue **Sécurité de l'Agent de lecture du journal** permet de spécifier :  
  
-   Le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent de lecture du journal s'exécute dans le serveur de distribution. Ce compte Windows est également baptisé *compte de processus*du fait que le processus agent s'exécute sous ce compte.  
  
-   Le contexte dans lequel l'Agent de lecture du journal établit les connexions avec le serveur de publication [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La connexion peut avoir lieu en empruntant l'identité du compte Windows ou dans le contexte d'un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous spécifiez.  
  
    > [!NOTE]  
    >  L'Agent de lecture du journal établit des connexions avec le serveur de publication même si celui-ci et le serveur de publication se trouvent sur le même ordinateur. L'Agent de lecture du journal établit également des connexions avec le serveur de distribution ; ces connexions ont toujours lieu en empruntant l'identité du compte Windows sous lequel s'exécute l'agent.  
  
     Pour les serveurs de publication Oracle, spécifiez le contexte dans lequel l'Agent de lecture du journal se connecte au serveur de publication dans la boîte de dialogue **Propriétés du serveur de publication** (disponible à partir de la boîte de dialogue **Propriétés du serveur de distribution** ). Pour plus d’informations, consultez [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Tous les comptes doivent être valides, le mot de passe correct étant spécifié pour chaque compte. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## <a name="options"></a>Options  
 **Process account**  
 Entrez le compte Windows sous lequel l'Agent de lecture du journal s'exécute dans le serveur de distribution. Le compte Windows que vous spécifiez doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de distribution.  
  
 **Mot de passe** et **Confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
 **Connexion au serveur de publication**  
 Sélectionnez si l'Agent de lecture du journal doit établir les connexions au serveur de publication en empruntant l'identité du compte spécifié dans la zone de texte **Compte de processus** ou en utilisant un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous choisissez d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un nom de connexion et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande de choisir d'emprunter l'identité du compte Windows plutôt que d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Le compte Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour la connexion doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les connexions et les mots de passe dans la réplication](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Vue d’ensemble des agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Bonnes pratiques en matière de sécurité de la réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
