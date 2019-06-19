---
title: Propriétés de SQL Server Agent (page Système de travaux) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a71dda192bebbe84876b2e4fbcb770f5967127c2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089611"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Propriétés de l'Agent SQL Server (page Système de travaux)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et modifier la façon dont le service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent gère les travaux.  
  
## <a name="options"></a>Options  
**Intervalle du délai d'arrêt (secondes)**  
Spécifie le nombre de secondes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attend pour considérer que les travaux sont terminés et pour forcer l'arrêt. Si le travail est toujours en cours d'exécution après l'intervalle spécifié, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] force l'arrêt du travail.  
  
**Utiliser un compte proxy non-administrateur**  
Définit un compte proxy non-administrateur pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] et les versions ultérieures prennent en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**User name**  
Entrez le nom de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Mot de passe**  
Entrez le mot de passe de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures prennent en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
**Domainee**  
Entrez le domaine de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
  
