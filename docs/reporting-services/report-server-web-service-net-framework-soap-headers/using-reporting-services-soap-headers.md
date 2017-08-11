---
title: "À l’aide de Reporting Services des en-têtes SOAP | Documents Microsoft"
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
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
caps.latest.revision: 39
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 08aec184077b69d05939fe493bf677043beb99d3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="using-reporting-services-soap-headers"></a>Utilisation des en-têtes SOAP de Reporting Services
  La communication avec une méthode Web Service à l'aide de SOAP suit un format standard. Ce format est constitué en partie des données encodées dans un document XML. Le document XML est constitué d’une racine **enveloppe** élément, qui à son tour se compose d’une valeur obligatoire **corps** élément et éventuellement un **en-tête** élément. Le **corps** élément contient les données spécifiques au message. Le paramètre facultatif **en-tête** élément peut contenir des informations supplémentaires pas directement liées au message. Chaque élément enfant de le **en-tête** élément est appelé un en-tête SOAP.  
  
 Bien que les en-têtes SOAP puissent contenir des données en rapport avec le message, ils contiennent en général des informations traitées par l'infrastructure du serveur Web.  
  
 Les services Web Report Server définissent plusieurs classes à utiliser dans l'en-tête SOAP : <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> et <xref:ReportExecution2005.ExecutionHeader>.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Méthodes de traitement par lot](../../reporting-services/report-server-web-service-net-framework-soap-headers/batching-methods.md)|Décrit comment traiter en lot plusieurs opérations dans une transaction unique à l'aide de <xref:ReportService2005.BatchHeader>.|  
|[Identification de l’état d’exécution](../../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)|Décrit comment gérer l’état de session dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à l’aide de **SessionHeader**.|  
|[Paramètre Namespace de l’élément de la méthode GetProperties](../../reporting-services/report-server-web-service-net-framework-soap-headers/setting-the-item-namespace-for-the-getproperties-method.md)|Décrit comment extraire des propriétés selon le chemin d'accès ou l'ID d'un élément, en utilisant la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> et l'en-tête SOAP <xref:ReportService2010.ItemNamespaceHeader>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Informations techniques de référence &#40; SSRS &#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
