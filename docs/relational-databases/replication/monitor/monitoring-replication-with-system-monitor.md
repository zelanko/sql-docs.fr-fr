---
title: "Contr&#244;le de la r&#233;plication avec le Moniteur syst&#232;me | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analyse des performances [réplication SQL Server], Moniteur système"
  - "Moniteur système [SQL Server], réplication"
  - "compteurs de performances [réplication SQL Server]"
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Contr&#244;le de la r&#233;plication avec le Moniteur syst&#232;me
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Le Moniteur système Windows vous permet d’utiliser des graphiques, des graphiques et des rapports pour évaluer l’efficacité de votre ordinateur, identifier et résoudre les problèmes éventuels (utilisation déséquilibrée des ressources, configuration matérielle est insuffisante ou conception de déficiente) et planifier les besoins matériels. Pour plus d’informations, consultez [surveiller l’utilisation des ressources & #40 ; Moniteur système & #41 ;](../../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md).  
  
 Le Moniteur système utilise des objets et des compteurs de performance qui fournissent des informations sur les performances de divers processus. Vous pouvez mesurer les performances de la réplication via des compteurs associés aux agents de réplication :  
  
|Agent|Objet de performance|Compteur|Description|  
|-----------|------------------------|-------------|-----------------|  
|Tous les agents|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Agents de réplication|Exécution en cours|Nombre d'agents de réplication actuellement en cours d'exécution.|  
|Agent d'instantané|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Capture instantanée de réplication|Instantané : commandes livrées/s|Nombre de commandes par seconde transmises au serveur de distribution.|  
|Agent d'instantané|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Capture instantanée de réplication|Instantané : transactions livrées/s|Nombre de transactions par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lecteur de journal de réplication|Lecteur de journal : commandes livrées/s|Nombre de commandes par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lecteur de journal de réplication|Lecteur de journal : transactions livrées/s|Nombre de transactions par seconde transmises au serveur de distribution.|  
|l'Agent de lecture du journal ;|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Lecteur de journal de réplication|Lecteur de journal : latence de livraison|Durée, en millisecondes, écoulée entre le moment où les transactions sont appliquées sur le serveur de publication et le moment où elles sont délivrées au serveur de distribution.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : commandes livrées/s|Le nombre de commandes par seconde transmises à l'abonné.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : transactions livrées/s|Nombre de transactions par seconde transmises à l'abonné.|  
|Agent de distribution|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Distribution de réplication|Serveur de distribution : latence de livraison|Durée, en millisecondes, écoulée entre le moment où les transactions sont délivrées au serveur de distribution et le moment où elles sont appliquées à l'Abonné.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Fusion de réplication|Conflits/seconde|Nombre de conflits par seconde qui se produisent lors du processus de fusion.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Fusion de réplication|Modifications téléchargées/seconde|Nombre de lignes par seconde répliquées du serveur de publication à l'Abonné.|  
|Agent de fusion|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Fusion de réplication|Modifications téléchargées/seconde|Nombre de lignes par seconde répliquées de l'Abonné au serveur de publication.|  
  
## Voir aussi  
 [Analyse & #40 ; Réplication & #41 ;](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  