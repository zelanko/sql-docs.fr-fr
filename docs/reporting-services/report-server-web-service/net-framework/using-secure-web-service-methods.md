---
title: Utilisation des méthodes de service web sécurisées | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 84c0b693df2906d4ab3245df20c3b9a979cf07f6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "63128801"
---
# <a name="using-secure-web-service-methods"></a>Utilisation des méthodes de service Web sécurisées
  Certaines méthodes de service Web Report Server peuvent requérir une connexion sécurisée lorsque vous les appelez. Ces méthodes qui exigent une connexion sécurisée sont déterminées par le paramètre **SecureConnectionLevel** dans le fichier RSReportServer.config. La valeur du paramètre est une valeur entière avec une plage valide supérieure ou égale à 0. Le tableau suivant décrit ces valeurs.  
  
|Level|Description|  
|-----------|-----------------|  
|**0**|Non sécurisé. Les appels effectués auprès de l'API SOAP de Reporting Services ne requièrent pas de connexion sécurisée.|  
|Supérieur à **0**|Sécurisé. Les appels effectués auprès de l'API SOAP de Reporting Services requièrent une connexion sécurisée.|  
  
 Vous pouvez utiliser la méthode <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> du service Web pour renvoyer une liste des méthodes de service Web qui requièrent une connexion sécurisée d'après la configuration actuelle du serveur de rapports. Dans un scénario SSL, vous devez évaluer la liste des méthodes qui sont renvoyées par <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> et remplacer le nom de méthode de l'URI de service Web par "https" ou "http" selon la méthode appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service Web des serveurs de rapports](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
