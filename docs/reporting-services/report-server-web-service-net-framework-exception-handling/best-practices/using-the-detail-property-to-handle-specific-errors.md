---
title: "Pour gérer les erreurs spécifiques à l’aide de la propriété Detail | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
caps.latest.revision: 30
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: cbbaf57ce4726bbb16c8cb722f50ac186fe59d81
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Utilisation de la propriété Detail pour gérer des erreurs spécifiques
  Pour classer les exceptions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] retourne des informations d’erreur supplémentaires dans le **InnerText** propriété des éléments enfants dans l’exception de SOAP **détail** propriété. Étant donné que la **détail** propriété est un **XmlNode** de l’objet, vous pouvez accéder à du texte interne de la **Message** élément enfant à l’aide du code suivant.  
  
 Pour obtenir la liste de tous les éléments enfants disponibles contenues dans le **détail** propriété, consultez [propriété Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md). Pour plus d’informations, consultez « Propriété Detail » dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentation du Kit de développement logiciel.  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 La ligne de code suivante écrit le code d'erreur spécifique qui est retourné dans l'exception SOAP sur la console. Vous pouvez également évaluer le code d'erreur et effectuer des actions spécifiques.  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Table d’erreurs SoapException](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  

