---
title: "Propriétés de Reporting Services | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
caps.latest.revision: "34"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 99ffd5970a7d1d3d973789b0fd67150e97d6bb42
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="reporting-services-properties"></a>Propriétés de Reporting Services
  Le serveur de rapports définit un jeu de propriétés système qui sont communes au serveur de rapports et un jeu de propriétés des éléments associées à un élément individuel stocké dans la base de données du serveur de rapports. Les propriétés définies par le serveur de rapports ne peuvent pas être supprimées, et sont dans certains cas en lecture seule. Une application peut étendre des propriétés système et des propriétés des éléments en ajoutant aux propriétés système et des éléments d'autres propriétés définies par l'utilisateur.  
  
 Les méthodes de service web suivantes récupèrent et définissent des propriétés [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
|Méthode|Action|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Retourne les valeurs d'une ou plusieurs propriétés sur un élément dans la base de données du serveur de rapports.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Retourne une ou plusieurs propriétés système.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Définit une ou plusieurs propriétés d'un élément dans la base de données du serveur de rapports.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Définit une ou plusieurs propriétés système.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Propriétés d’élément du serveur de rapports](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-item-properties.md)|Décrit les propriétés spécifiques à l'élément dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Propriétés système du serveur de rapports](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)|Décrit les propriétés spécifiques au système dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications à l’aide du service web et du .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
