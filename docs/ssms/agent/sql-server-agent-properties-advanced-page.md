---
title: Propriétés de SQL Server Agent (page Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1165ae7e319e5e8cd9d0548d404c9b356e378b38
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089649"
---
# <a name="sql-server-agent-properties-advanced-page"></a>Propriétés de l'Agent SQL Server (page Avancé)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour consulter et modifier les propriétés avancées du service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Transfert d'événements SQL Server**  
Les options de cette catégorie permettent d'activer et de configurer le transfert d'événements.  
  
**Transférer les événements sur un autre serveur**  
Transfère les événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sur un autre serveur.  
  
**Server**  
Sélectionnez le nom du serveur sur lequel vous voulez transférer les événements.  
  
**Événements non gérés**  
Transfère uniquement les événements non gérés sur le serveur spécifié. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent transfère uniquement les événements auxquels aucune alerte ne répond.  
  
**Tous les événements**  
Transfère tous les événements. Si une alerte répond à l'événement dans l'instance locale, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent transfère l'événement et traite l'alerte.  
  
**Si l'événement a une gravité au moins égale à**  
Transfère uniquement les événements dont le niveau de gravité est supérieur ou égal au niveau spécifié.  
  
**Condition d'inactivité de l'UC**  
Les options de cette catégorie définissent les conditions dans lesquelles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent exécute les travaux dont l'exécution est planifiée pendant l'inactivité de l'UC.  
  
**Définir la condition d'inactivité de l'UC**  
Définit les conditions dans lesquelles [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent considère que l'UC est inactive.  
  
**La moyenne d'utilisation de l'UC tombe en dessous de**  
Pourcentage d'utilisation de l'UC au-dessous duquel l'UC est considérée comme inactive.  
  
**Et reste sous ce niveau pendant**  
Durée pendant laquelle la moyenne d'utilisation de l'UC doit rester au-dessous du niveau spécifié avant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent démarre l'exécution des travaux planifiés pendant l'inactivité de l'UC.  
  
## <a name="see-also"></a>Voir aussi  
[Créer des planifications et les attacher à des travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Gérer les événements](../../ssms/agent/manage-events.md)  
  
