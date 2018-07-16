---
title: Catégorie d’événements de verrouillage | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 06427f8e-89bb-4710-a0c1-dc5e42b7e95e
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a3fc63269fdaff254ef2dfd412ef3a706abb09d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302769"
---
# <a name="lock-events-category"></a>Catégorie d'événements de verrou
  La catégorie d'événement Locks Events contient les classes d'événements décrites dans le tableau ci-dessous.  
  
|Classe d'événements|ID d'événement|Description|  
|-----------------|--------------|-----------------|  
|Deadlock|50|Recueille tous les événements d'interblocage des verrous de métadonnées depuis que la trace a démarré.|  
|Lock timeout|51|Recueille tous les événements de délai d'expiration des verrous de métadonnées depuis que la trace a démarré.|  
|Lock Acquired|52|Recueille des informations sur les verrous acquis, depuis le début de la trace.|  
|Lock Released|53|Recueille des informations sur les verrous libérés, depuis le début de la trace.|  
|Lock Waiting|54|Collecte des informations sur les verrous en attente, depuis le début de la trace.|  
  
 Pour plus d'informations sur les colonnes associées à chaque classe d'événements Lock, consultez [Lock Events Data Columns](lock-events-data-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de trace Analysis Services](analysis-services-trace-events.md)  
  
  
