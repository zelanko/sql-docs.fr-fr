---
title: Utiliser des bases de données autonomes avec les groupes de disponibilité
description: Découvrez comment utiliser des bases de données autonomes avec un groupe de disponibilité Always On
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: b93c4c91051284a944e3b234da3f4523b3092623
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66793550"
---
# <a name="use-contained-databases-with-always-on-availability-groups"></a>Utiliser des bases de données autonomes avec les groupes de disponibilité Always On 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette rubrique contient des informations sur l'utilisation d'une base de données autonome avec [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
##  <a name="Prerequisites"></a> Conditions préalables  
  
-   Avant d’ajouter une base de données autonome à un groupe de disponibilité, vérifiez que l’option de serveur **contained database authentication** a la valeur **1** sur chaque instance de serveur qui héberge un réplica de disponibilité pour le groupe de disponibilité. Pour plus d'informations, consultez [Authentification de la base de données autonome (option de configuration de serveur)](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) et [Server Configuration Options &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Options de configuration de serveur &#40;SQL Server&#41;](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Bases de données autonomes](../../../relational-databases/databases/contained-databases.md)  
  
  
