---
title: Sécurité de l’Agent de lecture de la file d’attente | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 92b80f727ce87606b0c1c58954b0743734880422
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68021260"
---
# <a name="queue-reader-agent-security"></a>Sécurité de l'Agent de lecture de la file d'attente
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La boîte de dialogue **Sécurité de l'Agent de lecture de la file d'attente** permet de définir le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent de lecture de la file d'attente s'exécute et établit des connexions locales avec le serveur de distribution. L'Agent se connecte au serveur de publication en utilisant le compte défini dans la boîte de dialogue **Propriétés du serveur de publication** (accessible depuis la boîte de dialogue **Propriétés du serveur de distribution** ) ; l'Agent se connecte à l'Abonné en utilisant le même contexte que l'Agent de distribution pour l'abonnement. Pour plus d’informations, consultez [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Le compte doit être valide avec le mot de passe correct défini. Les comptes et les mots de passe ne sont pas validés tant qu'un agent ne s'exécute pas.  
  
## <a name="options"></a>Options  
 **Compte de processus**  
 Tapez un compte Windows sous lequel l'Agent de lecture de la file d'attente s'exécute sur le serveur de distribution. Le compte Windows que vous spécifiez doit être au moins un membre du rôle de base de données fixe **db_owner** dans la base de données de distribution.  
  
 **Mot de passe** et **Confirmer le mot de passe**  
 Entrez le mot de passe du compte Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Identité et contrôle d’accès pour la réplication](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [Modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Bonnes pratiques en matière de sécurité de la réplication](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
