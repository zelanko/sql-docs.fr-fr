---
title: "Gestion des avertissements et des erreurs qui ne lèvent pas d’exceptions | Microsoft Docs"
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
caps.latest.revision: "30"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ab2f3f1830cfd27f261446ca80a73b27126fa232
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a>Gestion des avertissements et des erreurs qui ne lèvent pas d'exceptions
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ne lève pas d'exceptions pour les avertissements et certaines erreurs. Par exemple, lorsque vous utilisez la méthode <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> pour publier un nouveau rapport sur un serveur de rapports, tous les avertissements qui se produisent sont retournés sous la forme d'un tableau d'objets <xref:ReportService2010.Warning>. Ces avertissements doivent être gérés et affichés afin que les mesures appropriées puisse être prises.  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 Les erreurs peuvent également être gérées en évaluant les valeurs de retour de certaines méthodes. Par exemple, la méthode <xref:ReportService2010.ReportingService2010.FindItems%2A> peut être utilisée pour rechercher des éléments spécifiques dans la base de données du serveur de rapports. Si aucun élément correspondant aux critères de recherche n'est trouvé, un tableau null d'objets <xref:ReportService2010.CatalogItem> est retourné. Vous devez évaluer le tableau, vérifier la présence d’éléments **null** et informer l’utilisateur si aucun élément n’a été trouvé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportService2010.CatalogItem>   
 [Présentation de la gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
