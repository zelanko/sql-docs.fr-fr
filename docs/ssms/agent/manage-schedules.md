---
description: Gérer les planifications
title: Gérer les planifications
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016
ms.openlocfilehash: 8fe612c119493fb87229819a001c7058389a0e62
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482253"
---
# <a name="manage-schedules"></a>Gérer les planifications
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Managed Instance et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Permet de visualiser et de changer les propriétés des planifications de travaux du service [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Planifications disponibles**  
Répertorie les planifications disponibles pour cet utilisateur. Il faut noter qu'un travail et une planification doivent avoir le même propriétaire. Cette liste ne répertorie donc que les planifications appartenant au propriétaire du travail.  
  
**Nom**  
Affiche le nom de la planification.  
  
**Enabled**  
Sélectionnez cette option pour activer la planification.  
  
**Description**  
Décrit les conditions dans lesquelles la planification déclenche l'exécution du travail.  
  
**Travaux planifiés**  
Répertorie les numéros des travaux associés à la planification. Cliquez sur un numéro pour afficher les propriétés du travail correspondant.  
  
**Nouveau**  
Cliquez sur ce bouton pour créer une nouvelle planification.  
  
**Supprimer**  
Cliquez sur ce bouton pour supprimer la planification sélectionnée.  
  
**Propriétés**  
Cliquez sur ce bouton pour modifier les propriétés de la planification sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
[Créer des planifications et les attacher à des travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
