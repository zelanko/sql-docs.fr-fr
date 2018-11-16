---
title: Définition de l’espace de noms des éléments pour la méthode GetProperties | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-soap-headers
ms.topic: reference
helpviewer_keywords:
- item properties [Reporting Services]
- ItemNamespaceHeader SOAP header
- GetProperties method
ms.assetid: b0a08639-3101-40a2-abe2-3a41753826d1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 86d01110e1d1e0146e34a3d2f5c3afe2434f48bd
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51812842"
---
# <a name="setting-the-item-namespace-for-the-getproperties-method"></a>Définition de l'espace de noms d'élément pour la méthode GetProperties
  Vous pouvez utiliser l'en-tête SOAP <xref:ReportService2010.ItemNamespaceHeader> dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour récupérer des propriétés d'élément selon deux identificateurs d'élément différents : le chemin d'accès complet de l'élément ou l'ID de l'élément.  
  
 Lorsque vous effectuez un appel à la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A>, vous passez normalement en tant qu'argument le chemin d'accès complet de l'élément pour lequel vous souhaitez extraire des propriétés. À l'aide de <xref:ReportService2010.ItemNamespaceHeader>, vous pouvez définir l'en-tête SOAP pour votre appel de méthode pour vous permettre d'utiliser <xref:ReportService2010.ReportingService2010.GetProperties%2A> en passant l'ID de l'élément comme un identificateur.  
  
 L'exemple de code suivant extrait les valeurs pour les propriétés d'élément en fonction de l'ID de l'élément.  
  
> [!NOTE]  
>  Par défaut, vous n'avez pas besoin de définir une valeur pour <xref:ReportService2010.ItemNamespaceHeader> si vous passez à la méthode <xref:ReportService2010.ReportingService2010.GetProperties%2A> le chemin d'accès complet comme identificateur d'élément.  
  
```vb  
Imports System  
Imports System.Collections  
  
Class Sample  
   Sub Main()  
      Dim rs As New ReportingService2010()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      rs.Url = "https://<Server Name>/reportserver/ReportService2010.asmx"  
  
      Dim items() As CatalogItem  
  
      Try  
         ' Need the ID property of items. Normally, you would already have   
         ' this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", False)  
  
         ' Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = New ItemNamespaceHeader()  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased  
  
         ' Call GetProperties with item ID.  
         If Not (items Is Nothing) Then  
            Dim item As CatalogItem  
            For Each item In  items  
               Dim properties As [Property]() = rs.GetProperties(item.ID, Nothing)  
               Dim property As [Property]  
               For Each property In  properties  
                  Console.WriteLine(([property].Name + ": " + [property].Value))  
               Next property  
               Console.WriteLine()  
            Next item  
         End If  
  
      Catch e As Exception  
         Console.WriteLine((e.Message + ": " + e.StackTrace))  
      End Try  
   End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.Collections;  
  
class Sample  
{  
   static void Main()  
   {  
   ReportingService2010 rs = new ReportingService2010();  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      rs.Url = "https://<Server Name>/reportserver/ReportService2010.asmx";  
  
      CatalogItem[] items;  
  
      try  
      {  
         // Need the ID property of items. Normally, you would already have   
         // this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", false);  
  
         // Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = new ItemNamespaceHeader();  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased;  
  
         // Call GetProperties with item ID.  
         if (items != null)  
         {  
            foreach( CatalogItem item in items)  
            {  
               Property[] properties = rs.GetProperties(item.ID, null);  
               foreach (Property property in properties)  
               {  
                  Console.WriteLine(property.Name + ": " + property.Value);  
               }  
               Console.WriteLine();  
            }  
         }  
      }  
  
      catch (Exception e)  
      {  
         Console.WriteLine(e.Message);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Informations techniques de référence &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)   
 [Utilisation d’en-têtes SOAP Reporting Services](../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)  
  
  
