---
title: "La base de donn&#233;es secondaire n&#39;est pas attach&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.drp2joined.issues.f1"
helpviewer_keywords: 
  - "groupes de disponibilité [SQL Server], stratégies"
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
caps.latest.revision: 14
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 14
---
# La base de donn&#233;es secondaire n&#39;est pas attach&#233;e
    
## Introduction  
  
|||  
|-|-|  
|**Nom de la stratégie**|État de la jointure de la base de données de disponibilité|  
|**Problème**|La base de données secondaire n'est pas jointe.|  
|**Catégorie**|**Avertissement**|  
|**Facette**|Base de données de disponibilité|  
  
## Description  
 Cette stratégie vérifie l'état de jointure de la base de données secondaire (également appelée « réplica de base de données secondaire »). La stratégie se trouve dans un état non sain lorsque le réplica de dataset n'est pas joint. Autrement, l'état de la stratégie est sain.  
  
> [!NOTE]  
>  Pour cette version de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], les informations sur les causes et les solutions possibles sont situées sous [La base de données secondaire n’est pas jointe](http://go.microsoft.com/fwlink/p/?LinkId=220862) sur le Wiki TechNet.  
  
## Causes possibles  
 Cette base de données secondaire n'est pas jointe au groupe de disponibilité. La configuration de cette base de données secondaire est incomplète.  
  
## Solution possible  
 Utilisez Transact-SQL, PowerShell ou SQL Server Management Studio pour joindre le réplica secondaire au groupe de disponibilité. Pour plus d’informations sur la jointure des réplicas secondaires aux groupes de disponibilité, consultez [Jointure d’un réplica secondaire à un groupe de disponibilité (SQL Server)](http://msdn.microsoft.com/library/ff878473\(SQL.110\).aspx).  
  
## Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Utiliser le tableau de bord Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  