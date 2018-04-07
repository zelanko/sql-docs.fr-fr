---
title: Dispositif d’analyse avec System Center Operations Manager (APS)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de6cbf6e-f2e9-4877-94df-9c13b1182d56
caps.latest.revision: 14
ms.openlocfilehash: 02bdd22c66729ab471298e211b619e1cb1e4565c
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="monitor-the-appliance-by-using-system-center-operations-manager"></a>Surveiller l’application à l’aide de System Center Operations Manager
Cette section décrit comment utiliser System Center Operations Manager pour surveiller SQL Server PDW et HDInsight.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Configuration requise  
  
1.  System Center Operations Manager 2007 R2, 2012 ou 2012 SP1 doit être installé et en cours d’exécution.  
  
2.  SQL Server 2008 R2 Native Client ou SQL Server 2012 Native Client doit être installé.  
  
3.  Les packs d’administration pour analyser SQL Server PDW et HDInsight doivent être installés, importés et configurés. Utilisez les informations suivantes pour obtenir des instructions pour effectuer ces tâches.  
  
    -   [Installer les Packs d’administration SCOM &#40;Analytique plate-forme système&#41;](install-the-scom-management-packs.md)  
  
    -   [Importez le Pack d’administration SCOM pour PDW &#40;Analytique plate-forme système&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Configurer SCOM pour surveiller le système de plateforme Analytique &#40;Analytique plate-forme système&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>Pour surveiller SQL Server PDW avec SCOM  
Après avoir configuré les Packs d’administration SCOM, cliquez sur le volet analyse de SCOM et accéder à **SQL Server Appliance** , puis **Microsoft SQL Server Parallel Data Warehouse**. Sous Microsoft SQL Server Parallel Data Warehouse, il existe quatre options : alertes, appareils, diagramme d’application et nœuds.  
  
### <a name="alerts"></a>Alertes  
Les alertes sont où vous pouvez rechercher des alertes en cours à gérer.  
  
![Alerts](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>Appliances  
Appareils sont où vous trouverez les appareils actuellement détectés et analysés SQL Server PDW dans votre environnement. Si une appliance n’affiche pas ici, et vous avez créé la connexion ODBC pour celle-ci, puis il peut être un problème avec votre compte PDWWatcher. Si elles apparaissent comme « Non analysé » peut avoir un problème avec votre compte PDWMonitor. Soyez patient SCOM ne pas apporte des modifications en temps réel, mais vérifie périodiquement pour les nouveaux équipements à surveiller et envoie régulièrement des requêtes pour les appareils pour l’analyse.  
  
![Appliances](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>Diagramme des appliances  
La Page de diagramme des Appliances est où vous pouvez obtenir les examiner l’intégrité de votre application avec une vue d’arborescence :  
  
![Appliances diagram](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>Nœuds  
Enfin, l’affichage de nœuds permet de voir l’intégrité de votre application sur chaque nœud :  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Alertes de la Console Administration de présentation &#40;Analytique plate-forme système&#41;](understanding-admin-console-alerts.md)  
  
