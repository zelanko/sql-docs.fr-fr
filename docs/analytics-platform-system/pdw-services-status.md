---
title: État - des services PDW Analytique Platform System | Microsoft Docs
description: État des services de système de plateforme d’Analytique Parallel Data Warehouse (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3db994b4869c1b017a079b404af3d95db1316dad
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960367"
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>État des services de Parallel Data Warehouse pour l’Analytique Platform System
Parallel Data Warehouse **l’état des Services** page dans le Microsoft Analytique Platform System Configuration Manager affiche l’état actuel de tous les services SQL Server PDW et offre la possibilité d’arrêter et démarrer les services PDW. Il s’agit de la seule méthode prise en charge pour le démarrage et arrêt des services PDW. Notez que des composants ou services ne peut pas être redémarrées de manière indépendante.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>Pour démarrer ou arrêter les services de l’appliance  
  
1.  Pour démarrer les services de l’appliance, cliquez sur **démarrer une Appliance**.  
  
2.  Pour arrêter les services de l’appliance, cliquez sur **arrêter une Appliance**.  
  
Il n’est pas nécessaire de cliquer sur **appliquer** lors du démarrage et arrêt des services appliance à l’aide de **démarrer une Appliance** et **arrêter une Appliance**.  
  
![Services de PDW des appliances DWConfig](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> L’arrêt de la région PDW arrête également l’agent PDW (sqldwagent) sur les nœuds. L’agent PDW nécessite le nœud de contrôle PDW pour signaler l’intégrité.  
  
## <a name="see-also"></a>Voir aussi  
[Activé ou désactivé, l’alimentation de l’Appliance APS &#40;Analytique Platform System&#41;](power-the-aps-appliance-on-or-off.md)  
  
