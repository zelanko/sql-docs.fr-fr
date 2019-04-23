---
title: Utilisation de l’interface IDeliveryReportServerInformation pour une extension de remise | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a94b6da8536ee0269a448b8a446fc0da3f3f576
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60155307"
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
  
  
