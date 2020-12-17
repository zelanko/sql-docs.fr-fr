---
description: Propriétés du travail - Nouveau travail (page Étapes)
title: Propriétés du travail - Nouveau travail (page Étapes)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.steps.f1
ms.assetid: 231fe13e-c2dc-4149-a73e-1497e62c49e8
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 5fd49af8bafd3a47fefa3a1b232eefcab3990108
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466500"
---
# <a name="job-properties---new-job-steps-page"></a>Propriétés du travail - Nouveau travail (page Étapes)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour consulter et organiser les étapes d’un travail de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Liste des étapes du travail**  
Répertorie les étapes de ce travail.  
  
**Déplacer l'étape**  
Déplace le travail d'une étape, vers le haut ou vers le bas, dans la liste.  
  
**Étape de démarrage**  
Sélectionnez l'étape que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent va effectuer en premier lorsque le travail commence.  
  
**Nouveau**  
Crée une nouvelle étape de travail au-dessous de l'étape de travail sélectionnée.  
  
**Insérer**  
Crée une nouvelle étape de travail au-dessus de l'étape de travail sélectionnée.  
  
**Modifier**  
Modifie l'étape de travail sélectionnée.  
  
**Supprimer**  
Supprime l'étape de travail sélectionnée. Lorsque des étapes de travail sont supprimées, leur journal de sortie est automatiquement supprimé.  
  
## <a name="see-also"></a>Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
