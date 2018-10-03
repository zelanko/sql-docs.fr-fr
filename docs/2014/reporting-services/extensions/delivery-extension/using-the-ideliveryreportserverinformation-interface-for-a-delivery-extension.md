---
title: Utilisation de l’interface IDeliveryReportServerInformation pour une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d5198b839c0d11821f586f8f3c403c0bcdf96367
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222831"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>Utilisation de l'interface IDeliveryReportServerInformation pour une extension de remise
  L'interface <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> expose plusieurs propriétés que vous pouvez utiliser pour extraire des informations relatives à un serveur de rapports. Vous pouvez utiliser ces informations pour remettre des notifications et des rapports. Lors de l'implémentation de votre classe d'extension de remise, implémentez la propriété <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> comme étant requise par l'interface <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. La propriété <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> retourne un objet qui implémente l'interface <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>. À partir de cet objet, vous pouvez obtenir une liste des extensions de rendu actuellement prises en charge par le serveur de rapports.  
  
 Ce qui suit `for` boucle peut être utilisée pour stocker une liste des extensions de rendu actuellement disponibles sur le serveur de rapports dans un **ArrayList** objet.  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 Pour plus d’informations sur l’interface <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>, consultez [Utilisation de l’interface IDeliveryReportServerInformation pour une extension de remise](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Implémentation d’une extension de remise](implementing-a-delivery-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  
