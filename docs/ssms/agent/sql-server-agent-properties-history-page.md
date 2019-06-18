---
title: Propriétés de SQL Server Agent (page Historique) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 30426daee4c801ae0e8e338a88020434acda602d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089626"
---
# <a name="sql-server-agent-properties-history-page"></a>Propriétés de l'Agent SQL Server (page Historique)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et modifier des paramètres de gestion du journal d'historique du service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Limiter la taille du journal d'historique des travaux.**  
Limite la quantité d'informations d'historique des travaux que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve dans le journal.  
  
**Taille maximale du journal d'historique des travaux (lignes)**  
Spécifie le nombre maximal de lignes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve. Lorsque le journal a atteint le nombre de lignes indiqué, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprime les lignes les plus anciennes à mesure que de nouvelles lignes sont insérées.  
  
**Nombre  maximal de lignes d'historique des travaux par travail**  
Spécifie le nombre maximal de lignes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve par travail. Lorsque l'historique d'un travail particulier a atteint le nombre de lignes indiqué, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supprime les lignes les plus anciennes à mesure que de nouvelles lignes sont insérées.  
  
**Supprimer l'historique de l'agent**  
Indique que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] va supprimer les entrées présentes dans le journal depuis plus longtemps que la période spécifiée. Il s'agit d'une exécution ponctuelle pour supprimer l'historique. Si vous préférez un travail récurrent, créez et planifiez un plan de maintenance avec un travail de nettoyage.  
  
**Antérieur à**  
Spécifie la période pendant laquelle l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve les entrées.  
  
## <a name="see-also"></a>Voir aussi  
[Journal des erreurs de l'Agent SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
