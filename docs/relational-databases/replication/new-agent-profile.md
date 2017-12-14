---
title: "Nouveau profil de l’Agent | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.profiles.newperfprofile.f1
helpviewer_keywords: New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e7f73501091ce352164db71ebf4ebf8758d0c40e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="new-agent-profile"></a>Nouveau profil de l'Agent
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Utilisez la boîte de dialogue **Nouveau profil de l’Agent** pour créer un profil. Les nouveaux profils sont toujours dérivés de profils existants, mais il n'est pas possible de les modifier pour répondre aux besoins des applications. Lorsqu'un profil est créé, vous pouvez l'appliquer à des travaux de l'agent existants ou à venir dans la boîte de dialogue **Profils de l'Agent** . Vous pouvez modifier les valeurs de paramètre de l’agent dans la boîte de dialogue \<Propriétés de **Nom_Profil_Agent>**.  
  
## <a name="options"></a>Options  
 **Nom**  
 Entrez le nom du profil.  
  
 **Description**  
 Entrez la description du profil  
  
 **Paramètre**  
 Paramètres de l'agent contenus dans le profil. Le profil de base dont est dérivé le nouveau profil ne nécessite pas obligatoirement une valeur pour chaque paramètre. Pour connaître tous les paramètres valides pour un agent donné, désactivez la case à cocher **Afficher uniquement les paramètres utilisés dans ce profil** . Pour la description de chaque paramètre, consultez :  
  
-   [Agent d’instantané de réplication](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [Agent de lecture du journal des réplications](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Agent de distribution de réplication](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [Agent de fusion de réplication](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [Agent de lecture de la file d’attente de réplication](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 **Valeur par défaut**  
 Valeur par défaut de chaque paramètre de l'agent.  
  
 **Valeur**  
 Valeur du paramètre spécifié dans le profil de base du nouveau profil. Modifiez les paramètres voulus.  
  
 **Afficher uniquement les paramètres utilisés dans ce profil**  
 Désactivez cette case pour afficher tous les paramètres valides d'un agent donné.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des profils d’Agent de réplication](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Profils de l’Agent de réplication](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
