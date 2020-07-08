---
title: SQL Server, objet Catalog Metadata | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 5c8b74e6647422231f0ace765f57579bb3ea2b84
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85656182"
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, objet Catalog Metadata
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
L’objet de performance **SQLServer:Catalog Metadata** fournit des compteurs pour les métadonnées de catalogue pour SQL Server.

Le tableau suivant décrit les objets de performance **Métadonnées de catalogue** SQL Server.


|**Compteurs de métadonnées de catalogue SQLServer**|Description|  
|-------------|-----------------|  
|**Nombre d’entrées de cache**|Nombre d’entrées dans le cache de métadonnées de catalogue.|
|**Nombre d’entrées de cache épinglées**|Nombre d’entrées épinglées du cache de métadonnées de catalogue.|
|**Taux d'accès au cache**|Rapport entre les accès au cache de métadonnées de catalogue et les recherches.|
|**Base du taux d’accès au cache**|À usage interne uniquement.|

Il existe une instance du compteur pour chaque base de données.

## <a name="see-also"></a>Voir aussi  
[Analyser l'utilisation des ressources (Moniteur système)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
