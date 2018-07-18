---
title: Performances, instantanés, mise en cache (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: 85afd00f-e8d7-4ef7-9174-2ff84d82f960
caps.latest.revision: 19
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5ceab28c15a3e0a5e8851fd4d7142a7d0c0b2f18
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236159"
---
# <a name="performance-snapshots-caching-reporting-services"></a>Performances, instantanés, mise en cache (Reporting Services)
  Les performances du serveur de rapports sont affectées par une combinaison de facteurs qui incluent le matériel, le nombre d'utilisateurs simultanés qui accèdent aux rapports, la quantité de données d'un rapport et le format de sortie. Pour déterminer quels sont les facteurs de performances spécifiques à votre installation et quelles sont les solutions qui produiront les résultats escomptés, vous devez obtenir des données de référence et effectuer des tests. Pour plus d'informations sur les outils et instructions disponibles, consultez les publications suivantes sur MSDN : [Optimisation des performances de Reporting Services](http://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) et [Utilisation de Visual Studio 2005 pour effectuer un test de charge sur un serveur de rapports SQL Server 2005 Reporting Services](http://go.microsoft.com/fwlink/?LinkID=77519)(en anglais).  
  
 Les principes généraux à prendre en considération sont les suivants :  
  
-   Le traitement et le rendu des rapports sont des opérations qui nécessitent beaucoup de mémoire. Si possible, choisissez un ordinateur disposant d'une grande quantité de mémoire.  
  
-   L'hébergement du serveur de rapports et de la base de données du serveur de rapports sur des ordinateurs distincts a tendance à offrir de meilleures performances qu'un hébergement sur un seul ordinateur haut de gamme.  
  
-   Si le traitement de l'ensemble des rapports est lent, songez à effectuer un déploiement avec montée en puissance parallèle, où plusieurs instances de serveur de rapports prennent en charge une base de données du serveur de rapports unique. Pour obtenir les meilleurs résultats, utilisez un logiciel d'équilibrage de charge afin de répartir les requêtes de manière uniforme dans le déploiement.  
  
-   Si le traitement d'un rapport unique est lent, ajustez les requêtes de dataset du rapport si le rapport doit s'exécuter à la demande. Vous pouvez également envisager d'utiliser des datasets partagés que vous pouvez mettre en cache, de mettre en cache le rapport ou d'exécuter le rapport comme un instantané.  
  
-   Si le traitement de l'ensemble des rapports est lent dans un format spécifique (lors du rendu au format PDF, par exemple), songez à utiliser la remise par partage de fichiers, à ajouter davantage de mémoire ou à choisir un autre format.  
  
-   Pour déterminer le temps de traitement d'un rapport et pour connaître d'autres mesures relatives à l'utilisation, consultez le journal des exécutions du serveur de rapports. Pour plus d’informations, consultez [journal de l’exécution de serveur de rapports et vue ExecutionLog3](report-server-executionlog-and-the-executionlog3-view.md).  
  
-   Pour plus d’informations sur la façon d’atténuer les problèmes de performances en ajustant les paramètres de configuration de gestion de mémoire, consultez [configurer la mémoire disponible pour les Applications de serveur de rapports](../report-server/configure-available-memory-for-report-server-applications.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contrôle des performances d'un serveur de rapports](monitoring-report-server-performance.md)  
 Décrit les objets de performances dont vous pouvez vous servir pour assurer le suivi de la charge de traitement sur votre serveur.  
  
 [Définir les propriétés de traitement d'un rapport](set-report-processing-properties.md)  
 Décrit les différentes configurations d'un rapport pour qu'il s'exécute à la demande, à partir de la mémoire cache ou suivant une planification en tant qu'instantané de rapport.  
  
 [Configurer la mémoire disponible pour les applications du serveur de rapports](../report-server/configure-available-memory-for-report-server-applications.md)  
 Décrit comment remplacer le comportement par défaut de gestion de la mémoire.  
  
 [La mise en cache des rapports &#40;SSRS&#41;](caching-reports-ssrs.md)  
 Décrit le comportement de mise en cache d'un rapport sur un serveur de rapports.  
  
 [Cache des Datasets partagés &#40;SSRS&#41;](cache-shared-datasets-ssrs.md)  
 Décrit le comportement de mise en cache d'un dataset partagé sur un serveur de rapports.  
  
 [Traiter les rapports volumineux](process-large-reports.md)  
 Délivre des recommandations sur la façon de configurer et de distribuer un rapport de taille volumineuse.  
  
 [Définition des valeurs de délai d’attente pour traitement des rapports et jeu de données partagée &#40;SSRS&#41;](setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
 Explique comment définir des délais d'attente pour le traitement des requêtes et des rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer un processus en cours d’exécution](../subscriptions/manage-a-running-process.md)   
 [Vérification de l'exécution d'un rapport](verifying-a-report-run.md)  
  
  
