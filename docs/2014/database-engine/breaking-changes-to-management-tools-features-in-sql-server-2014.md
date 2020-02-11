---
title: Modifications importantes apportées aux fonctionnalités des outils d’administration de SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 73e2c6ecb4ae2f829c02897ed5c6ab5d84f1ba4b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62787012"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a>Dernières modifications apportées aux fonctionnalités des outils d'administration dans SQL Server 2014
  Cette rubrique décrit les dernières modifications apportées aux fonctionnalités des outils d'administration. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il se peut que vous rencontriez ces problèmes lors d'une mise à niveau. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-includesssql14includessssql14-mdmd"></a>Modifications avec rupture dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informations qui seront fournies par la suite.  
  
## <a name="breaking-changes-in-includesssql11includessssql11-mdmd"></a>Modifications avec rupture dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="you-cannot-use-includesssql11includessssql11-mdmd-management-tools-to-create-a-utility-control-point-on-a-includesskilimanjaroincludessskilimanjaro-mdmd-instance-of-sql-server"></a>Vous ne pouvez pas utiliser les outils de gestion de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] pour créer un point de contrôle de l'utilitaire sur une instance de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] de SQL Server  
 Pour créer un point de contrôle de l'utilitaire sur une instance de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], utilisez les outils de gestion de [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] .  
  
### <a name="smo-has-been-reversioned-in-includesssql11includessssql11-mdmd"></a>SMO a changé de version dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Le code développé avec SMO depuis [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ou les versions antérieures peut ne pas convenir sur [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] à mois d'y apporter des changements mineurs. Pour plus d’informations, consultez [Compatibilité descendante dans SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).  

## <a name="previous-versions"></a>Modifications avec rupture dans SQL Server 2005  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante](../../2014/getting-started/backward-compatibility.md)  
 [En savoir plus sur les modifications importantes apportées aux fonctionnalités des outils d’administration de SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
