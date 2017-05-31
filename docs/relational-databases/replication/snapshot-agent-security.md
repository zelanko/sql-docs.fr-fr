---
title: "Sécurité de l’Agent d’instantané | Microsoft Docs"
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
- sql13.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9a3834548fba6eb52e57836eefdb9f8917cb35d0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="snapshot-agent-security"></a>Sécurité de l'Agent d'instantané
  La boîte de dialogue **Sécurité de l'Agent d'instantané** permet de définir :  
  
-   Le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent d'instantané s'exécute le serveur de distribution. Ce compte Windows est également baptisé *compte de processus*du fait que le processus agent s'exécute sous ce compte.  
  
-   Le contexte sous lequel l'Agent d'instantané établit des connexions au serveur de publication [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La connexion peut avoir lieu en empruntant l'identité du compte Windows ou dans le contexte d'un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous spécifiez.  
  
    > [!NOTE]  
    >  L'Agent d'instantané établit des connexions au serveur de publication, même si le serveur de publication et le serveur de distribution se trouvent sur le même ordinateur. L'Agent d'instantané établit également des connexions au serveur de distribution ; ces connexions sont toujours établies en imitant le compte Windows sous lequel l'Agent s'exécute.  
  
     Pour les serveurs de publication Oracle, définissez le contexte sous lequel l'Agent d'instantané se connecte au serveur de publication dans la boîte **Propriétés du serveur de publication** (accessible depuis la boîte de dialogue **Propriété du serveur de distribution** ). Pour plus d’informations, consultez [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Tous les comptes doivent être valides, le mot de passe correct étant spécifié pour chaque compte. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## <a name="options"></a>Options  
 **Process account**  
 Entrez le compte Windows sous lequel l'Agent d'instantané s'exécute sur le serveur de distribution. Le compte Windows que vous définissez doit :  
  
-   être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de distribution ;  
  
-   pouvoir écrire dans le partage de fichiers de instantanés.  
  
 **Mot de passe** et **Confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
 **Connexion au serveur de publication**  
 Indiquez si l'Agent d'instantané doit établir des connexions au serveur de publication en imitant le compte défini dans la zone de texte **Compte de processus** en utilisant un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous choisissez d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , entrez un nom de connexion et un mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Il est recommandé de choisir d'emprunter l'identité du compte Windows plutôt que d'utiliser un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Le compte Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé pour la connexion doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les connexions et les mots de passe dans la réplication](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Vue d’ensemble des agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
