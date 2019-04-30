---
title: Sécurité de l’Agent de lecture de la file d’attente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 657116e00b6905964f8cc65c28dff383c3cc9ad0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63261693"
---
# <a name="queue-reader-agent-security"></a>Sécurité de l'Agent de lecture de la file d'attente
  La boîte de dialogue **Sécurité de l'Agent de lecture de la file d'attente** permet de définir le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent de lecture de la file d'attente s'exécute et établit des connexions locales avec le serveur de distribution. L'Agent se connecte au serveur de publication en utilisant le compte défini dans la boîte de dialogue **Propriétés du serveur de publication** (accessible depuis la boîte de dialogue **Propriétés du serveur de distribution** ) ; l'Agent se connecte à l'Abonné en utilisant le même contexte que l'Agent de distribution pour l'abonnement. Pour plus d’informations, consultez [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Le compte doit être valide avec le mot de passe correct défini. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## <a name="options"></a>Options  
 **Compte de processus**  
 Tapez un compte Windows sous lequel l'Agent de lecture de la file d'attente s'exécute sur le serveur de distribution. Le compte Windows que vous spécifiez doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de distribution.  
  
 **Mot de passe** et **Confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les comptes de connexion et les mots de passe dans la réplication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Modèle de sécurité de l’Agent de réplication](security/replication-agent-security-model.md)   
 [Vue d’ensemble des agents de réplication](agents/replication-agents-overview.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)  
  
  
