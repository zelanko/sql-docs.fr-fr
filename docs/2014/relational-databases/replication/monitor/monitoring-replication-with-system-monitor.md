---
title: Surveillance de la réplication avec le moniteur système | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], System Monitor
- System Monitor [SQL Server], replication
- performance counters [SQL Server replication]
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b5d1a63937a11da4703ec4ef0338dee89a5c33f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52815581"
---
# <a name="monitoring-replication-with-system-monitor"></a>Contrôle de la réplication avec le Moniteur système
  Le Moniteur système[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows permet d'utiliser des diagrammes, des graphiques et des rapports pour évaluer l'efficacité de votre ordinateur, identifier et résoudre les problèmes éventuels (utilisation déséquilibrée des ressources, configuration matérielle insuffisante ou conception logicielle déficiente) et anticiper les besoins matériels. Pour plus d’informations, consultez [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../performance-monitor/monitor-resource-usage-system-monitor.md).  
  
 Le Moniteur système utilise des objets et des compteurs de performance qui fournissent des informations sur les performances de divers processus. Vous pouvez mesurer les performances de la réplication via des compteurs associés aux agents de réplication :  
  
|Agent|Objet de performance|Compteur|Description|  
|-----------|------------------------|-------------|-----------------|  
|Tous les agents|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Agents de réplication|Exécution en cours|Nombre d'agents de réplication actuellement en cours d'exécution.|  
|Agent d'instantané|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Instantané de réplication|Instantané : Commandes livrées/seconde|Nombre de commandes par seconde transmises au serveur de distribution.|  
|Agent d'instantané|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Instantané de réplication|Instantané : Transactions livrées/seconde|Nombre de transactions par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Journal des réplications|Lecteur de journal : Commandes livrées/seconde|Nombre de commandes par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Journal des réplications|Lecteur de journal : Transactions livrées/seconde|Nombre de transactions par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Journal des réplications|Lecteur de journal : Latence de livraison|Durée, en millisecondes, écoulée entre le moment où les transactions sont appliquées sur le serveur de publication et le moment où elles sont délivrées au serveur de distribution.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : Commandes livrées/seconde|Le nombre de commandes par seconde transmises à l'abonné.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : Transactions livrées/seconde|Nombre de transactions par seconde transmises à l'abonné.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : Latence de livraison|Durée, en millisecondes, écoulée entre le moment où les transactions sont délivrées au serveur de distribution et le moment où elles sont appliquées à l'Abonné.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Fusion de réplication|Conflits/seconde|Nombre de conflits par seconde qui se produisent lors du processus de fusion.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Fusion de réplication|Modifications téléchargées/seconde|Nombre de lignes par seconde répliquées du serveur de publication à l'Abonné.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Fusion de réplication|Modifications téléchargées/seconde|Nombre de lignes par seconde répliquées de l'Abonné au serveur de publication.|  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance &#40;réplication&#41;](../monitoring-replication.md)  
  
  
