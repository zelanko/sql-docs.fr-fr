---
title: SQL Server, objet Catalog Metadata | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
caps.latest.revision: 
author: dagiro
ms.author: v-dagir
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86913554f86a9965906d37f8a7ff683570dfb8ad
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, objet Catalog Metadata
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L’objet de performance **SQLServer:Catalog Metadata** fournit des compteurs pour les métadonnées de catalogue dans SQL Server.

Le tableau suivant décrit les objets de performance **Métadonnées de catalogue** SQL Server.


|**Compteurs de métadonnées de catalogue SQLServer**|Description|  
|-------------|-----------------|  
|**Nombre d’entrées de cache**|Nombre d’entrées dans le cache de métadonnées de catalogue.|
|**Nombre d’entrées de cache épinglées**|Nombre d’entrées épinglées du cache de métadonnées de catalogue.|
|**Taux d'accès au cache**|Rapport entre les accès au cache de métadonnées de catalogue et les recherches.|
|**Base du taux d’accès au cache**|À usage interne uniquement|

Il existe une instance du compteur pour chaque base de données.

## <a name="see-also"></a> Voir aussi  
[Analyser l'utilisation des ressources (Moniteur système)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
