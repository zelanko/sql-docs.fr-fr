---
title: Surveiller avec SCOM
description: Utilisez System Center Operations Manager (SCOM) pour surveiller l’appliance Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 0b244d85e601e46fe778298e723c0a7d01e669bb
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400968"
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>Surveiller avec System Center Operations Manager-Analytics Platform System
Utilisez System Center Operations Manager (SCOM) pour surveiller l’appliance Analytics Platform System (APS).
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Conditions préalables  
  
1.  System Center Operations Manager 2007 R2, 2012 ou 2012 SP1 doit être installé et en cours d’exécution.  
  
2.  SQL Server 2008 R2 Native Client ou SQL Server 2012 Native Client doit être installé.  
  
3.  Les packs d’administration à surveiller SQL Server PDW doivent être installés, importés et configurés. Utilisez les articles suivants pour obtenir des instructions sur l’exécution de ces tâches.  
  
    -   [Installer les packs d’administration SCOM &#40;système de plateforme Analytics&#41;](install-the-scom-management-packs.md)  
  
    -   [Importez le pack d’administration SCOM pour PDW &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Configurer SCOM pour surveiller Analytics Platform System &#40;Analytics Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>Pour surveiller SQL Server PDW avec SCOM  
Après la configuration des packs d’administration SCOM, cliquez sur le volet analyse de SCOM, puis explorez **SQL Server Appliance** , puis **Microsoft SQL Server Parallel Data Warehouse**. Sous Microsoft SQL Server Parallel Data Warehouse, vous avez le choix entre quatre options : alertes, Appliances, diagramme d’appliance et nœuds.  
  
### <a name="alerts"></a>Alertes  
Les alertes vous permettent de trouver les alertes en cours à gérer.  
  
![Alertes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>Appliances  
Les appliances sont là où vous trouverez les appliances SQL Server PDW actuellement découvertes et surveillées dans votre environnement. Si une appliance ne s’affiche pas ici et que vous avez créé la connexion ODBC pour celle-ci, il se peut qu’il y ait un problème avec votre compte PDWWatcher. S’ils apparaissent comme « non analysés », il se peut qu’il y ait un problème avec votre compte PDWMonitor. Soyez patient depuis que SCOM n’apporte pas de modifications en temps réel, mais il recherche régulièrement les nouvelles Appliances à surveiller et envoie régulièrement des requêtes aux appliances à des fins de surveillance.  
  
![SCM](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>Diagramme d’appliances  
La page du diagramme d’appliances vous permet d’examiner l’état d’intégrité de votre appliance à l’aide d’une arborescence :  
  
![Diagramme des appliances](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>Nœuds  
Enfin, la vue nœuds vous permet d’afficher l’intégrité de votre appliance via chaque nœud :  
  
![Ceux](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Fonctionnement des alertes de la console d’administration &#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md)  
  
