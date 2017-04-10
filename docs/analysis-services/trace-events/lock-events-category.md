---
title: "Cat&#233;gorie d&#39;&#233;v&#233;nements de verrou | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 06427f8e-89bb-4710-a0c1-dc5e42b7e95e
caps.latest.revision: 6
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 6
---
# Cat&#233;gorie d&#39;&#233;v&#233;nements de verrou
  La catégorie d'événement Locks Events contient les classes d'événements décrites dans le tableau ci-dessous.  
  
|Classe d'événements|ID d'événement|Description|  
|-----------------|--------------|-----------------|  
|Deadlock|50|Recueille tous les événements d'interblocage des verrous de métadonnées depuis que la trace a démarré.|  
|Lock timeout|51|Recueille tous les événements de délai d'expiration des verrous de métadonnées depuis que la trace a démarré.|  
|Lock Acquired|52|Recueille des informations sur les verrous acquis, depuis le début de la trace.|  
|Lock Released|53|Recueille des informations sur les verrous libérés, depuis le début de la trace.|  
|Lock Waiting|54|Collecte des informations sur les verrous en attente, depuis le début de la trace.|  
  
 Pour plus d'informations sur les colonnes associées à chaque classe d'événements Lock, consultez [Lock Events Data Columns](../../analysis-services/trace-events/lock-events-data-columns.md).  
  
## Voir aussi  
 [Événements de trace Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  