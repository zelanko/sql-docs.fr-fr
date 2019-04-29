---
title: Références à des collections de variables de rapport et de groupe (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10404"
- sql12.rtp.rptdesigner.categorygroupproperties.variables.f1
- "10083"
- sql12.rtp.rptdesigner.seriesgroupproperties.variables.f1
- sql12.rtp.rptdesigner.reportproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- "10292"
- "10412"
ms.assetid: 4be5b463-3ce2-483d-a3c6-dae752cb543e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4733ba204671ec3ed691e77626fb08861b7e6763
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63020742"
---
# <a name="report-and-group-variables-collections-references-report-builder-and-ssrs"></a>Références à des collections de variables de rapport et de groupe (Générateur de rapports et SSRS)
  Lorsqu'un calcul complexe est utilisé plusieurs fois dans les expressions d'un rapport, vous pouvez créer une variable. Vous pouvez créer une variable de rapport ou une variable de groupe. Les noms de variable doivent être uniques dans un rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-variables"></a>Variables de rapport  
 Utilisez une variable de rapport pour contenir une valeur dans le cadre de calculs qui dépendent du temps, tels que les taux de change ou horodatages, ou pour un calcul complexe référencé plusieurs fois. Par défaut, une variable de rapport est calculée une fois et peut être utilisée dans les expressions de l'ensemble d'un rapport. Les variables de rapport sont en lecture seule par défaut. Vous pouvez modifier la valeur par défaut pour permettre à une variable de rapport d'être en lecture-écriture. La valeur d'une variable de rapport est conservée tout au long d'une session, jusqu'à ce que le rapport soit traité une nouvelle fois.  
  
 Pour ajouter une variable de rapport, ouvrez la boîte de dialogue **Propriétés du rapport** , cliquez sur **Variables**, puis spécifiez un nom et une valeur. Les noms sont des chaînes sensibles à la casse qui commencent par une lettre et qui ne contiennent aucun espace. Un nom peut inclure des lettres, des nombres et des traits de soulignement (_).  
  
 Pour faire référence à la variable dans une expression, utilisez la syntaxe de collection globale, par exemple `=Variables!CustomTimeStamp.Value`. Sur l’aire de conception, la valeur s’affiche dans une zone de texte sous la forme `<<Expr>>`.  
  
 Vous pouvez utiliser les variables de rapport des manières suivantes :  
  
-   **Utilisation en lecture seule** Définissez une valeur une fois pour créer une constante pour la session de rapport, par exemple pour créer un horodatage.  
  
     Dans la mesure où les expressions dans les zones de texte sont évaluées à la demande quand un utilisateur navigue parmi les pages d’un rapport, les valeurs dynamiques (par exemple, une expression qui inclut la fonction `Now()` , qui retourne l’heure du jour) peuvent retourner des valeurs différentes si vous passez aux pages suivante et précédente à l’aide du bouton **Précédent** . En définissant la valeur d'une variable de rapport avec l'expression `=Now()`, puis en ajoutant la variable à votre expression, vous garantissez que la même valeur est utilisée dans l'intégralité du traitement des rapports.  
  
-   **Utilisation en lecture/écriture** Définissez une valeur une fois et sérialisez-la dans une session de rapport. L'option en lecture-écriture pour les variables fournit une meilleure alternative que l'utilisation d'une variable statique dans le bloc de code dans la définition de rapport.  
  
     Lorsque vous désactivez le **en lecture seule** option pour une variable, la propriété accessible en écriture pour la variable est définie sur `true`. Pour mettre à jour la valeur à partir d’une expression, utilisez la méthode SetValue, par exemple `=Variables!MyVariable.SetValue("123")`.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas contrôler le moment où le processeur de rapports initialise une variable ou évalue une expression qui met à jour une variable. L'ordre d'exécution pour l'initialisation d'une variable est non défini.  
  
 Pour plus d’informations sur les sessions, consultez [Aperçu des rapports dans le Générateur de rapports](../report-builder/previewing-reports-in-report-builder.md).  
  
## <a name="group-variables"></a>Variables de groupe  
 Utilisez une variable de groupe pour calculer une expression complexe dans l'étendue d'un groupe. Une variable de groupe est valide uniquement dans l'étendue du groupe et ses groupes enfants.  
  
 Par exemple, supposez qu'une région de données affiche des données d'inventaire pour des éléments qui sont dans différentes catégories d'impôts et que vous souhaitez appliquer différents taux de taxe pour chaque catégorie. Vous regroupez les données en fonction des catégories et définissez une variable *Tax* sur le groupe parent. Vous définissez ensuite une variable de groupe pour *ItemTax* pour chaque catégorie d’impôts et affectez chacun des différents sous-groupes de catégories à la variable de groupe correcte. Exemple :  
  
-   Pour le groupe parent basé sur `[Category]`, affectez à la variable *Tax* la valeur `[Tax]`. Supposez que les valeurs des catégories sont Food et Clothing.  
  
-   Pour le groupe enfant basé sur `[Subcategory]`, affectez à la variable *ItemsTax* la valeur `=Variables!Tax.Value * Sum(Fields!Price.Value)`. Supposez que les valeurs des sous-catégories pour la catégorie Food sont Beverages et Bread. Supposez que les valeurs des sous-catégories pour Clothing sont Shirts et Hats.  
  
-   Pour une zone de texte d’une ligne située dans le groupe enfant, ajoutez l’expression `=Variables!ItemsTax.Value`.  
  
     La zone de texte affiche l'impôt total pour Beverages et Bread à l'aide de l'impôt de la catégorie Food, et pour Shirts et Hats à l'aide de l'impôt de la catégorie Clothing.  
  
 Pour ajouter une variable de groupe, ouvrez la boîte de dialogue **Propriétés du groupe de tableaux matriciels** , cliquez sur **Variables**, puis indiquez un nom et une valeur. La variable de groupe est calculée une fois par valeur de groupe unique.  
  
 Pour faire référence à la variable dans une expression, utilisez la syntaxe de collection globale, par exemple `=Variables!GroupDescription.Value`. Sur l’aire de conception, la valeur s’affiche dans une zone de texte sous la forme `<<Expr>>`.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](built-in-collections-in-expressions-report-builder.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)  
  
  
