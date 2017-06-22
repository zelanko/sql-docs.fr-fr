---
title: "Empêche les demandes non valides | Documents Microsoft"
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
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4ec670f66ad710e0f9a21f03681aedcac943ef35
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="preventing-invalid-requests"></a>Éviter les demandes non valides
  Vous pouvez éviter que certains types d'exceptions soient levés en analysant le flux de votre application et en veillant à ce que les demandes qui sont envoyées au serveur de rapports soient valides. Par exemple, dans les applications qui permettent aux utilisateurs d'ajouter ou de mettre à jour le nom d'un rapport, d'une source de données ou d'autres éléments de serveur de rapports, vous devez valider le texte entré par un utilisateur. Vous devez toujours vérifier que la demande ne contient pas de caractères réservés avant de l'envoyer à un serveur de rapports. Utilisez conditionnelle **si** instructions ou autres constructions logiques dans votre code pour avertir l’utilisateur qu’ils n’ont pas remplies les conditions nécessaires pour envoyer des demandes au serveur de rapports.  
  
 Dans l'exemple C# simplifié suivant, un message d'erreur convivial s'affiche lorsque les utilisateurs essaient de créer un rapport dont le nom contient une barre oblique (/).  
  
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
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 Pour plus d’informations sur les types d’erreurs qui peuvent être évités avant les demandes sont envoyées au serveur de rapports, consultez [Table d’erreurs SoapException](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md). Pour plus d’informations sur la manière d’améliorer l’exemple précédent, à l’aide des blocs try/catch, consultez [utilisation de Try et les blocs Catch](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
