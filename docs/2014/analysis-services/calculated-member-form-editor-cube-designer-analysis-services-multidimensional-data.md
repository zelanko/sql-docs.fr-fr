---
title: Éditeur de formulaire de membre (onglet calculs, Concepteur de Cube) calculé (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationexpression.calculatedmember.f1
ms.assetid: f7719b9e-b1e6-4792-90a6-30d9d8eb1196
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 432300f54a7678970f394b27712bcb28ba8a7e7d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088372"
---
# <a name="calculated-member-form-editor-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a>Éditeur de formulaire de membre calculé (onglet Calculs, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Éditeur de formulaire de membre calculé** de l'onglet **Calculs** dans le Concepteur de cube pour créer et modifier un membre calculé.  
  
 **Remarque** Ce volet s'affiche uniquement en mode Formulaire.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom du membre calculé.  
  
 **Propriétés parentes**  
 Développez cette branche pour afficher les options **Hiérarchie parente**, **Membre parent**et **Modifier** .  
  
 **Hiérarchie parente**  
 Sélectionnez dans le cube sélectionné la dimension et la hiérarchie à inclure dans le membre calculé. Sélectionnez MESURES pour définir une mesure calculée.  
  
 **Membre parent**  
 Sélectionnez le membre parent sous lequel le membre calculé doit apparaître.  
  
 **Remarque** Cette option est disponible si **Hiérarchie parente** spécifie une hiérarchie différente de MESURES.  
  
 **Change**  
 Affiche la boîte de dialogue **Sélectionnez le membre parent** pour choisir un **Membre parent**. Pour plus d’informations sur la boîte de dialogue **Sélectionnez le membre parent**, consultez [Boîte de dialogue Sélectionnez le membre parent &#40;Analysis Services - Données multidimensionnelles&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Expression**  
 Développez cette branche pour afficher ou modifier l'expression MDX (Multidimensional Expressions) du membre calculé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
> [!NOTE]  
>  Il est recommandé que cette expression soit évaluée à une chaîne de caractères ou une valeur numérique.  
  
 **Propriétés supplémentaires**  
 Développez cette branche pour afficher les options **Chaîne de format**, **Visible**, **Comportement non vide**, **Expressions de couleur**et **Expressions de police** .  
  
 **Chaîne de format**  
 Tapez la chaîne de format MDX utilisée pour mettre en forme la valeur retournée par le membre calculé ou sélectionnez une chaîne de format prédéfinie.  
  
 Pour plus d’informations sur les chaînes de format MDX, consultez [Contenu de FORMAT_STRING &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md).  
  
 **Visible**  
 Sélectionnez **True** pour que le membre calculé soit visible dans les applications clientes.  
  
 **Comportement non vide**  
 Sélectionnez le nom de la mesure utilisée pour résoudre les requêtes NON EMPTY dans la chaîne MDX du membre calculé. Si la propriété **Comportement non vide** est vide, le membre calculé doit être évalué à plusieurs reprises pour déterminer si un membre est vide. Si la propriété **Comportement non vide** contient le nom d'une mesure, le membre calculé est considéré comme vide si la mesure spécifiée est vide.  
  
> [!WARNING]  
>  Cette propriété est déconseillée. Évitez de l'utiliser. Consultez [Analysis Services déconseillées dans SQL Server 2014](deprecated-analysis-services-features-in-sql-server-2014.md) pour plus d’informations.  
  
 **Expressions de couleur**  
 Développez cette branche pour afficher les options **Couleur avant** et **Couleur d’arrière-plan** .  
  
 **Couleur de premier plan**  
 Tapez l'expression MDX qui fournit la couleur de premier plan du membre calculé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 Cliquez sur le bouton de sélection des couleurs pour afficher la boîte de dialogue **Couleur** et insérer la valeur RVB (rouge/vert/bleu) d’une couleur spécifiée dans l’expression MDX. Pour plus d’informations sur les valeurs RVB, consultez [Contenu de FORE_COLOR et BACK_COLOR &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).  
  
 **Couleur d’arrière-plan**  
 Tapez l'expression MDX qui fournit la couleur d'arrière-plan du membre calculé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 Cliquez sur le bouton de sélection des couleurs pour afficher la boîte de dialogue **Couleur** et insérer la valeur RVB (rouge/vert/bleu) d’une couleur spécifiée dans l’expression MDX. Pour plus d’informations sur les valeurs RVB, consultez [Contenu de FORE_COLOR et BACK_COLOR &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).  
  
 **Expressions de police**  
 Développez cette branche pour afficher les options **Nom de police**, **Taille de police**et **Indicateurs de police** .  
  
 **Nom de police**  
 Tapez l'expression MDX qui fournit le nom de la police utilisée pour le membre calculé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 Cliquez sur le bouton de sélection pour afficher la boîte de dialogue **Police** et insérer les valeurs des propriétés d'une police spécifiée dans l'expression MDX. Pour plus d’informations sur les valeurs des propriétés, consultez [Création et utilisation de valeurs de propriétés &#40;MDX&#41;](creating-and-using-property-values-mdx.md).  
  
 **Taille de la police**  
 Tapez l'expression MDX qui fournit la taille de la police utilisée pour le membre calculé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 Cliquez sur le bouton de sélection pour afficher la boîte de dialogue **Police** et insérer les valeurs des propriétés d'une police spécifiée dans l'expression MDX. Pour plus d’informations sur les valeurs des propriétés, consultez [Création et utilisation de valeurs de propriétés &#40;MDX&#41;](creating-and-using-property-values-mdx.md).  
  
 **Indicateurs de police**  
 Tapez l'expressionDX qui fournit la valeur bitmap qui contient les attributs (ex. souligné ou gras) de la police utilisée pour le membre calculé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 Cliquez sur le bouton de sélection pour afficher la boîte de dialogue **Police** et insérer les valeurs des propriétés d'une police spécifiée dans l'expression MDX. Pour plus d’informations sur les valeurs des propriétés, consultez [Création et utilisation de valeurs de propriétés &#40;MDX&#41;](creating-and-using-property-values-mdx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Calculs](multidimensional-models-olap-logical-cube-objects/calculations.md)   
 [Créer des membres calculés](multidimensional-models/create-calculated-members.md)   
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Calculs &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet calculs, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Organisateur de script &#40;onglet calculs, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Outils de calcul &#40;onglet calculs, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de formulaire de jeu nommé &#40;onglet calculs, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Éditeur de script &#40;onglet calculs, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
