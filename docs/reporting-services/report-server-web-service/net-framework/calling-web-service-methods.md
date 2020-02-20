---
title: Appel des méthodes de service web | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 65da2d36c53f5f00851b36f47396b7bcbf6a6092
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "63284609"
---
# <a name="calling-web-service-methods"></a>Appel des méthodes de service Web
  Quand vous utilisez une classe proxy [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pour appeler des opérations de service web, vous le faites en utilisant les méthodes de cette classe. Ces méthodes répondent comme toute autre méthode de classe incluse dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Toutes les méthodes de service Web disposent d'un accès public et requièrent que vous fournissiez le nombre approprié d'arguments et de types d'arguments. Après avoir créé une instance de la classe proxy dans votre projet, vous pouvez appeler les méthodes pour effectuer des opérations de création de rapports via le serveur de rapports. Le code C# suivant illustre l’utilisation de la méthode <xref:ReportService2010.ReportingService2010.ListChildren%2A> de la classe proxy <xref:ReportService2010.ReportingService2010>. Le code est utilisé pour effectuer un appel récurrent du service Web qui renvoie un tableau d'objets <xref:ReportService2010.CatalogItem> qui contient la liste de tous les éléments contenus dans la base de données du serveur de rapports :  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
