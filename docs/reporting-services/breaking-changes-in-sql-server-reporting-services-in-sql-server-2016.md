---
title: "Changements essentiels apportés à SQL Server Reporting Services dans SQL Server 2016 | Microsoft Docs"
ms.date: 07/02/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: "121"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 0f36c68a5f5f83162f3daf31712b9eb19d3ec273
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016"></a>Modifications importantes de SQL Server Reporting Services dans SQL Server 2016

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)])

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

Cette rubrique décrit les changements importants apportés à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous pouvez rencontrer ces problèmes lorsque vous effectuez une mise à niveau, ou dans les scripts ou les rapports personnalisés.

## <a name="security-extensions"></a>Extensions de sécurité

Les extensions de sécurité personnalisées doivent être modifiées pour fonctionner avec le nouveau [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Les extensions de sécurité doivent utiliser l’interface IAuthenticationExtension2.

## <a name="wmi-provider"></a>Fournisseur WMI

Le nom de l’application [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] n’est plus « ReportManager », mais « ReportServerWebApp ».

## <a name="next-steps"></a>Étapes suivantes

[Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2016](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)  
[Nouveautés de Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)   
[Fonctions dépréciées de SQL Server Reporting Services dans SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)    
[Fonctionnalités supprimées de SQL Server Reporting Services dans SQL Server 2016](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
