---
title: Exemples d’expressions de groupe (Générateur de rapports) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- data [Reporting Services], grouping
- grouping data
- expressions [Reporting Services], adding
- groups [Reporting Services], expressions
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0e6378f523b74483ed6f1a459f63aafbfa1fc5ee
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "77082099"
---
# <a name="group-expression-examples-report-builder-and-ssrs"></a>Exemples d'expressions de groupe (Générateur de rapports et SSRS)
  Dans une région de données, vous pouvez regrouper des données selon un champ unique ou créer des expressions plus complexes qui identifient les données sur lesquelles effectuer le regroupement. Les expressions complexes incluent des références à plusieurs champs ou paramètres et instructions conditionnelles, ou à du code personnalisé. Quand vous définissez un groupe pour une région de données, vous ajoutez ces expressions aux propriétés du **groupe** . Pour plus d’informations, consultez [Ajouter ou supprimer un groupe dans une région de données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).  
  
 Pour fusionner plusieurs groupes basés sur des expressions de champ simples, ajoutez chaque champ à la liste d'expressions de groupe dans la définition de groupe.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="examples-of-group-expressions"></a>Exemples d'expressions de groupe  
 Le tableau suivant fournit des exemples d'expressions de groupe qu'il est possible d'utiliser pour définir un groupe.  
  
|Description|Expression|  
|-----------------|----------------|  
|Regroupement selon le champ `Region` .|`=Fields!Region.Value`|  
|Regroupement selon le nom et le prénom.|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|Regroupement selon la première lettre du nom.|`=Fields!LastName.Value.Substring(0,1)`|  
|Regroupement selon un paramètre, en fonction de la sélection de l'utilisateur.<br /><br /> Dans cet exemple, le paramètre `GroupBy` doit être basé sur une liste de valeurs disponibles qui fournit un choix valide de regroupements.|`=Fields(Parameters!GroupBy.Value).Value`|  
|Regroupement selon trois tranches d'âge distinctes :<br /><br /> Moins de 21 ans, Entre 21 et 50, et Plus de 50.|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|Regroupement selon de nombreuses tranches d'âge. Cet exemple illustre un code personnalisé, écrit en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, qui retourne une chaîne pour les tranches suivantes :<br /><br /> 25 ou moins<br /><br /> 26 à 50<br /><br /> 51 à 75<br /><br /> Plus de 75|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> Code personnalisé :<br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)  
  
  
