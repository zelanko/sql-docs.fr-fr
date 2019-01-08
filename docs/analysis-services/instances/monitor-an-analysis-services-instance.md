---
title: Surveiller une vue d’ensemble de l’Instance Analysis Services | Microsoft Docs
ms.date: 11/16/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ac0f94b7f12cdba6237b2694114580f56dc6597
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52540457"
---
# <a name="monitoring-overview"></a>Vue d'ensemble de la surveillance
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Analysis Services dispose de plusieurs outils pour vous aider à surveiller et et régler les performances de vos serveurs. Le choix de l'outil dépend du type de surveillance ou de paramétrage à effectuer et des événements spécifiques à contrôler.

Pour plus d’informations sur la surveillance de SQL Server Analysis Services, consultez le [Guide des opérations SQL Server 2008 R2](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
## <a name="monitoring-tools"></a>Outils de supervision  

|Tool  |Description  |
|---------|---------|
|[SQL Server Profiler](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)      |   Effectue le suivi des événements de processus du moteur. Il capture également les données relatives à ces événements, ce qui vous permet de surveiller l’activité du serveur et base de données.      |
| [Événements étendus](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)     |   Un léger de traçage et la surveillance des performances système qui utilise très peu de ressources système et un outil idéal pour diagnostiquer les problèmes sur les serveurs de production et de test.       |
| [Vues de gestion dynamique &#40;DMV&#41;](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)      |   Requêtes qui retournent des informations sur les objets de modèle, les opérations de serveur et l’intégrité du serveur. La requête, basée sur SQL, est une interface pour les ensembles de lignes de schéma.      |
| [Événements de trace](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)     |  Suivez l’activité d’une instance en capturant, puis en analysant les événements de trace générés par l’instance. Les événements de trace sont regroupés afin que vous puissiez plus facilement rechercher des événements de trace connexes.        |
|   [Compteurs de performances](../../analysis-services/instances/performance-counters-ssas.md)\*    |    L'Analyseur de performances vous permet d'analyser les performances d'une instance Microsoft SQL Server Analysis Services (SSAS) à l'aide de compteurs de performance.     |
|[Opérations du journal](../../analysis-services/instances/performance-counters-ssas.md)\*|Une instance de SQL Server Analysis Services enregistrera les notifications du serveur, les erreurs et avertissements dans le fichier msmdsrv.log - un pour chaque instance que vous installez. |

\* S’applique à SQL Server Analysis Services uniquement.

## <a name="see-also"></a>Voir aussi

[Surveiller les métriques de serveur Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-monitor)   
[Configurer la journalisation de diagnostique pour Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-logging)
