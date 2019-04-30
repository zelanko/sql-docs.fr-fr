---
title: Page mise en cache, Datasets partagés (rapport Gestionnaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: eac372e9-d2a1-48a8-bbe5-09d101df16ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6b816af806e419cab0f6eb0997c6ec7f08bc7b93
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63266335"
---
# <a name="caching-page-shared-datasets-report-manager"></a>Page Mise en cache, datasets partagés (Gestionnaire de rapports)
  Utilisez la page de propriétés de mise en cache pour définir les options de mise en cache d'un dataset partagé.  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour accéder à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-caching-properties-page-for-a-shared-dataset"></a>Pour ouvrir la page des propriétés de mise en cache d'un dataset partagé  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez configurer les propriétés de dataset partagé.  
  
2.  Pointez sur le dataset partagé, puis cliquez sur la flèche déroulante.  
  
3.  Dans la liste déroulante, cliquez sur **Gérer**. La page de propriétés générales du rapport s'ouvre.  
  
4.  Cliquez sur l'onglet **Mise en cache** .  
  
## <a name="options"></a>Options  
 **Jeu de données de cache partagé**  
 Place une copie temporaire des données dans un cache lorsqu'un utilisateur ouvre pour la première fois un rapport qui utilise ce dataset partagé. Les utilisateurs suivants qui exécutent le rapport dans la période de mise en cache reçoivent la copie mise en cache des données. La mise en cache améliore habituellement les performances, car les données sont retournées à partir du cache ; la requête de dataset n'est pas réexécutée.  
  
 **Faire expirer le cache après un certain nombre de minutes**  
 Spécifie la durée, en minutes, pendant laquelle la copie mise en cache des données est enregistrée. Dès qu'une copie temporaire expire, les données ne sont plus retournées à partir du cache. Lors de l'ouverture suivante d'un rapport utilisant ce dataset partagé par un utilisateur, la requête de dataset s'exécute et le serveur de rapports réinsère une copie des données actualisées dans le cache.  
  
 **Faire expirer le cache selon la planification suivante**  
 Planifie l'heure à laquelle les données mises en cache ne sont plus valides et sont supprimées du cache. Il peut s'agir d'une planification partagée ou d'une planification s'appliquant exclusivement au dataset partagé actuel.  
  
 **Planification spécifique aux DataSets**  
 Spécifie une planification qui est utilisée uniquement par ce dataset.  
  
 **Planification partagée**  
 Spécifie une planification qui est partagée par des rapports, des abonnements et d'autres datasets partagés.  
  
 **Appliquer**  
 Enregistrez vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Mettre en cache les datasets partagés &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md)   
 [Planifications](subscriptions/schedules.md)  
  
  
