---
description: Choisir une planification pour le travail
title: Choisir une planification pour le travail
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.pickscheduleforjob.f1
helpviewer_keywords:
- Pick Schedule for Job dialog box
ms.assetid: 6de2025d-c25c-47b9-9a25-18c294935c15
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c095370f69aaa1e9f06cfc3e57500c09442c728a
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92030798"
---
# <a name="pick-schedule-for-job"></a>Choisir une planification pour le travail
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance), la plupart, mais pas toutes les fonctionnalités SQL Server Agent sont actuellement prises en charge. Pour plus d’informations, consultez [Instancefferences Azure SQL Managed et SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette boîte de dialogue vous permet de choisir une planification existante pour le travail de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Options  
**Planifications disponibles**  
Répertorie les planifications disponibles pour ce travail. Comme un travail et une planification doivent avoir le même propriétaire, cette liste inclut uniquement les planifications possédées par le propriétaire du travail.  
  
**Nom**  
Affiche le nom de la planification.  
  
**Enabled**  
Option sélectionnée si la planification est activée.  
  
**Description**  
Décrit les conditions dans lesquelles la planification déclenche l'exécution du travail.  
  
**Travaux planifiés**  
Répertorie les numéros des travaux associés à la planification. Cliquez sur un numéro pour afficher les propriétés du travail correspondant.  
  
**Propriétés**  
Affiche la boîte de dialogue **Propriétés de la planification du travail** qui inclut des informations sur la planification.  
  
## <a name="see-also"></a>Voir aussi  
[Créer des planifications et les attacher à des travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
