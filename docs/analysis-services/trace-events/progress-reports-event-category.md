---
title: Catégorie d’événement des rapports de progression | Documents Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f1b177defd7a767925d4f429d57507ec62a0a3d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
  
  
