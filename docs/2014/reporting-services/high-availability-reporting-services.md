---
title: Haute disponibilité (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], Reporting Services
- high availability [Reporting Services]
- Reporting Services, high availability
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8bc05f1f669597229a3a07d6ce8487eb19a77201
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63261154"
---
# <a name="high-availability-reporting-services"></a>Haute disponibilité (Reporting Services)
  Un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est un serveur sans état qui stocke des données d'application, du contenu, des propriétés et des informations de session dans deux bases de données relationnelles [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Par conséquent, la meilleure façon de garantir la disponibilité des fonctionnalités [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est d'effectuer les opérations suivantes :  
  
-   Utilisez les fonctionnalités de haute disponibilité du moteur de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] pour optimiser le temps de fonctionnement des bases de données du serveur de rapports. Si vous configurez une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)] afin qu'elle s'exécute dans un cluster de basculement, vous pouvez sélectionner cette instance lorsque vous créez une base de données du serveur de rapports.  
  
-   Utilisez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)] avec les bases de données [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et pour les sources de données, si possible. Pour plus d’informations, consultez [Reporting Services avec les groupes de disponibilité Always On &#40;SQL Server&#41;](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).  
  
-   Configurez plusieurs serveurs de rapports afin qu'ils s'exécutent dans un déploiement avec montée en puissance parallèle, où tous les serveurs partagent une seule base de données du serveur de rapports. Le déploiement de plusieurs instances de serveur de rapports, de préférence sur des serveurs distincts, dans un déploiement avec montée en puissance parallèle, peut contribuer à fournir un service ininterrompu en cas de panne de l'une des instances de serveur de rapports.  
  
 Un déploiement avec montée en puissance parallèle permet de partager une base de données. Si un serveur de rapports tombe en panne, les autres serveurs du même déploiement continuent de fonctionner.  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n’est pas sensible aux clusters. Un déploiement avec montée en puissance parallèle ne fournit pas d'équilibrage de charge ; il ne détecte pas les charges de traitement d'un serveur de rapports et n'achemine pas les nouvelles requêtes de traitement au serveur le moins occupé. Il ne réachemine pas les requêtes de traitement ayant échoué avant de se terminer. Si vous voulez obtenir des fonctionnalités d'équilibrage de charge, vous devez configurer l'équilibrage de charge pour les serveurs Web qui hébergent les serveurs de rapports ; vous devez ensuite configurer les serveurs de rapports dans un déploiement avec montée en puissance parallèle afin qu'ils partagent la même base de données du serveur de rapports.  
  
 Le service Web Report Server et le service Windows sont étroitement intégrés et s'exécutent en tant qu'instance de serveur de rapports unique. Vous ne pouvez pas configurer la disponibilité de ces deux services de manière séparée.  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions haute disponibilité &#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  
