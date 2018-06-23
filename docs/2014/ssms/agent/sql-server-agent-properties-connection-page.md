---
title: Propriétés de SQL Server Agent (page Connexion) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 48f107d115960c879a8f2818b62215c6a1c316b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050964"
---
# <a name="sql-server-agent-properties-connection-page"></a>Propriétés de SQL Server Agent (page Connexion)
  Utilisez cette page pour afficher et modifier les paramètres de la connexion du service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Options  
 **Alias du serveur hôte local**  
 Spécifie l'alias à utiliser pour se connecter à l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous ne pouvez pas utiliser les options de connexion par défaut pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , définissez un alias pour l'instance et spécifiez l'alias à cet endroit.  
  
 **Utiliser l'authentification Windows**  
 Définit l'authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows comme la méthode d'authentification utilisée pour se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte sous le compte utilisé par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Utiliser l’authentification SQL Server**  
 Définit l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comme la méthode d'authentification utilisée pour se connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est fournie dans un souci de compatibilité descendante. Pour une sécurité renforcée, utilisez l'authentification Windows dans la mesure du possible.  
  
 **Connexion**  
 Permet de spécifier le nom d’accès à utiliser pour la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Mot de passe**  
 Permet de spécifier le mot de passe à utiliser pour la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  