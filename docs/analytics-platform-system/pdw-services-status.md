---
title: "État des Services PDW (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fc9bee2-c372-4c4a-956c-fb54215d8918
caps.latest.revision: "14"
ms.openlocfilehash: 7a6b1a1f9a6ef922833930abf00ca10482648141
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="pdw-services-status"></a>État des Services PDW
Parallel Data Warehouse **l’état des Services** page dans Microsoft Analytique plateforme système Configuration Manager affiche l’état actuel de tous les services SQL Server PDW et offre la possibilité d’arrêter et démarrer les services PDW. Il s’agit de la seule méthode prise en charge pour démarrer et arrêter les services PDW. Notez que des composants ou services ne peut pas être redémarrées de manière indépendante.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>Pour démarrer ou arrêter les services d’application  
  
1.  Pour démarrer les services d’application, cliquez sur **démarrer une Appliance**.  
  
2.  Pour arrêter les services d’application, cliquez sur **arrêter l’Appliance**.  
  
Il n’est pas nécessaire de cliquer sur **appliquer** lors du démarrage et arrêt des services d’application à l’aide de **démarrer une Appliance** et **arrêter l’Appliance**.  
  
![Services de PDW des appliances DWConfig](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> L’arrêt de la région PDW arrête également l’agent PDW (sqldwagent) sur les nœuds de la HDInsight région. La HDInsight région fonctionne toujours, mais le contrôle d’intégrité ne sera pas disponible. (L’agent PDW nécessite le nœud de contrôle PDW pour signaler le contrôle d’intégrité).  
  
## <a name="see-also"></a>Voir aussi  
[L’alimentation de l’Appliance APS ou désactiver &#40; Système de plateforme Analytique &#41;](power-the-aps-appliance-on-or-off.md)  
  
