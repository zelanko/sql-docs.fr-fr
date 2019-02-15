---
title: Informations de référence sur la collection ReportItems (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: edc0c75f-0530-4e6d-85aa-3385301bfd00
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 92872f29600bc380025e76933ef8a1aab2879e51
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56285877"
---
# <a name="reportitems-collection-references-report-builder-and-ssrs"></a>Références à la collection ReportItems (Générateur de rapports et SSRS)
  La collection intégrée `ReportItems` constitue l'ensemble des zones de texte des éléments de rapport, tels que les lignes d'une région de données ou les zones de texte de l'aire de conception du rapport. La collection `ReportItems` comprend les zones de texte situées dans l'étendue actuelle d'un en-tête de page, d'un pied de page ou du corps du rapport. Cette collection est déterminée au moment de l'exécution par le processeur de rapports et le convertisseur de rapports. L'étendue actuelle change à mesure que le processeur de rapports combine successivement les données du rapport et ses éléments de mise en page lorsque l'utilisateur visualise les pages du rapport. Vous pouvez utiliser la collection intégrée `ReportItems` pour produire des en-têtes de page de type dictionnaire, qui représentent le premier et le dernier éléments de chaque page.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-reportitems-value-property"></a>Utilisation de la propriété Value de ReportItems  
 Éléments de la `ReportItems` collection n'avoir qu’une seule propriété : Valeur : La valeur d'un élément de `ReportItems` peut être utilisée pour afficher ou pour calculer des données provenant d'un autre champ du rapport. Pour accéder à la valeur de la zone de texte actuelle, vous pouvez utiliser l’entité [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] globale intégrée Me.Value ou simplement Value. Dans les fonctions de rapport telles que First et les fonctions d'agrégation, il convient toutefois d'utiliser la syntaxe complète.  
  
 Exemple :  
  
-   Cette expression, placée dans une zone de texte, affiche la valeur d'une zone de texte `ReportItem` nommée `Textbox1` :  
  
     `=ReportItems!Textbox1.Value`  
  
-   Cette expression, placée dans un `ReportItem` la zone de texte propriété de couleur, affiche le texte en noir lorsque la valeur est > 0 ; sinon, la valeur est affichée en rouge :  
  
     `=IIF(Me.Value > 0,"Black","Red")`  
  
-   Cette expression, placée dans une zone de texte dans l’en-tête ou le pied de page, affiche la première valeur par page du rapport rendu pour une zone de texte nommée `LastName`:  
  
     `=First(ReportItems("LastName").Value)`  
  
## <a name="dictionary-style-page-header-expressions"></a>Expressions d'en-tête de page de type dictionnaire  
 Vous pouvez créer un en-tête de page pour afficher le premier et le dernier clients qui figurent sur la page. Une zone de texte de l'en-tête de page ne pouvant pas faire référence à la collection intégrée `ReportItems` plus d'une fois dans une expression, vous devez ajouter deux zones de texte à l'en-tête de page : une pour le premier nom de client (`=First(ReportItems!textboxLastName.Value`) et une pour le dernier (`=Last(ReportItems!textboxLastName.Value`).  
  
 Dans une section d'en-tête ou de pied de page, seules les zones de texte de la page actuelle sont disponibles en tant que membres de la collection `ReportItems`. Par exemple, si `ReportItems!textboxLastName.Value` fait référence à une zone de texte qui ne figure que sur la première page d’une région de données qui en comprend plusieurs, vous voyez une valeur pour la première page, mais toutes les autres pages affichent **#Erreur** pour indiquer que l’expression n’a pas pu être évaluée comme écrite.  
  
## <a name="scope-for-the-reportitems-collection"></a>Étendue de la collection ReportItems  
 À mesure que le rapport est traité, chaque zone de texte du corps du rapport ou d'une région de données est évaluée dans le contexte de son dataset, de sa région de données et des associations de groupes. L'étendue d'une référence à la collection `ReportItems` est l'étendue actuelle ou tout point situé plus haut.  
  
 Par exemple, une zone de texte d'une ligne située dans un groupe parent ne doit pas contenir d'expression faisant référence au nom d'une zone de texte d'une ligne située dans un groupe enfant. Une telle expression ne donne pas de valeur dans le rapport, car la zone de texte de la ligne enfant n'appartient pas à l'étendue. Pour plus d’informations, consultez [Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](built-in-collections-in-expressions-report-builder.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
