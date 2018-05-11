---
title: Catégorie d’événement des rapports de progression | Documents Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4722ea18e493a243e6adaf64555c4e90ec4b165
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="progress-reports-event-category"></a>Rapports de progression, catégorie d'événement
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La catégorie d'événement Rapports de progression contient les classes d'événements décrites dans le tableau ci-dessous.  
  
|Classe d'événements|ID d'événement|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|Collecte tous les événements de début de rapport de progression depuis le début de la trace.|  
|Progress Report End|6|Collecte tous les événements de fin de rapport de progression depuis le début de la trace.|  
|Progress Report Current|7|Collecte tous les événements actuels de rapport de progression depuis le début de la trace. Par exemple, au cours du traitement, les rapports actuels incluent les informations de traitement sur les objets en cours de traitement (dimensions, partitions, cube, etc.).|  
|Progress Report Error|8|Collecte tous les événements d'erreur de rapport de progression depuis le début de la trace.|  
  
 Chaque événement de début de rapport de progression commence par un flux d'événements de rapport de progression et se termine par un événement de fin de rapport de progression. Le flux peut contenir n'importe quel nombre d'événements actuels de rapport de progression et d'événements d'erreur de rapport de progression.  
  
 Pour plus d’informations sur les colonnes associées à chaque classe d’événements Progress Report, consultez [Colonnes de données des rapports de progression](../../analysis-services/trace-events/progress-reports-data-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de Trace Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
