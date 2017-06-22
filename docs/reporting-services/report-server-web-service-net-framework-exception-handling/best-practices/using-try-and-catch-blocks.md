---
title: "À l’aide de blocs Try et Catch | Documents Microsoft"
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
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
caps.latest.revision: 29
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 659707603a24ff8d59bfc1b001d80e8184c119e1
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="using-try-and-catch-blocks"></a>À l’aide de Try et les blocs Catch
  Après avoir limité les demandes non valides au serveur de rapports en ajoutant des instructions conditionnelles à votre code, vous devez fournir une gestion adéquate des exceptions à l'aide des blocs try/catch. Cette technique fournit une autre couche de protection contre les demandes qui ne sont pas valides. Si une demande faite au serveur de rapports est incluse dans un bloc try et que cette demande entraîne la levée d'une exception par le serveur de rapports, l'exception est interceptée dans le bloc catch, empêchant ainsi votre application de se terminer de façon inattendue. Une fois l'exception interceptée, vous pouvez l'utiliser soit pour instruire l'utilisateur de modifier son action, soit pour l'informer, de façon amicale, qu'une erreur s'est produite. Vous pouvez utiliser ensuite un bloc finally pour nettoyer les ressources. D'une manière idéale, vous devez élaborer un plan général de gestion des exceptions afin d'éviter une duplication inutile des blocs try/catch.  
  
 L'exemple suivant utilise les blocs try/catch pour améliorer la fiabilité du code de gestion des exceptions.  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
