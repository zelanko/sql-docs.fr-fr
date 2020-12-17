---
description: Utiliser des objets de performance
title: Utiliser des objets de performance
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
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
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: f6b7aa5d5028dabe94e9112ca935afc3e5199fd6
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97476960"
---
# <a name="use-performance-objects"></a>Utiliser des objets de performance
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent comprend des compteurs et des objets de performance qui permettent de surveiller le fonctionnement du service. Ces objets de performance vous permettent d'utiliser un outil Windows, en l'occurrence l'Analyseur de performances, pour identifier la tâche réalisée en arrière-plan par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Par exemple, vous pouvez identifier le nombre de travaux actifs en cours d'exécution par le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent afin de déterminer ceux qui sont bloqués.  
  
Les compteurs et les objets de performance du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sont disponibles pour chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installée sur un ordinateur. Un objet de performance est nommé en fonction de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qu'il représente.  
  
Le tableau suivant décrit la dénomination des objets de performance du service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent :  
  
|Type d’instance|Nom d’objet|  
|-----------------|---------------|  
|Par défaut|**SQLAgent:**_objet_:_compteur_|  
|named|**SQLAgent$**<br /> **&#42;nom_instance&#42; :**_objet_:_compteur_|  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comprend les objets de performance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent suivants.  
  
|Nom d’objet|Description|  
|---------------|---------------|  
|[SQLAgent:Jobs](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Informations de performance relatives aux travaux démarrés, aux taux de réussite et à l'état actuel|  
|[SQLAgent:JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Informations d'état relatives aux étapes de travail|  
|[SQLAgent:Alerts](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Informations relatives au nombre d'alertes et de notifications|  
|[SQLAgent:Statistics](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Informations générales sur les performances|  
  
## <a name="see-also"></a>Voir aussi  
[Surveillance et réglage des performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
[Procédure : démarrer le Moniteur système (Windows)](../../relational-databases/performance/start-system-monitor-windows.md)  
