---
title: Sécurité de l’Agent de lecture du journal | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c55292aff126d1955c438c9417ce0651cc6afc94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63162238"
---
# <a name="log-reader-agent-security"></a>Sécurité de l'Agent de lecture du journal
  La boîte de dialogue **sécurité de l’agent de lecture du journal** vous permet de spécifier les éléments suivants :  
  
-   Le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent de lecture du journal s'exécute dans le serveur de distribution. Le compte Windows est également appelé *compte de processus*, car le processus de l’agent s’exécute sous ce compte.  
  
-   Contexte dans lequel l’agent de lecture du journal établit des connexions [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au serveur de publication. La connexion peut avoir lieu en empruntant l'identité du compte Windows ou dans le contexte d'un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous spécifiez.  
  
    > [!NOTE]  
    >  L'Agent de lecture du journal établit des connexions avec le serveur de publication même si celui-ci et le serveur de publication se trouvent sur le même ordinateur. L'Agent de lecture du journal établit également des connexions avec le serveur de distribution ; ces connexions ont toujours lieu en empruntant l'identité du compte Windows sous lequel s'exécute l'agent.  
  
     Pour les serveurs de publication Oracle, spécifiez le contexte dans lequel l'Agent de lecture du journal se connecte au serveur de publication dans la boîte de dialogue **Propriétés du serveur de publication** (disponible à partir de la boîte de dialogue **Propriétés du serveur de distribution** ). Pour plus d’informations, consultez [afficher et modifier les paramètres de sécurité de la réplication](security/view-and-modify-replication-security-settings.md).  
  
 Tous les comptes doivent être valides, le mot de passe correct étant spécifié pour chaque compte. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## <a name="options"></a>Options  
 **Compte de processus**  
 Entrez le compte Windows sous lequel l'Agent de lecture du journal s'exécute dans le serveur de distribution. Le compte Windows que vous spécifiez doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de distribution.  
  
 **Mot de passe** et **confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
 **Se connecter au serveur de publication**  
 Sélectionnez si l'Agent de lecture du journal doit établir les connexions au serveur de publication en empruntant l'identité du compte spécifié dans la zone de texte **Compte de processus** ou en utilisant un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous choisissez d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un nom de connexion et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande de choisir d'emprunter l'identité du compte Windows plutôt que d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Le compte Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour la connexion doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les comptes de connexion et les mots de passe dans la réplication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Modèle de sécurité de l’agent de réplication](security/replication-agent-security-model.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)   
 [Bonnes pratiques en matière de sécurité de la réplication](security/replication-security-best-practices.md)  
  
  
