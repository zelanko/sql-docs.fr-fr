---
title: "À l’aide des méthodes de Service Web sécurisée | Documents Microsoft"
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
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 1222a4223f54eec0f6083790da4d0afebf353ec9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="using-secure-web-service-methods"></a>Utilisation des méthodes de service Web sécurisées
  Certaines méthodes de service Web Report Server peuvent requérir une connexion sécurisée lorsque vous les appelez. Les méthodes qui requièrent une connexion sécurisée sont déterminées par la **SecureConnectionLevel** définissant dans le fichier RSReportServer.config. La valeur du paramètre est une valeur entière avec une plage valide supérieure ou égale à 0. Le tableau suivant décrit ces valeurs.  
  
|Level| Description|  
|-----------|-----------------|  
|**0**|Non sécurisé. Les appels effectués auprès de l'API SOAP de Reporting Services ne requièrent pas de connexion sécurisée.|  
|Supérieur à **0**|Sécurisé. Les appels effectués auprès de l'API SOAP de Reporting Services requièrent une connexion sécurisée.|  
  
 Vous pouvez utiliser la méthode <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> du service Web pour renvoyer une liste des méthodes de service Web qui requièrent une connexion sécurisée d'après la configuration actuelle du serveur de rapports. Dans un scénario SSL, vous devez évaluer la liste des méthodes qui sont renvoyées par <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> et remplacer le nom de méthode de l'URI de service Web par "https" ou "http" selon la méthode appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service Web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
