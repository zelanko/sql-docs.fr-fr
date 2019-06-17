---
title: SQL Server, réplica de base de données | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SQLServer:Database Replica
- performance counters [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], performance counters
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: e9f3a9a7a51bd0ca96a21806a11334df6f264753
ms.sourcegitcommit: cc4651df495920413ad54f585dbbe5ccef728899
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749142"
---
# <a name="sql-server-database-replica"></a>SQL Server, réplica de base de données

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L’objet de performance **SQLServer:Database Replica** contient des compteurs de performances qui communiquent des informations sur les bases de données secondaires d’un groupe de disponibilité Always On dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Cet objet est valide uniquement sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge un réplica secondaire.  
  
|Nom du compteur|Description|Vue sur…|  
|------------------|-----------------|--------------|  
|**Octets de fichier reçus/s**|Quantité de données FILESTREAM reçue par le réplica secondaire pour la base de données secondaire au cours de la dernière seconde.|Réplica secondaire|  
|**File des blocs du journal en attente d’application**|Nombre de blocs de journal en attente d’application au réplica de base de données.|Réplica secondaire|
|**File des blocs du journal prêts pour application**|Nombre de blocs de journal en attente, qui sont prêts à être appliqués au réplica de base de données.|Réplica secondaire|
|**Octets de journal reçus/s**|Quantité d'enregistrements du journal reçue par le réplica secondaire pour la base de données au cours de la dernière seconde.|Réplica secondaire|  
|**Taille de journal restante pour l'annulation**|Quantité de journal, en kilo-octets, restant pour terminer la phase de restauration.|Réplica secondaire|  
|**File d'attente d'envoi du journal**|Quantité d’enregistrements du journal dans les fichiers journaux de la base de données primaire, en kilo-octets, qui n’ont pas encore été envoyés au réplica secondaire. Cette valeur est envoyée au réplica secondaire à partir du réplica principal. La taille de file d’attente n’inclut pas les fichiers FILESTREAM envoyés à un réplica secondaire.|Réplica secondaire|  
|**Transactions d'écriture en miroir/s**|Nombre de transactions qui ont été écrites dans la base de données primaire et qui ont ensuite attendu que le journal soit envoyé à la base de données secondaire pour être validées, au cours de la dernière seconde.|Réplica principal|  
|**File de récupération**|Quantité d’enregistrements du journal dans les fichiers journaux du réplica secondaire qui n’ont pas été réexécutés.|Réplica secondaire|  
|**Restauration par progression bloquée/s**|Nombre de fois que le thread de restauration a été bloqué sur des verrous détenus par les lecteurs de la base de données.|Réplica secondaire|  
|**Octets restants de restauration par progression**|Taille de journal restante, en kilo-octets, avant la fin de la phase de restauration.|Réplica secondaire|  
|**Octets réexécutés/s**|Quantité d'enregistrements du journal réexécutée sur la base de données secondaire au cours de la dernière seconde.|Réplica secondaire|  
|**Taille totale de journal nécessitant une annulation**|Nombre total de kilo-octets du journal qui doivent être annulés.|Réplica secondaire|  
|**Délai de transaction**|Délai d’attente d’accusé de réception de validation non terminée pour toutes les transactions en cours, en millisecondes. Divisez cette valeur par *Transactions d’écriture en miroir/s* pour obtenir le *délai de transaction moyen*. Pour plus d’informations, consultez [SQL Server 2012 AlwaysOn – Part 12 – Performance Aspects and Performance Monitoring II](https://blogs.msdn.microsoft.com/saponsqlserver/2013/04/24/sql-server-2012-alwayson-part-12-performance-aspects-and-performance-monitoring-ii/).|Réplica principal|  
  
## <a name="see-also"></a> Voir aussi
  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, réplica de disponibilité](../../relational-databases/performance-monitor/sql-server-availability-replica.md)   
 [SQL Server, objet Databases](../../relational-databases/performance-monitor/sql-server-databases-object.md)   
 [Groupes de disponibilité Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  