---
title: Sécurité de l’agent de fusion | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.MA.f1
helpviewer_keywords:
- Merge Agent Security dialog box
ms.assetid: 9b86171a-4381-4b39-869a-cdc161e7cd15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: af3d3490957114d6ba7731b49435dc7e90122f90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62932495"
---
# <a name="merge-agent-security"></a>Sécurité de l'agent de fusion
  La boîte de dialogue **Sécurité de l'agent de fusion** vous permet de spécifier le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent de fusion doit s'exécuter. L'Agent de fusion s'exécute sur le serveur de distribution pour les abonnements envoyés et sur l'Abonné pour les abonnements extraits. Le compte Windows est également appelé *compte de processus*, car le processus de l’agent s’exécute sous ce compte. La boîte de dialogue propose des options supplémentaires en fonction de la façon d'y accéder :  
  
-   Si la boîte de dialogue est ouverte à partir de l'Assistant Nouvel abonnement, elle vous propose ainsi en plus d'indiquer le contexte dans lequel l'agent de fusion établit les connexions avec l'Abonné (dans le cas d'abonnements envoyés au serveur) ou avec le serveur de publication et le serveur de distribution (dans le cas d'abonnements extraits du serveur). La connexion peut être établie à l’aide du compte Windows ou dans le contexte [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’un compte que vous spécifiez.  
  
-   Si la boîte de dialogue est ouverte à partir de celle intitulée **Propriétés de l'abonnement** , vous devez indiquer le contexte dans lequel l'agent de fusion établit les connexions en cliquant sur le bouton des propriétés (**...**) de la ligne **Connexion de l'Abonné** ou **Connexion du serveur de publication** . Pour plus d’informations sur l’accès à la boîte de dialogue **Propriétés de l’abonnement**, consultez [Afficher et modifier les propriétés d’un abonnement par émission de données](view-and-modify-push-subscription-properties.md) et la procédure indiquant comment [Afficher et modifier les propriétés d’un abonnement par extraction](view-and-modify-pull-subscription-properties.md).  
  
 Tous les comptes doivent être valides, le mot de passe correct étant spécifié pour chaque compte. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## <a name="options"></a>Options  
 **Compte de processus**  
 Permet de saisir un compte sous lequel l'agent de fusion peut s'exécuter.  
  
-   Pour les abonnements par envoi de données, le compte doit :  
  
    -   Au minimum être membre du rôle de base de données fixe **db_owner** dans la base de données de distribution.  
  
    -   être membre de la liste d'accès à la publication (PAL) ;  
  
    -   un compte de session associé à un utilisateur enregistré dans la base de données de publication ;  
  
    -   avoir les autorisations de lecture sur le partage des fichiers d'instantanés.  
  
-   Pour les abonnements par extraction, le compte doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données d'abonnement.  
  
 Des autorisations supplémentaires sont indispensables si l'identité du compte de processus est empruntée lorsque les connexions sont établies. Voir les sections **Connexion au serveur de publication et au serveur de distribution** et **Connexion à l'Abonné** ci-dessous.  
  
 Le **compte de processus** ne peut pas être spécifié [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]pour des abonnements par extraction, car l’agent de fusion [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]ne s’exécute pas sur des instances de.  
  
 **Mot de passe** et **confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
 **Se connecter au serveur de publication et au serveur de distribution**  
 Dans le cas d'abonnements envoyés, les connexions au serveur de publication et au serveur de distribution s'établissent toujours en empruntant l'identité du compte indiqué dans la zone de texte **Compte de processus** .  
  
 Dans le cas d'abonnements extraits, indiquez si vous voulez que l'agent de fusion établisse les connexions au serveur de publication et au serveur de distribution en empruntant l'identité du compte précisé dans la zone de texte **Compte de processus** ou en utilisant un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous choisissez d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un nom de connexion et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande de choisir d'emprunter l'identité du compte Windows plutôt que d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Le compte Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour la connexion doit :  
  
-   être membre de la liste d'accès à la publication (PAL) ;  
  
-   un compte de session associé à un utilisateur enregistré dans la base de données de publication ;  
  
-   un compte de session associé à un utilisateur enregistré dans la base de données de distribution (bien que l'utilisateur puisse aussi ouvrir sa session en tant qu'Invité) ;  
  
-   avoir les autorisations de lecture sur le partage des fichiers d'instantanés.  
  
 **Connexion à l’abonné**  
 Pour les abonnements par extraction, les connexions à l'Abonné ont toujours lieu en empruntant l'identité du compte spécifié dans la zone de texte **Compte de processus** .  
  
 Dans le cas d'abonnements envoyés, indiquez si vous voulez que l'agent de fusion établisse les connexions au serveur de publication et au serveur de distribution en empruntant l'identité du compte précisé dans la zone de texte **Compte de processus** ou en utilisant un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous choisissez d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un nom de connexion et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Il est recommandé de choisir d'emprunter l'identité du compte Windows plutôt que d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Le compte Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour la connexion avec l'abonné doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données d'abonnement.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les comptes de connexion et les mots de passe dans la réplication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Modèle de sécurité de l’agent de réplication](security/replication-agent-security-model.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [S'abonner à des publications](subscribe-to-publications.md)  
  
  
