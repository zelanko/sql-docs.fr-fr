---
title: Stockage XTP SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 502ee4eb72f476d3e63eee6efbe2aaa21df88d75
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53379740"
---
# <a name="sql-server-xtp-storage"></a>Stockage XTP SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L’objet de performance SQL Server XTP Storage contient des compteurs liés au stockage sur disque pour l’OLTP en mémoire dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Ce tableau décrit les compteurs **SQL Server XTP Storage** .  
  
|Compteur|Description|  
|-------------|-----------------|  
|**Points de contrôle fermés**|Nombre de points de contrôle fermés effectués par l'agent en ligne.|  
|**Points de contrôle terminés**|Nombre de points de contrôle traités par le thread de point de contrôle hors connexion.|  
|**Fusions principales terminées**|Nombre de fusions principale exécutées par le thread de travail de fusion. Ces fusions ne sont pas encore installées.|  
|**Évaluations de la stratégie de fusion**|Nombre d'évaluations de la stratégie de fusion depuis le démarrage du serveur.|  
|**Demandes de fusion en attente**|Nombre de demandes de fusion en attente depuis le démarrage du serveur.|  
|**Fusions abandonnées**|Nombre de fusions abandonnées en raison d'un échec.|  
|**Fusions installées**|Nombre de fusions correctement installées.|  
|**Fichiers totaux fusionnés**|Nombre total de fichiers sources fusionnés. Ce nombre peut être utilisé pour rechercher le nombre moyen de fichiers sources dans la fusion.|  
  
## <a name="see-also"></a> Voir aussi  
 [SQL Server XTP &#40;OLTP en mémoire&#41;, compteurs de performances](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
