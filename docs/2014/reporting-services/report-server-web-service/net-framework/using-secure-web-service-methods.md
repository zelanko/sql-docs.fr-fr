---
title: Utilisation des méthodes de service web sécurisées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7e05a1656395828181f8622f82a4127107fa8ecc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238319"
---
# <a name="using-secure-web-service-methods"></a>Utilisation des méthodes de service Web sécurisées
  Certaines méthodes de service Web Report Server peuvent requérir une connexion sécurisée lorsque vous les appelez. Ces méthodes sont déterminées par le paramètre `SecureConnectionLevel` dans le fichier RSReportServer.config. La valeur du paramètre est une valeur entière avec une plage valide supérieure ou égale à 0. Le tableau suivant décrit ces valeurs.  
  
|Level|Description|  
|-----------|-----------------|  
|**0**|Non sécurisé. Les appels effectués auprès de l'API SOAP de Reporting Services ne requièrent pas de connexion sécurisée.|  
|Supérieur à **0**|Sécurisé. Les appels effectués auprès de l'API SOAP de Reporting Services requièrent une connexion sécurisée.|  
  
 Vous pouvez utiliser la méthode <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> du service Web pour renvoyer une liste des méthodes de service Web qui requièrent une connexion sécurisée d'après la configuration actuelle du serveur de rapports. Dans un scénario SSL, vous devez évaluer la liste des méthodes qui sont renvoyées par <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> et remplacer le nom de méthode de l'URI de service Web par "https" ou "http" selon la méthode appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service Web des serveurs de rapports](../report-server-web-service.md)  
  
  
