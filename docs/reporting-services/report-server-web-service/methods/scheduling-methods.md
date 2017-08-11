---
title: "Méthodes de planification | Documents Microsoft"
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
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: b72d4a6fb29541232192775a9a25eed34884b211
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="scheduling-methods"></a>Méthodes de planification
  Vous pouvez utiliser ces méthodes pour créer et gérer des planifications partagées pour l'exécution et la remise de rapports, et pour mettre en cache des plans d'actualisation utilisés par le serveur de rapports.  
  
|Méthode|Action|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|Crée un plan d'actualisation du cache pour un élément.|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|Crée une planification partagée.|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|Supprime un plan d'actualisation du cache.|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|Supprime une planification partagée en fonction de son ID.|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|Retourne les propriétés du plan d'actualisation du cache spécifié.|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|Retourne les valeurs des propriétés d'une planification partagée.|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|Retourne une liste des plans d'actualisation du cache associés à un élément de catalogue.|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|Retourne une liste des éléments associés à une planification partagée.|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|Retourne une liste de toutes les planifications partagées du serveur de rapports ou du site SharePoint.|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|Retourne une liste d'états de planification pris en charge.|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|Suspend l'exécution d'une planification donnée.|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|Reprend une planification partagée qui a été suspendue.|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|Définit les propriétés d'un plan d'actualisation du cache.|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|Définit la valeur des propriétés d'une planification partagée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service Web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Méthodes de Service Web Report Server](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Informations techniques de référence &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
