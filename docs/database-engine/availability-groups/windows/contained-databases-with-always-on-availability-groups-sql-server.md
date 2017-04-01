---
title: "Bases de donn&#233;es &#224; relation contenant-contenu avec les groupes de disponibilit&#233; Always On (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groupes de disponibilité [SQL Server], interopérabilité"
  - "base de données à relation contenant-contenu, AlwaysOnAvailabilityGroups"
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 9
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 9
---
# Bases de donn&#233;es &#224; relation contenant-contenu avec les groupes de disponibilit&#233; Always On (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique contient des informations sur l'utilisation d'une base de données à relation contenant-contenu avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Dans cette rubrique :**  
  
-   [Conditions préalables](#Prerequisites)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> Conditions préalables  
  
-   Avant d’ajouter une base de données à relation contenant-contenu à un groupe de disponibilité, vérifiez que l’option de serveur **contained database authentication** a la valeur **1** sur chaque instance de serveur qui héberge un réplica de disponibilité pour le groupe de disponibilité. Pour plus d'informations, consultez [Authentification de la base de données à relation contenant-contenu (option de configuration de serveur)](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) et [Options de configuration de serveur &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Options de configuration de serveur &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Bases de données à relation contenant-contenu](../../../relational-databases/databases/contained-databases.md)  
  
  