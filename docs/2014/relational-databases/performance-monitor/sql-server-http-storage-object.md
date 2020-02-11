---
title: SQL Server, HTTP_STORAGE_OBJECT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f104f7a6395442484be15f1e72c849edbf11e74f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70152680"
---
# <a name="sql-server-http_storage_object"></a>SQL Server, HTTP_STORAGE_OBJECT
  L’objet de performance **SqlServer : HTTP_STORAGE_OBJECT** est constitué de compteurs de performances qui surveillent le compte de stockage Azure. À l’aide [des fichiers de données SQL Server dans Azure](../databases/sql-server-data-files-in-microsoft-azure.md) , vous pouvez stocker des fichiers de base de données dans des objets BLOB de stockage Azure. Cet objet de performance traite chaque compte de stockage Azure en tant que lecteur différent.  
  
|Nom de compteur|Description|  
|------------------|-----------------|  
|**Octets de lecture/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations de lecture.|  
|**Octets d’écriture/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations d'écriture.|  
|**Nombre total d’octets/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations de lecture et d'écriture.|  
|**Lectures/s**|Nombre de lectures par seconde sur le stockage HTTP.|  
|**Écritures/s**|Nombre d'écritures par seconde sur le stockage HTTP.|  
|**Transferts/s**|Nombre d'opérations de lecture et d'écriture par seconde sur le stockage HTTP.|  
|**Nombre moyen d’octets/lecture**|Nombre moyen d'octets transférés du stockage HTTP par lecture.|  
|**Nombre moyen d’octets/écriture**|Nombre moyen d'octets transférés du stockage HTTP par écriture.|  
|**Nombre moyen d’octets/transfert**|Nombre moyen d'octets transférés du stockage HTTP pendant des opérations de lecture ou d'écriture.|  
|**Moyenne microsecondes/lecture**|Nombre moyen de microsecondes nécessaires pour chaque lecture à partir du stockage HTTP.|  
|**Moyenne microsecondes/écriture**|Nombre moyen de microsecondes nécessaires pour chaque écriture sur le stockage HTTP.|  
|**Nombre moyen de microsecondes/transfert**|Nombre moyen de microsecondes nécessaires pour chaque transfert vers le stockage HTTP.|  
|**E/s stockage HTTP en suspens**|Nombre total d'E/S en attente vers un stockage HTTP.|  
|**Nouvelle tentative d’e/s de stockage HTTP/s**|Nombre de demandes de nouvelle tentative envoyées au stockage HTTP par seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
