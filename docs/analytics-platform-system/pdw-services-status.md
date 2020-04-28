---
title: État des services PDW
description: État des services de Data Warehouse parallèles pour Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2789c8b74420a56a32d08a0339d4ee6d3cc112d1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400852"
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>État des services de Data Warehouse parallèles pour Analytics Platform System
La page **État des services** de Data Warehouse parallèles du Microsoft Analytics Platform System Configuration Manager affiche l’état actuel de tous les services SQL Server PDW, et permet d’arrêter et de démarrer les services PDW. Il s’agit de la seule méthode prise en charge pour démarrer et arrêter les services PDW. Notez que les composants ou services individuels ne peuvent pas être démarrés indépendamment.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>Pour démarrer ou arrêter les services de l’appliance  
  
1.  Pour démarrer les services de l’appliance, cliquez sur **Démarrer l’appliance**.  
  
2.  Pour arrêter les services de l’appareil, cliquez sur **arrêter l’appareil**.  
  
Il n’est pas nécessaire de cliquer sur **appliquer** pour démarrer et arrêter les services de l’appliance à l’aide de l' **appliance de démarrage** et d’arrêt de l' **Appliance**.  
  
![Services d'PDW des appliances DWConfig](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> L’arrêt de la région PDW arrête également l’agent PDW (sqldwagent) sur les nœuds. L’agent PDW nécessite que le nœud de contrôle PDW pour signaler le contrôle d’intégrité.  
  
## <a name="see-also"></a>Voir aussi  
[Mettez sous tension l’appliance APS ou désactivez &#40;Analytics Platform System&#41;](power-the-aps-appliance-on-or-off.md)  
  
