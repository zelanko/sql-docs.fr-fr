---
title: SQL Server, objet Broker TO Statistics | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1a8c5bc039e4e6c18680ba4e290ea7e69fa87804
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63250781"
---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server, objet Broker TO Statistics
  L’objet de performance SQL Server : Statistiques des objets de transmission de Service Broker communique des informations sur le nombre de fois que des dialogues [!INCLUDE[ssSB](../../includes/sssb-md.md)] demandent des objets de transmission et sur la fréquence à laquelle des objets de transmission sont écrits dans **tempdb**.  
  
 Les objets de transmission enregistrent l'état de transmissions de message pour un dialogue [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Ils sont stockés en mémoire. Pour libérer de la mémoire, [!INCLUDE[ssSB](../../includes/sssb-md.md)] écrit périodiquement des lots d’objets de transmission inactifs dans des tables de travail **tempdb**.  
  
 Le tableau ci-dessous répertorie les compteurs que cet objet contient.  
  
|Compteurs de Statistiques des objets de transmission de Service Broker|Description|  
|----------------------------------------------|-----------------|  
|**Durée moy. des écritures par lot**|Nombre moyen d'objets de transmission enregistrés dans un lot.|  
|**Durée moy. d’écriture d’un lot (ms)**|Nombre moyen de millisecondes requises pour enregistrer un lot d'objets de transmission.|  
|**Temps moyen entre les lots (MS)**|Nombre moyen de millisecondes entre des écritures de lots d'objets de transmission.|  
|**Objets de transmission obtenus/s**|Nombre de fois par seconde que les dialogues ont demandé des objets de transmission.|  
|**Nombre d'objets de transmission marqués comme modifiés/s**|Nombre de fois par seconde que les objets de transmission ont été marqués comme modifiés. Les objets de transmission sont marqués comme modifiés par la première modification qui entraîne une différence entre la copie en mémoire et la copie stockée dans **tempdb**. Les objets de transmission sont modifiés lorsque [!INCLUDE[ssSB](../../includes/sssb-md.md)] doit enregistrer une modification dans l'état des transmissions de message pour le dialogue.|  
|**Objets de transmission écrits/s**|Nombre de fois par seconde où un lot d’objets de transmission a été écrit dans les tables de travail **tempdb** . De grands nombres d'écritures peuvent indiquer que la mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est accentuée.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server, objet de méthodes d’accès](sql-server-access-methods-object.md)   
 [SQL Server, objet de gestionnaire de mémoire](sql-server-memory-manager-object.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
