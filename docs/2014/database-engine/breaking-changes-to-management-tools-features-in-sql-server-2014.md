---
title: Modifications avec rupture à la gestion des fonctionnalités des outils dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f206da123659c750f955d2132142dcae76df6a46
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165350"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a>Dernières modifications apportées aux fonctionnalités des outils d'administration dans SQL Server 2014
  Cette rubrique décrit les dernières modifications apportées aux fonctionnalités des outils d'administration. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il se peut que vous rencontriez ces problèmes lors d'une mise à niveau. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-includesssql14includessssql14-mdmd"></a>Changements essentiels apportés à [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informations qui seront fournies par la suite.  
  
## <a name="breaking-changes-in-includesssql11includessssql11-mdmd"></a>Changements essentiels apportés à [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="you-cannot-use-includesssql11includessssql11-mdmd-management-tools-to-create-a-utility-control-point-on-a-includesskilimanjaroincludessskilimanjaro-mdmd-instance-of-sql-server"></a>Vous ne pouvez pas utiliser les outils de gestion de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] pour créer un point de contrôle de l'utilitaire sur une instance de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] de SQL Server  
 Pour créer un point de contrôle de l'utilitaire sur une instance de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], utilisez les outils de gestion de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
  
### <a name="smo-has-been-reversioned-in-includesssql11includessssql11-mdmd"></a>SMO a changé de version dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Le code développé avec SMO depuis [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ou les versions antérieures peut ne pas convenir sur [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] à mois d'y apporter des changements mineurs. Pour plus d’informations, consultez [Compatibilité descendante dans SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante](../../2014/getting-started/backward-compatibility.md)  
  
  
