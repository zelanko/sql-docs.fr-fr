---
title: "Propriétés de SQL Server Agent (page Connexion) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e7b4cc647a5654a098ab8d3a318dbcfc313a1c8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sql-server-agent-properties-connection-page"></a>Propriétés de l'Agent SQL Server (page Connexion)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Utilisez cette page pour afficher et modifier les paramètres de la connexion du service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>Options  
**Alias du serveur hôte local**  
Spécifie l'alias à utiliser pour se connecter à l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Si vous ne pouvez pas utiliser les options de connexion par défaut pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , définissez un alias pour l'instance et spécifiez l'alias à cet endroit.  
  
**Utiliser l'authentification Windows**  
Définit l'authentification [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows comme la méthode d'authentification utilisée pour se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se connecte sous le compte utilisé par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
**Utiliser l’authentification SQL Server**  
Définit l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] comme la méthode d'authentification utilisée pour se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] est fournie dans un souci de compatibilité descendante. Pour une sécurité renforcée, utilisez l'authentification Windows dans la mesure du possible.  
  
**Connexion**  
Permet de spécifier le nom d’accès à utiliser pour la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Mot de passe**  
Permet de spécifier le mot de passe à utiliser pour la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
