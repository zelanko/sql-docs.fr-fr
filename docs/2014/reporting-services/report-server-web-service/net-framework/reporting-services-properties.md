---
title: Propriétés de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
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
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61f1f50ea7a49acc616a36a4eaf1d3d5fcdf269a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63260917"
---
# <a name="reporting-services-properties"></a>Propriétés de Reporting Services
  Le serveur de rapports définit un jeu de propriétés système qui sont communes au serveur de rapports et un jeu de propriétés des éléments associées à un élément individuel stocké dans la base de données du serveur de rapports. Les propriétés définies par le serveur de rapports ne peuvent pas être supprimées, et sont dans certains cas en lecture seule. Une application peut étendre des propriétés système et des propriétés des éléments en ajoutant aux propriétés système et des éléments d'autres propriétés définies par l'utilisateur.  
  
 Les méthodes de service Web suivantes récupèrent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et définissent des propriétés.  
  
|Méthode|Action|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Retourne les valeurs d'une ou plusieurs propriétés sur un élément dans la base de données du serveur de rapports.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Retourne une ou plusieurs propriétés système.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Définit une ou plusieurs propriétés d'un élément dans la base de données du serveur de rapports.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Définit une ou plusieurs propriétés système.|  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Propriétés d'élément du serveur de rapports](reporting-services-properties-report-server-item-properties.md)|Décrit les propriétés spécifiques à l'élément dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Propriétés système de Report Server](reporting-services-properties-report-server-system-properties.md)|Décrit les propriétés spécifiques au système dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service web Report Server](../report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
