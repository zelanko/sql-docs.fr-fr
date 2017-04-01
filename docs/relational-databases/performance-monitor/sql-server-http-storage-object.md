---
title: "SQL&#160;Server, HTTP_STORAGE_OBJECT | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae849f79-c581-42a5-a5cc-0a9ebea171b9
caps.latest.revision: 7
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 7
---
# SQL&#160;Server, HTTP_STORAGE_OBJECT
  L’objet de performance **SQLServer:HTTP_STORAGE_OBJECT** est constitué de compteurs de performances qui surveillent le compte Microsoft Azure Storage. La fonctionnalité [Fichiers de données SQL Server de Microsoft Azure](../../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) permet d’enregistrer les fichiers de base de données dans Azure Storage Blob. Cet objet de performance traite chaque compte de stockage Windows Azure en tant que lecteur différent.  
  
|Nom du compteur|Description|  
|------------------|-----------------|  
|**Octets lus/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations de lecture.|  
|**Octets écrits/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations d'écriture.|  
|**Octets totaux/s**|Quantité de données transférées du stockage HTTP par seconde pendant des opérations de lecture et d'écriture.|  
|**Lectures/s**|Nombre de lectures par seconde sur le stockage HTTP.|  
|**logiques/s**|Nombre d'écritures par seconde sur le stockage HTTP.|  
|**Transferts/s**|Nombre d'opérations de lecture et d'écriture par seconde sur le stockage HTTP.|  
|**Nombre moyen d'octets/lecture**|Nombre moyen d'octets transférés du stockage HTTP par lecture.|  
|**Nombre moyen BASE octets/lecture**|À usage interne uniquement|
|**Nombre moyen d'octets/transfert**|Nombre moyen d'octets transférés du stockage HTTP pendant des opérations de lecture ou d'écriture.|  
|**Nombre moyen BASE octets/transfert**|À usage interne uniquement|
|**Nombre moyen d'octets/écriture**|Nombre moyen d'octets transférés du stockage HTTP par écriture.|  
|**Nombre moyen BASE octets/écriture**|À usage interne uniquement|
|**Nombre moyen de microsecondes/lecture**|Nombre moyen de microsecondes nécessaires pour chaque lecture à partir du stockage HTTP.|  
|**Nombre moyen BASE microsecondes/lecture**|À usage interne uniquement|
|**Nombre moyen Comp. microsecondes/lecture**|Nombre moyen de microsecondes nécessaires au protocole HTTP pour achever la lecture du stockage.| 
|**Nombre moyen BASE comp. microsecondes/lecture**|À usage interne uniquement|
|**Nombre moyen de microsecondes/écriture**|Nombre moyen de microsecondes nécessaires pour chaque écriture sur le stockage HTTP.|  
|**Nombre moyen de microsecondes/transfert**|Nombre moyen de microsecondes nécessaires pour chaque transfert vers le stockage HTTP.|  
|**Nombre moyen BASE microsecondes/transfert**|À usage interne uniquement|
|**Nombre moyen BASE microsecondes/écriture**|À usage interne uniquement|
|**Nombre moyen Comp. microsecondes/écriture**|Nombre moyen de microsecondes nécessaires au protocole HTTP pour achever l’écriture dans le stockage.|  
|**Nombre moyen BASE comp. microsecondes/écriture**|À usage interne uniquement|
|**E/S en attente vers le stockage HTTP**|Nombre total d'E/S en attente vers un stockage HTTP.|  
|**Échec/s des ES de stockage HTTP**|Nombre de requêtes d’écriture échouées envoyées au stockage HTTP par seconde.| 
|**Nouvelle tentative d'E/S au stockage HTTP/s**|Nombre de demandes de nouvelle tentative envoyées au stockage HTTP par seconde.|  
  
## Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  