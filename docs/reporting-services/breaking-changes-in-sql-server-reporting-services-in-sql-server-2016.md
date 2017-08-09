---
title: Modifications avec rupture dans SQL Server Reporting Services dans SQL Server 2016 | Documents Microsoft
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 121
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 6348d05b8dbe6c8ab1a682388b4e69ce438e6a12
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---

# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016"></a>Modifications importantes de SQL Server Reporting Services dans SQL Server 2016

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

Cette rubrique décrit les changements importants apportés à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous pouvez rencontrer ces problèmes lorsque vous effectuez une mise à niveau, ou dans les scripts ou les rapports personnalisés.

## <a name="security-extensions"></a>Extensions de sécurité

Les extensions de sécurité personnalisées doivent être modifiées pour fonctionner avec le nouveau [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Les extensions de sécurité doivent utiliser l’interface IAuthenticationExtension2.

## <a name="wmi-provider"></a>Fournisseur WMI

Le nom de l’application [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] n’est plus « ReportManager », mais « ReportServerWebApp ».

## <a name="next-steps"></a>Étapes suivantes

[Changements de comportement SQL Server Reporting Services dans SQL Server 2016](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)  
[Quelles sont les nouveautés de Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)   
[Fonctionnalités déconseillées dans SQL Server Reporting Services dans SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)    
[Fonctionnalités supprimées de SQL Server Reporting Services dans SQL Server 2016](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
