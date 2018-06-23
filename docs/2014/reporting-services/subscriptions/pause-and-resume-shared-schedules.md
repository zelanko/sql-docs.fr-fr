---
title: Suspendre et reprendre des planifications partagées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pausing schedules
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services], resuming
- resuming schedules
- continuing schedules
- schedules [Reporting Services], resuming
- schedules [Reporting Services], pausing
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 68971d1dfd25f7e2e15be0007e1aaf5efb19099f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041029"
---
# <a name="pause-and-resume-shared-schedules"></a>Pause and Resume Shared Schedules
  Vous pouvez suspendre et reprendre une planification partagée en cours d'utilisation. Le fait de suspendre une planification partagée fournit un moyen de geler temporairement une planification qui est utilisée pour déclencher un traitement de rapport et des abonnements. Seules les planifications partagées peuvent être suspendues et reprises. Vous ne pouvez pas suspendre des planifications spécifiques aux rapports.  
  
 Vous ne pouvez pas suspendre et reprendre un traitement de rapport en cours. Vous ne pouvez suspendre et reprendre que les planifications faisant partie de la file d'attente des planifications du service Agent SQL Server. Un travail en cours ne fait pas partie du champ d'intervention du moteur de planification. Pour plus d’informations, consultez [gérer un processus en cours d’exécution](manage-a-running-process.md)  
  
 Pendant qu'une planification partagée est suspendue, toutes les opérations censées s'exécuter sont temporairement autorisées à ne pas avoir lieu. Lorsque vous reprenez une planification partagée, le traitement du rapport et de la planification se produit à l'heure planifiée suivante, en fonction de l'heure locale du serveur. Le serveur de rapports en mode natif ou les applications de service SharePoint n'effectuent pas les opérations planifiées qui étaient censées s'exécuter si la planification n'avait pas été suspendue.  
  
 Dans cette rubrique :  
  
-   [Suspendre et reprendre des planifications partagées (mode natif)](#bkmk_native)  
  
-   [Suspendre et reprendre des planifications partagées (mode SharePoint)](#bkmk_sharepoint)  
  
##  <a name="bkmk_native"></a> Suspendre et reprendre des planifications partagées (mode natif)  
 Pour suspendre et reprendre une planification partagée, utilisez la page Planifications du Gestionnaire de rapports. Vous ne pouvez pas utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]; ce dernier n'a pas les options nécessaires pour vous permettre de suspendre et de reprendre des planifications. Pour plus d’informations, consultez [créer, modifier et supprimer des planifications](create-modify-and-delete-schedules.md).  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a>Pour suspendre ou reprendre une planification partagée  
  
1.  Dans le Gestionnaire de rapports, cliquez sur **Paramètres du site**.  
  
2.  Cliquez sur **Planifications**.  
  
3.  Sélectionnez la planification, puis cliquez sur **Suspendre** ou **Reprendre** dans le Ruban. Si une planification est actuellement suspendue, la colonne **État** contient **Suspendu**.  
  
##  <a name="bkmk_sharepoint"></a> Suspendre et reprendre des planifications partagées (mode SharePoint)  
 Pour suspendre et reprendre une planification partagée, utilisez la page Paramètres du site ou PowerShell. Les planifications sont gérées en fonction de chaque site SharePoint.  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a>Pour suspendre ou reprendre une planification partagée  
  
1.  Cliquez sur **Actions du site**.  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Dans la section Reporting Services, cliquez sur **Gérer les planifications partagées**.  
  
4.  Sélectionnez la planification, puis cliquez sur **Suspendre les planifications sélectionnées** ou sur **Exécuter les planifications sélectionnées**. Si une planification est actuellement suspendue, la colonne **État** contient **Suspendu**.  
  
## <a name="see-also"></a>Voir aussi  
 [Planifications](schedules.md)   
 [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md)   
 [Modifier les fuseaux horaires et les paramètres d’horloge sur un serveur de rapports](change-time-zones-and-clock-settings-on-a-report-server.md)   
 [Gérer un processus en cours d'exécution](manage-a-running-process.md)  
  
  