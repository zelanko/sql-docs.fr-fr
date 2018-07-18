---
title: Boîte de dialogue Expression (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10040"
helpviewer_keywords:
- expressions
ms.assetid: e89c4d97-5d41-4b55-8695-79329edac15d
caps.latest.revision: 16
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 130d436ceb8080e6e7d70adc41196f3e76b07edb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244499"
---
# <a name="expression-dialog-box-report-builder"></a>Boîte de dialogue Expression (Générateur de rapports)
  Utilisez le **Expression** boîte de dialogue pour écrire [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] propriétés d’un élément expressions pour les rapports. Vous pouvez utiliser des expressions pour définir un grand nombre de propriétés, notamment la couleur, la police et les bordures. Au moment de l'exécution, le processeur de rapports évalue les expressions et remplace le résultat de la valeur de la propriété.  
  
 La boîte de dialogue **Expression** contient une fenêtre de code, une arborescence des catégories, des éléments de catégorie, un volet de description et un volet d’exemple. Le **Expression** boîte de dialogue est contextuelle ; les éléments de catégorie et les descriptions changent en réponse à la catégorie d’expression que vous travaillez. Pour plus d’informations, consultez [exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md), [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
## <a name="expression-constructs"></a>Composants d'une expression  
 Les expressions commencent par un signe égal (=) et peuvent inclure des constantes, des littéraux, des opérateurs, ainsi que des références à des champs prédéfinis, à des collections intégrées, à des fonctions intégrées, à des fonctions de la bibliothèque d'exécutables [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], à des classes Common Language Runtime (CLR) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] et à des fonctions personnalisées. La liste suivante décrit les catégories et les valeurs que vous pouvez ajouter à une expression.  
  
 **Définir l’expression pour :***\<PropertyName >  *  
 Nom de la propriété pour laquelle vous définissez une expression. Vous pouvez également définir cette propriété, par son nom, dans le volet Propriétés.  
  
 **Constantes**  
 Fournit la liste des valeurs prédéfinies valides pour cette propriété pour les propriétés basées sur des constantes. Par exemple, une propriété basée sur la couleur affiche les noms de couleur valides. Pour une propriété qui est un type de données booléen, les valeurs sont `True` et `False`.  
  
 Une constante ne peut pas être affectée à tous les éléments qui prennent en charge les expressions. Si une valeur constante ne peut pas être affectée à une propriété, le volet de description l'indique.  
  
 **Champs prédéfinis**  
 Donne la liste des éléments de la collection globale que vous pouvez utiliser dans une expression. Certaines collections ne sont prises en charge qu'après la publication du rapport sur le serveur. Pour plus d’informations, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **Paramètres**  
 Fournit la liste des paramètres de rapport.  
  
 **Champs (** * \<dataset_sélectionné >* **)**  
 Affiche la liste des champs du dataset sélectionné dans la catégorie Datasets. Double-cliquez sur un champ pour le copier dans la zone **Expression** .  
  
 **Jeux de données**  
 Donne la liste des datasets disponibles et affiche les champs membres du dataset.  
  
 **Variables**  
 Affiche la liste des variables de rapport. Pour plus d’informations, consultez [Références à des collections de variables de rapport et de groupe &#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md).  
  
 **Opérateurs**  
 Affiche les opérateurs que vous pouvez inclure dans un calcul ou une manipulation de chaîne. Pour plus d’informations, consultez [Opérateurs dans les expressions &#40;Générateur de rapports et SSRS&#41;](report-design/operators-in-expressions-report-builder-and-ssrs.md).  
  
 **Fonctions communes**  
 Affiche des fonctions communes, regroupées par type. Lorsque vous sélectionnez une fonction dans le volet Élément, une description et un exemple s'affichent.  
  
 Les fonctions communes incluent les fonctions de rapport et d'agrégation intégrées, les fonctions de la bibliothèque d'exécutables [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et les classes Common Language Runtime (CLR) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] de l'espace de noms <xref:System.Math> et <xref:System.Convert>. Vous pouvez également ajouter des références à des classes CLR et à des assemblys externes qui n'apparaissent pas dans la liste des catégories. Pour plus d’informations, consultez [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
## <a name="options"></a>Options  
 Fenêtre de code  
 Utilisez la fenêtre de code du volet supérieur pour taper une expression. Quand vous ouvrez la boîte de dialogue **Expression** , la fenêtre de code contient l’expression. Vous pouvez remplacer ou modifier l'expression. Vous pouvez ajouter des appels de fonction, des opérateurs, des constantes, des champs, des paramètres, des éléments issus des collections globales et des références à du code personnalisé. La fenêtre de code affiche vos modifications à mesure que vous les apportez.  
  
 Un soulignement ondulé rouge signale une erreur de syntaxe. Pointez sur le texte souligné pour afficher le message d'erreur.  
  
 Lorsque vous entrez des termes de collections globales suivis d'un signe de ponctuation, une liste déroulante affiche les membres ou propriétés disponibles. Dans la liste déroulante, vous pouvez taper les tout premiers caractères suivis d'une tabulation pour remplir automatiquement la sélection.  
  
 Lorsque vous tapez un nom de fonction suivi d'une parenthèse ouvrante, une info-bulle qui fournit des informations sur les paramètres et les valeurs de retour de fonction s'affiche.  
  
 **Catégorie**  
 Affiche les catégories d'expressions. Le choix d'une catégorie établit un contexte pour la création d'une expression et modifie la liste des valeurs valides dans le volet Élément. Par exemple, pour une expression pour une valeur de zone de texte, développez fonctions communes et sélectionnez les fonctions d’agrégation pour afficher `Avg`, `Count`et d’autres fonctions dans le **élément** volet.  
  
 **Élément**  
 Affiche la liste des valeurs valides pour la catégorie sélectionnée. Double-cliquez sur un élément pour ajouter le texte de l'expression pour cet élément au point d'insertion dans la fenêtre de code.  
  
 **Valeurs**  
 En fonction de la catégorie et de l'élément sélectionnés, le troisième volet contient une description, un exemple d'expression ou la liste des valeurs valides. Faites glisser le bord de la boîte de dialogue pour élargir la zone d'aperçu.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Mise en forme des éléments de rapport &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Mise en forme des nombres et des Dates &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Références à la collection Parameters&#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-parameters-collection-references-report-builder.md)   
 [Exemples d’expressions de groupe &#40;Générateur de rapports et SSRS&#41;](report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [Exemples d’équations de filtre &#40;Générateur de rapports et SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [Références à la Collection de champs de DataSet &#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-dataset-fields-collection-references-report-builder.md)   
 [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Sélectionnez la boîte de dialogue couleur &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/select-color-dialog-box-report-builder-and-ssrs.md)  
  
  
