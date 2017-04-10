---
title: "Modifications importantes de SQL Server Reporting Services dans SQL Server 2016 | Microsoft Docs"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Me.Value references"
  - "Reporting Services, backward compatibility"
  - "modifications importantes [Reporting Services]"
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 116
---
# Modifications importantes de SQL Server Reporting Services dans SQL Server 2016
  Cette rubrique décrit les changements importants apportés à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous pouvez rencontrer ces problèmes lorsque vous effectuez une mise à niveau, ou dans les scripts ou les rapports personnalisés.  
  
  ## Extensions de sécurité
  
  Les extensions de sécurité personnalisées doivent être modifiées pour fonctionner avec le nouveau [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Les extensions de sécurité doivent utiliser l’interface IAuthenticationExtension2.
  
  ## Fournisseur WMI
  
  Le nom de l’application [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] n’est plus « ReportManager », mais « ReportServerWebApp ».
  
## Voir aussi  
 [Changements de comportement apportés à SQL Server Reporting Services dans SQL Server 2016](http://msdn.microsoft.com/fr-fr/2a767f0f-84f2-4099-8784-1e37790f858e)   
 [Nouveautés de Reporting Services &#40;SSRS&#41;](../Topic/What's%20New%20in%20Reporting%20Services%20\(SSRS\).md)   
 [Fonctions déconseillées de SQL Server Reporting Services dans SQL Server 2016](http://msdn.microsoft.com/fr-fr/3876c01e-f81d-4cce-9104-5106a8c369e6)   
 [Fonctionnalités supprimées de SQL Server Reporting Services dans SQL Server 2016](http://msdn.microsoft.com/fr-fr/d529cc96-3483-480b-9bfc-bd28b1d0ef52)  
  
  