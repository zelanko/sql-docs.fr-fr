---
title: Nouveau profil de l’Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8549be8d4c8a40aaaa35c171e0d2183c7b490768
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039750"
---
# <a name="new-agent-profile"></a>Nouveau profil de l'Agent
  Utilisez la boîte de dialogue **Nouveau profil de l'Agent** pour créer un profil. Les nouveaux profils sont toujours dérivés de profils existants, mais il n'est pas possible de les modifier pour répondre aux besoins des applications. Lorsqu'un profil est créé, vous pouvez l'appliquer à des travaux de l'agent existants ou à venir dans la boîte de dialogue **Profils de l'Agent** . Vous pouvez modifier les valeurs de paramètre de l’agent dans la boîte de dialogue \<Propriétés de **Nom_Profil_Agent>**.  
  
## <a name="options"></a>Options  
 **Nom**  
 Entrez le nom du profil.  
  
 **Description**  
 Entrez la description du profil  
  
 **Paramètre**  
 Paramètres de l'agent contenus dans le profil. Le profil de base dont est dérivé le nouveau profil ne nécessite pas obligatoirement une valeur pour chaque paramètre. Pour connaître tous les paramètres valides pour un agent donné, désactivez la case à cocher **Afficher uniquement les paramètres utilisés dans ce profil** . Pour la description de chaque paramètre, consultez :  
  
-   [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
-   [Agent de lecture du journal des réplications](agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](agents/replication-distribution-agent.md)  
  
-   [Agent de fusion de réplication](agents/replication-merge-agent.md)  
  
-   [Agent de lecture de la file d’attente de réplication](agents/replication-queue-reader-agent.md)  
  
 **Valeur par défaut**  
 Valeur par défaut de chaque paramètre de l'agent.  
  
 **Valeur**  
 Valeur du paramètre spécifié dans le profil de base du nouveau profil. Modifiez les paramètres voulus.  
  
 **Afficher uniquement les paramètres utilisés dans ce profil**  
 Désactivez cette case pour afficher tous les paramètres valides d'un agent donné.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des profils d’Agent de réplication](agents/work-with-replication-agent-profiles.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)   
 [Profils de l’Agent de réplication](agents/replication-agent-profiles.md)  
  
  