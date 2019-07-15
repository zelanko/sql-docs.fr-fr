---
title: Utiliser des objets de performance | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 28a282e9f5f4061d94059986e70b4bf0755ceb5a
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67687646"
---
# <a name="use-performance-objects"></a>Utiliser des objets de performance
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent comprend des compteurs et des objets de performance qui permettent de surveiller le fonctionnement du service. Ces objets de performance vous permettent d'utiliser un outil Windows, en l'occurrence l'Analyseur de performances, pour identifier la tâche réalisée en arrière-plan par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Par exemple, vous pouvez identifier le nombre de travaux actifs en cours d'exécution par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent afin de déterminer ceux qui sont bloqués.  
  
Les compteurs et les objets de performance du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sont disponibles pour chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installée sur un ordinateur. Un objet de performance est nommé en fonction de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qu'il représente.  
  
Le tableau suivant décrit la dénomination des objets de performance du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent :  
  
|Type d’instance|Nom de l'objet|  
|-----------------|---------------|  
|Valeur par défaut|**SQLAgent:** _objet_:_compteur_|  
|Nommé|**SQLAgent$**<br /> **&#42;nom_instance&#42; :** _objet_:_compteur_|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comprend les objets de performance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent suivants.  
  
|Nom de l'objet|Description|  
|---------------|---------------|  
|[SQLAgent:Jobs](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Informations de performance relatives aux travaux démarrés, aux taux de réussite et à l'état actuel|  
|[SQLAgent:JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Informations d'état relatives aux étapes de travail|  
|[SQLAgent:Alerts](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Informations relatives au nombre d'alertes et de notifications|  
|[SQLAgent:Statistics](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Informations générales sur les performances|  
  
## <a name="see-also"></a>Voir aussi  
[Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
[Procédure : Démarrer le moniteur système (Windows)](https://msdn.microsoft.com/5e51bb79-5737-470b-9c47-fac330c001c5)  
  
