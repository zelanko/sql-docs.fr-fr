---
title: SQL Server, objet Catalog Metadata | Microsoft Docs
description: Découvrez l’objet de performance SQLServer:Catalog Metadata, qui fournit des compteurs pour les métadonnées de catalogue dans SQL Server.
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
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: a02c8d6253df487ebf5c01c8658f448ec680022c
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505813"
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
