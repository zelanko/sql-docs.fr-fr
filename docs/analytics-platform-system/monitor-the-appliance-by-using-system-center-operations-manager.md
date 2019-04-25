---
title: Moniteur avec SCOM - Analytique Platform System | Microsoft Docs
description: Utilisez System Center Operations Manager (SCOM) pour surveiller l’appliance Analytique Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3c43734dbd7ef1a766f3f1258f97565ab82e175d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62639854"
---
# <a name="monitor-with-system-center-operations-manager---analytics-platform-system"></a>Moniteur avec System Center Operations Manager - Analytique Platform System
Utilisez System Center Operations Manager (SCOM) pour surveiller l’appliance Analytique Platform System (APS).
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Prérequis  
  
1.  System Center Operations Manager 2007 R2, 2012 ou 2012 SP1 doit être installé et en cours d’exécution.  
  
2.  SQL Server 2008 R2 Native Client ou SQL Server 2012 Native Client doit être installé.  
  
3.  Les packs d’administration pour surveiller SQL Server PDW doivent être installés, importés et configurés. Utilisez les articles suivants pour obtenir des instructions pour effectuer ces tâches.  
  
    -   [Installer les Packs d’administration SCOM &#40;Analytique Platform System&#41;](install-the-scom-management-packs.md)  
  
    -   [Importer le Pack d’administration SCOM pour PDW &#40;Analytique Platform System&#41;](import-the-scom-management-pack-for-pdw.md) 
    
    -   [Configurer SCOM pour surveiller le système de plateforme d’Analytique &#40;Analytique Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md)
  
<!-- MISSING LINKS    -   [Import the SCOM Management Pack for HDInsight &#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-hdinsight.md)  -->  
   
  
## <a name="to-monitor-sql-server-pdw-with-scom"></a>Pour surveiller SQL Server PDW avec SCOM  
Après avoir configuré les Packs d’administration SCOM, cliquez sur le volet surveillance de SCOM et explorez pour **SQL Server Appliance** , puis **Microsoft SQL Server Parallel Data Warehouse**. Sous Microsoft SQL Server Parallel Data Warehouse, il existe quatre options : Alertes, appareils, diagramme de l’Appliance et nœuds.  
  
### <a name="alerts"></a>Alertes  
Les alertes sont où vous pouvez trouver les alertes actives à gérer.  
  
![Alerts](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM.png "SCOM_SCOM")  
  
### <a name="appliances"></a>Appliances  
Les appliances sont où vous trouverez les Appliances actuellement détectés et analysés SQL Server PDW dans votre environnement. Si un appareil ne s’affiche pas ici et que vous avez créé la connexion ODBC pour celle-ci, puis il peut être un problème avec votre compte PDWWatcher. Si elles s’affichent comme « Non analysé », peut-être un problème avec votre compte PDWMonitor. Soyez patient depuis SCOM n’apporte pas de changements en temps réel, mais vérifie régulièrement les nouvelles appliances à surveiller et envoie régulièrement des requêtes pour les appareils pour la surveillance.  
  
![Appliances](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM2.png "SCOM_SCOM2")  
  
### <a name="appliances-diagram"></a>Diagramme des appliances  
La Page du diagramme Appliances est où vous pouvez obtenir un coup de œil à l’intégrité de votre appliance dotée d’une arborescence :  
  
![Diagramme des appliances](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM3.png "SCOM_SCOM3")  
  
### <a name="nodes"></a>Nodes  
Enfin, l’affichage de nœuds vous permet de voir l’intégrité de votre appliance via chaque nœud :  
  
![Nodes](./media/monitor-the-appliance-by-using-system-center-operations-manager/SCOM_SCOM4.png "SCOM_SCOM4")  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Alertes de la Console d’administration de présentation &#40;Analytique Platform System&#41;](understanding-admin-console-alerts.md)  
  
