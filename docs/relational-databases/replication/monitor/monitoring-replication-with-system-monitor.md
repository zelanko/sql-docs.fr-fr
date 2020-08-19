---
description: Contrôle de la réplication avec le Moniteur système
title: Surveillance de la réplication avec le moniteur système | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
ms.openlocfilehash: 4af6d03aa3898fdf91dc7e60fb8c5634a56e87b8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88380265"
---
# <a name="monitoring-replication-with-system-monitor"></a>Contrôle de la réplication avec le Moniteur système
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Le Moniteur système[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows permet d'utiliser des diagrammes, des graphiques et des rapports pour évaluer l'efficacité de votre ordinateur, identifier et résoudre les problèmes éventuels (utilisation déséquilibrée des ressources, configuration matérielle insuffisante ou conception logicielle déficiente) et anticiper les besoins matériels. Pour plus d’informations, consultez [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md).  
  
 Le Moniteur système utilise des objets et des compteurs de performance qui fournissent des informations sur les performances de divers processus. Vous pouvez mesurer les performances de la réplication via des compteurs associés aux agents de réplication :  
  
|Agent|Objet de performance|Compteur|Description|  
|-----------|------------------------|-------------|-----------------|  
|Tous les agents|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] : Agents de réplication|Exécution en cours|Nombre d'agents de réplication actuellement en cours d'exécution.|  
|Agent d'instantané|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Réplication d'instantané|Instantané : commandes livrées/s|Nombre de commandes par seconde transmises au serveur de distribution.|  
|Agent d'instantané|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Réplication d'instantané|Instantané : transactions livrées/s|Nombre de transactions par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lecteur du journal des réplications|Lecteur de journal : commandes livrées/s|Nombre de commandes par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lecteur du journal des réplications|Lecteur de journal : transactions livrées/s|Nombre de transactions par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lecteur du journal des réplications|Lecteur de journal : latence de livraison|Durée, en millisecondes, écoulée entre le moment où les transactions sont appliquées sur le serveur de publication et le moment où elles sont délivrées au serveur de distribution.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : commandes livrées/s|Le nombre de commandes par seconde transmises à l'abonné.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : transactions livrées/s|Nombre de transactions par seconde transmises à l'abonné.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : latence de livraison|Durée, en millisecondes, écoulée entre le moment où les transactions sont délivrées au serveur de distribution et le moment où elles sont appliquées à l'Abonné.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Réplication de fusion|Conflits/seconde|Nombre de conflits par seconde qui se produisent lors du processus de fusion.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Réplication de fusion|Modifications téléchargées/seconde|Nombre de lignes par seconde répliquées du serveur de publication à l'Abonné.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Réplication de fusion|Modifications téléchargées/seconde|Nombre de lignes par seconde répliquées de l'Abonné au serveur de publication.|  
  
## <a name="see-also"></a>Voir aussi  
 [Supervision &#40;réplication&#41;](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
