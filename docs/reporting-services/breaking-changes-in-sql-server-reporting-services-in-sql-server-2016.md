---
title: Modifications avec rupture dans SQL Server Reporting Services dans SQL Server 2016 | Documents Microsoft
ms.date: 03/15/2017
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
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 36ec7d7f1aa78e08f7fa4b63e8ca6525afe1c215
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016"></a>Modifications importantes de SQL Server Reporting Services dans SQL Server 2016
  Cette rubrique décrit les changements importants apportés à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous pouvez rencontrer ces problèmes lorsque vous effectuez une mise à niveau, ou dans les scripts ou les rapports personnalisés.  
  
  ## <a name="security-extensions"></a>Extensions de sécurité
  
  Les extensions de sécurité personnalisées doivent être modifiées pour fonctionner avec le nouveau [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Les extensions de sécurité doivent utiliser l’interface IAuthenticationExtension2.
  
  ## <a name="wmi-provider"></a>Fournisseur WMI
  
  Le nom de l’application [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] n’est plus « ReportManager », mais « ReportServerWebApp ».
  
## <a name="see-also"></a>Voir aussi 

[Changements de comportement SQL Server Reporting Services dans SQL Server 2016](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)

[Quelles sont les nouveautés de Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)
 
[Fonctions déconseillées de SQL Server Reporting Services dans SQL Server 2016](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)
  
[Fonctionnalités supprimées de SQL Server Reporting Services dans SQL Server 2016](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)



