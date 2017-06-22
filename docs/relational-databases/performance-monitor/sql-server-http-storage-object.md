---
title: SQL Server, HTTP_STORAGE_OBJECT | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ea717edbbed863b262617e457ac29fc3d45a4be4
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-httpstorageobject"></a>SQL Server, HTTP_STORAGE_OBJECT
  L’objet de performance **SQLServer:HTTP_STORAGE_OBJECT** est constitué de compteurs de performances qui surveillent le compte Microsoft Azure Storage. La fonctionnalité [Fichiers de données SQL Server de Microsoft Azure](../../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) permet d’enregistrer les fichiers de base de données dans Azure Storage Blob. Cet objet de performance traite chaque compte de stockage Windows Azure en tant que lecteur différent.  
  
|Nom du compteur|Description|  
|------------------|-----------------|  
|**Octets lus/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations de lecture.|  
|**Octets écrits/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations d'écriture.|  
|**Octets totaux/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations de lecture et d'écriture.|  
|**Lectures/s**|Nombre de lectures par seconde sur le stockage HTTP.|  
|**logiques/s**|Nombre d'écritures par seconde sur le stockage HTTP.|  
|**Transferts/s**|Nombre d'opérations de lecture et d'écriture par seconde sur le stockage HTTP.|  
|**Nbre moyen octets/lecture**|Nombre moyen d'octets transférés du stockage HTTP par lecture.|  
|**Nbre moyen octets/lecture BASE**|À usage interne uniquement|
|**Nbre moyen octets/transfert**|Nombre moyen d'octets transférés du stockage HTTP pendant des opérations de lecture ou d'écriture.|  
|**Nbre moyen octets/transfert BASE**|À usage interne uniquement|
|**Nbre moyen octets/écriture**|Nombre moyen d'octets transférés du stockage HTTP par écriture.|  
|**Nbre moyen octets/écriture BASE**|À usage interne uniquement|
|**Nbre moyen microsecondes/lecture**|Nombre moyen de microsecondes nécessaires pour chaque lecture à partir du stockage HTTP.|  
|**Nbre moyen microsecondes/lecture BASE**|À usage interne uniquement|
|**Nbre moyen microsecondes/lecture achevée**|Nombre moyen de microsecondes nécessaires au protocole HTTP pour achever la lecture du stockage.| 
|**Nbre moyen microsecondes/lecture achevée BASE**|À usage interne uniquement|
|**Nbre moyen microsecondes/écriture**|Nombre moyen de microsecondes nécessaires pour chaque écriture sur le stockage HTTP.|  
|**Nbre moyen micros./transfert**|Nombre moyen de microsecondes nécessaires pour chaque transfert vers le stockage HTTP.|  
|**Nbre moyen micros./transfert BASE**|À usage interne uniquement|
|**Nbre moyen microsecondes/écriture BASE**|À usage interne uniquement|
|**Nbre moyen microsecondes/écriture achevée**|Nombre moyen de microsecondes nécessaires au protocole HTTP pour achever l’écriture dans le stockage.|  
|**Nbre moyen microsecondes/écriture achevée BASE**|À usage interne uniquement|
|**E/S en attente vers le stockage HTTP**|Nombre total d'E/S en attente vers un stockage HTTP.|  
|**Échec/s des ES de stockage HTTP**|Nombre de requêtes d’écriture échouées envoyées au stockage HTTP par seconde.| 
|**Nouvelle tentative d'E/S au stockage HTTP/s**|Nombre de demandes de nouvelle tentative envoyées au stockage HTTP par seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
