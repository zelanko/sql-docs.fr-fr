---
title: "Ajouter du code &#224; un rapport (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "code [Reporting Services]"
  - "code personnalisé [Reporting Services]"
  - "expressions [Reporting Services], code"
  - "ajout de code"
  - "rapports [Reporting Services], code"
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
caps.latest.revision: 41
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 41
---
# Ajouter du code &#224; un rapport (SSRS)
  Dans toute expression, vous pouvez appeler votre propre code personnalisé. Vous pouvez fournir du code des deux manières suivantes :  
  
-   Incorporez du code écrit en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] directement dans votre rapport. Si votre code fait référence à un élément [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] qui n’est pas <xref:System.Math> ni <xref:System.Convert>, vous devez ajouter la référence au rapport. Pour plus d’informations, consultez [Ajouter une référence d’assembly à un rapport &#40;SSRS&#41;](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md). Pour plus d’informations sur les autres références au code possibles, consultez [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
-   Fournissez un assembly de code personnalisé en utilisant le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Si vous fournissez un assembly personnalisé, vous devez l'installer à la fois sur l'ordinateur où vous créez le rapport et sur le serveur de rapports où vous affichez le rapport. Pour plus d’informations, consultez [Utilisation d’assemblys personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md).  
  
### Pour ajouter du code incorporé à un rapport  
  
1.  En mode **Conception**, cliquez avec le bouton droit sur l’aire de conception à l’extérieur de la bordure du rapport et cliquez sur **Propriétés du rapport**.  
  
2.  Cliquez sur **Code**.  
  
3.  Dans **Code personnalisé**, tapez le code. Des erreurs de code génèrent des avertissements lorsque le rapport s'exécute. L'exemple suivant crée une fonction personnalisée nommée `ChangeWord` qui remplace le mot « `Bike` » par « `Bicycle` ».  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  L'exemple suivant montre comment transmettre un champ de dataset nommé Category à cette fonction dans une expression :  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     Si vous ajoutez cette expression à une cellule de table qui affiche des valeurs de catégorie, chaque fois que le mot « Bike » est dans le champ de dataset pour cette ligne, la valeur de cellule de table affiche à la place le mot « Bicycle ».  
  
## Voir aussi  
 [Boîte de dialogue Propriétés du rapport, Code](../Topic/Report%20Properties%20Dialog%20Box,%20Code.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Informations de référence sur la collection de paramètres &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/parameters-collection-references-report-builder-and-ssrs.md)  
  
  