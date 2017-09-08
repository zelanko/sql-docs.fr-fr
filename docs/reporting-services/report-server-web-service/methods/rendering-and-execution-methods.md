---
title: "Méthodes d’exécution et le rendu | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 78435f88c76c3c98f4d1736af47492f3173ed91d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="rendering-and-execution-methods"></a>Méthodes de rendu et d'exécution
  Vous pouvez utiliser ces méthodes pour gérer l'exécution et la mise en cache des éléments, ainsi que la génération des rapports.  
  
|Méthode|Action|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|Invalide le cache pour un élément.|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|Retourne la configuration de mise en cache pour un élément et les paramètres qui décrivent à quel moment la copie de l'élément mise en cache arrive à expiration.|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|Retourne l'option d'exécution et les paramètres associés pour un élément individuel.|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|Retourne une liste de paramètres d'exécution pris en charge.|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|Traite le rapport spécifié et effectue le rendu du rapport dans un format spécifié.|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|Configure la mise en cache d'un élément et fournit des paramètres qui spécifient à quel moment la copie de l'élément mise en cache arrive à expiration.|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|Définit des options et des propriétés d'exécution associées pour un élément spécifié.|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|Génère un instantané de l'exécution de l'élément pour un élément spécifié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service Web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Méthodes de Service Web Report Server](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Informations techniques de référence &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
