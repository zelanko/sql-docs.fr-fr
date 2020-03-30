---
title: Ajouter du code à un rapport | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bd2f5d60bacc29a5b7efcf1abb8c1d44429d93f6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "77081670"
---
# <a name="add-code-to-a-report-ssrs"></a>Ajouter du code à un rapport (SSRS)
  Dans toute expression, vous pouvez appeler votre propre code personnalisé. Vous pouvez fournir du code des deux manières suivantes :  
  
-   Incorporez du code écrit en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] directement dans votre rapport. Si votre code fait référence à un élément [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] qui n’est pas <xref:System.Math> ni <xref:System.Convert>, vous devez ajouter la référence au rapport. Pour plus d’informations, consultez [Ajouter une référence d’assembly à un rapport &#40;SSRS&#41;](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md). Pour plus d’informations sur les autres références au code possibles, consultez [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
-   Fournissez un assembly de code personnalisé en utilisant le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Si vous fournissez un assembly personnalisé, vous devez l'installer à la fois sur l'ordinateur où vous créez le rapport et sur le serveur de rapports où vous affichez le rapport. Pour plus d’informations, consultez [Utilisation d’assemblys personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md).  
  
### <a name="to-add-embedded-code-to-a-report"></a>Pour ajouter du code incorporé à un rapport  
  
1.  En mode **Conception** , cliquez avec le bouton droit sur l’aire de conception à l’extérieur de la bordure du rapport et cliquez sur **Propriétés du rapport**.  
  
2.  Cliquez sur **Code**.  
  
3.  Dans **Code personnalisé**, tapez le code. Des erreurs de code génèrent des avertissements lorsque le rapport s'exécute. L'exemple suivant crée une fonction personnalisée nommée `ChangeWord` qui remplace le mot «`Bike`» par «`Bicycle`».  
  
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
  
4.  L'exemple suivant montre comment transmettre un champ de dataset nommé Category à cette fonction dans une expression :  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     Si vous ajoutez cette expression à une cellule de table qui affiche des valeurs de catégorie, chaque fois que le mot « Bike » est dans le champ de dataset pour cette ligne, la valeur de cellule de table affiche à la place le mot « Bicycle ».  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Propriétés du rapport, Code](https://msdn.microsoft.com/library/955d4b11-17b4-4f1c-9690-6e7af54caea7)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Références à la collection Parameters &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
