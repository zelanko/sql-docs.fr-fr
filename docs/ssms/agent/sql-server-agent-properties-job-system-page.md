---
description: Propriétés de l'Agent SQL Server (page Système de travaux)
title: Propriétés de l'Agent SQL Server (page Système de travaux)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 0805e5f6aae09a76e08c21ec30e3dec3e5bb47ed
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97474340"
---
# <a name="sql-server-agent-properties-job-system-page"></a>Propriétés de l'Agent SQL Server (page Système de travaux)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour afficher et modifier la façon dont le service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent gère les travaux.  
  
## <a name="options"></a>Options  
**Intervalle du délai d'arrêt (secondes)**  
Spécifie le nombre de secondes que l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attend pour considérer que les travaux sont terminés et pour forcer l'arrêt. Si le travail est toujours en cours d'exécution après l'intervalle spécifié, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] force l'arrêt du travail.  
  
**Utiliser un compte proxy non-administrateur**  
Définit un compte proxy non-administrateur pour l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] et les versions ultérieures prennent en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Nom d’utilisateur**  
Entrez le nom de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Mot de passe**  
Entrez le mot de passe de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures prennent en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
**Domaine**  
Entrez le domaine de l'utilisateur du compte proxy non-administrateur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge plusieurs serveurs proxy, c'est pourquoi cette option est applicable uniquement à la gestion des versions de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui précèdent [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
