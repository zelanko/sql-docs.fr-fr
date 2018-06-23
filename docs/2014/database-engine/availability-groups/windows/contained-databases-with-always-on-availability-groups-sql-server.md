---
title: Bases de données autonomes avec les groupes de disponibilité Always On (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- contained database [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 8
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 2fcb71ddb5bef8f4b93c900f4e2f536dea820381
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144367"
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>Bases de données autonomes avec les groupes de disponibilité Always On (SQL Server)
  Cette rubrique contient des informations sur l'utilisation d'une base de données autonome avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Dans cette rubrique :**  
  
-   [Conditions préalables](#Prerequisites)  
  
-   [Tâches associées](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> Conditions préalables  
  
-   Avant d'ajouter une base de données autonome à un groupe de disponibilité, vérifiez que l'option de serveur `contained database authentication` est définie sur `1` sur chaque instance de serveur qui héberge un réplica de disponibilité pour le groupe de disponibilité. Pour plus d'informations, consultez [Authentification de la base de données autonome (option de configuration de serveur)](../../configure-windows/contained-database-authentication-server-configuration-option.md) et [Server Configuration Options &amp;#40;SQL Server&amp;#41;](../../configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Options de configuration de serveur &#40;SQL Server&#41;](../../configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 
  [Bases de données autonomes](../../../relational-databases/databases/contained-databases.md)  
  
  