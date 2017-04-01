---
title: "Cat&#233;gorie d&#39;&#233;v&#233;nement Rapports de progression | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "événements de progression [Analysis Services]"
  - "Rapports de progression, catégorie d'événement"
  - "classes d’événements [Analysis Services], rapports de progression"
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 23
---
# Cat&#233;gorie d&#39;&#233;v&#233;nement Rapports de progression
  La catégorie d'événement Rapports de progression contient les classes d'événements décrites dans le tableau ci-dessous.  
  
|Classe d'événements|ID d'événement|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|Collecte tous les événements de début de rapport de progression depuis le début de la trace.|  
|Progress Report End|6|Collecte tous les événements de fin de rapport de progression depuis le début de la trace.|  
|Progress Report Current|7|Collecte tous les événements actuels de rapport de progression depuis le début de la trace. Par exemple, au cours du traitement, les rapports actuels incluent les informations de traitement sur les objets en cours de traitement (dimensions, partitions, cube, etc.).|  
|Progress Report Error|8|Collecte tous les événements d'erreur de rapport de progression depuis le début de la trace.|  
  
 Chaque événement de début de rapport de progression commence par un flux d'événements de rapport de progression et se termine par un événement de fin de rapport de progression. Le flux peut contenir n'importe quel nombre d'événements actuels de rapport de progression et d'événements d'erreur de rapport de progression.  
  
 Pour plus d’informations sur les colonnes associées à chaque classe d’événements Progress Report, consultez [Colonnes de données des rapports de progression](../../analysis-services/trace-events/progress-reports-data-columns.md).  
  
## Voir aussi  
 [Événements de trace Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  