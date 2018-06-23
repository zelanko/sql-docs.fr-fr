---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5ff4ca4df43667dce7a5afe60dba95f33c0690eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045559"
---
# <a name="mssqleng014150"></a>MSSQL_ENG014150
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14150|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Réplication-%s : réussite de l'agent %s. %s|  
  
## <a name="explanation"></a>Explication  
 Ce message indique qu'un agent de réplication s'est correctement exécuté. La réplication utilise les agents suivants :  
  
-   L'Agent d'instantané. Cet agent est utilisé par toutes les publications.  
  
-   L'Agent de lecture du journal. Cet agent est utilisé par toutes les publications transactionnelles.  
  
-   L'Agent de lecture de la file d'attente. Cet agent est utilisé par les publications transactionnelles pour lesquelles les abonnements mis à jour en file d'attente sont activés.  
  
-   L'Agent de distribution. Cet agent synchronise les abonnements aux publications transactionnelles et aux publications d'instantané.  
  
-   L'Agent de fusion. Cet agent synchronise les abonnements aux publications de fusion.  
  
-   Travaux de maintenance de la réplication  
  
## <a name="user-action"></a>Action de l'utilisateur  
 L'Agent de lecture du journal, l'Agent de lecture de la file d'attente et l'Agent de distribution s'exécutent généralement en continu, tandis que les autres agents s'exécutent généralement à la demande ou selon un calendrier. Si vous ne pensez pas qu'un agent doit avoir terminé son exécution, vérifiez son état. Pour plus d’informations, voir [Monitor Replication Agents](agents/replication-agents.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administration de l’Agent de réplication](agents/replication-agent-administration.md)   
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)   
 [Agent de distribution de réplication](agents/replication-distribution-agent.md)   
 [Agent de lecture du journal de réplication](agents/replication-log-reader-agent.md)   
 [Agent de fusion de réplication](agents/replication-merge-agent.md)   
 [Agent de lecture de la file d’attente de réplication](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  