---
title: Agent XPs (option de configuration de serveur) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 13f707d8d745cfcaf5a1dc63ecca96297cb04696
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="agent-xps-server-configuration-option"></a>Agent XPs (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **Agent XPs** pour activer les procédures stockées étendues de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sur ce serveur. Si cette option n'est pas activée, le nœud de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas disponible dans l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 Quand vous utilisez l’outil [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour démarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, ces procédures stockées étendues sont activées automatiquement. Pour plus d'informations, consultez [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] L’Explorateur d’objets n’affiche pas le contenu du nœud [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent, sauf si ces procédures stockées étendues sont activées, quel que soit l’état du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 Les valeurs possibles sont les suivantes :  
  
-   **0**, qui indique que les procédures stockées étendues de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent ne sont pas disponibles (valeur par défaut).  
  
-   **1**, qui indique que les procédures stockées étendues de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sont disponibles.  
  
 Le paramètre prend effet immédiatement, sans arrêt et redémarrage du serveur.  
  
## <a name="example"></a> Exemple
 L'exemple suivant active les procédures stockées étendues de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

1. Depuis Microsoft SQL Server Management Studio, connectez-vous au moteur de base de données.

2.  Dans la barre d’outils standard, cliquez sur **Nouvelle requête**.

3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. 
  
```sql 
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Tâches d’administration automatisée &#40;SQL Server Agent&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)   
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
  
