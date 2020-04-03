---
title: Utilisation des en-têtes SOAP Reporting Services | Microsoft Docs
description: Utilisez les en-têtes SOAP Reporting Services pour exécuter un lots d’opérations au sein d’une même transaction, gérer l’état de la session et récupérer des propriétés en fonction du chemin ou de l’ID d’un élément.
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-soap-headers
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7f0cb5dc846e8f1f7e292366c7f938366b53de2d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216195"
---
# <a name="using-reporting-services-soap-headers"></a>Utilisation des en-têtes SOAP de Reporting Services
  La communication avec une méthode Web Service à l'aide de SOAP suit un format standard. Ce format est constitué en partie des données encodées dans un document XML. Le document XML consiste en un élément **Envelope** racine, composé lui-même d’un élément **Body** obligatoire et d’un élément **Header** facultatif. L’élément **Body** contient les données propres au message. L’élément **Header** facultatif peut contenir des informations supplémentaires qui ne sont pas directement liées au message. Chaque élément enfant de l’élément **Header** est appelé « en-tête SOAP ».  
  
 Bien que les en-têtes SOAP puissent contenir des données en rapport avec le message, ils contiennent en général des informations traitées par l'infrastructure du serveur Web.  
  
 Les services Web Report Server définissent plusieurs classes à utiliser dans l'en-tête SOAP : <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> et <xref:ReportExecution2005.ExecutionHeader>.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Méthodes de traitement par lot](../../reporting-services/report-server-web-service-net-framework-soap-headers/batching-methods.md)|Décrit comment traiter en lot plusieurs opérations dans une transaction unique à l'aide de <xref:ReportService2005.BatchHeader>.|  
|[Identification de l'état d'exécution](../../reporting-services/report-server-web-service-net-framework-soap-headers/identifying-execution-state.md)|Explique comment gérer l’état de session dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à l’aide de **SessionHeader**.|  
|[Définition de l'espace de noms des éléments pour la méthode GetProperties](../../reporting-services/report-server-web-service-net-framework-soap-headers/setting-the-item-namespace-for-the-getproperties-method.md)|Décrit comment extraire des propriétés selon le chemin d'accès ou l'ID d'un élément, en utilisant la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> et l'en-tête SOAP <xref:ReportService2010.ItemNamespaceHeader>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
