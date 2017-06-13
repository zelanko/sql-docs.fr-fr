---
title: "Propriétés de Reporting Services | Documents Microsoft"
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
applies_to:
- SQL Server 2016 Preview
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
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3a81e521f0e17404ddfc0ed6d36950d8611ba666
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="reporting-services-properties"></a>Propriétés de Reporting Services
  Le serveur de rapports définit un jeu de propriétés système qui sont communes au serveur de rapports et un jeu de propriétés des éléments associées à un élément individuel stocké dans la base de données du serveur de rapports. Les propriétés définies par le serveur de rapports ne peuvent pas être supprimées, et sont dans certains cas en lecture seule. Une application peut étendre des propriétés système et des propriétés des éléments en ajoutant aux propriétés système et des éléments d'autres propriétés définies par l'utilisateur.  
  
 Les méthodes de service Web suivantes récupérer et définir [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] propriétés.  
  
|Méthode|Action|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Retourne les valeurs d'une ou plusieurs propriétés sur un élément dans la base de données du serveur de rapports.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Retourne une ou plusieurs propriétés système.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Définit une ou plusieurs propriétés d'un élément dans la base de données du serveur de rapports.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Définit une ou plusieurs propriétés système.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Propriétés d’élément de serveur de rapports](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-item-properties.md)|Décrit les propriétés spécifiques à l'élément dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Propriétés système de Report Server](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)|Décrit les propriétés spécifiques au système dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
