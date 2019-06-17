---
title: Boîte de dialogue Expression | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10040"
- sql12.rtp.rptdesigner.expression.f1
helpviewer_keywords:
- Expression dialog box [Reporting Services]
ms.assetid: e6c74ccb-4594-4d4f-b958-618d710e34eb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 905aa453c8a6cac78e8423d071672d6431e3c3c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66109199"
---
# <a name="expression-dialog-box"></a>Boîte de dialogue Expression
  Utilisez le **Expression** boîte de dialogue pour écrire [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] propriétés d’un élément expressions pour les rapports. Vous pouvez utiliser des expressions pour définir un grand nombre de propriétés, notamment la couleur, la police et les bordures. Au moment de l'exécution, le processeur de rapports évalue les expressions et remplace le résultat de la valeur de la propriété.  
  
 Une expression peut être simple ou complexe. Vous pouvez taper des expressions simples directement dans une zone de texte sur l'aire de conception ou dans une boîte de dialogue. Pour créer des expressions complexes, utilisez le **Expression** boîte de dialogue. Vous ne pouvez créer qu'une seule expression à la fois. Pour plus d’informations, consultez [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md).  
  
 Pour ouvrir la boîte de dialogue **Expression** , cliquez sur le bouton Expression (**fx**) dans les boîtes de dialogue, ou sélectionnez **Expression** dans le menu contextuel ou les listes déroulantes du volet Propriétés. Pour plus d’informations, consultez [utilisation d’expressions dans les rapports &#40;Générateur de rapports et SSRS&#41;](report-design/expression-uses-in-reports-report-builder-and-ssrs.md).  
  
 La boîte de dialogue **Expression** contient une fenêtre de code, une arborescence des catégories, des éléments de catégorie, un volet de description et un volet d’exemple.  
  
 La boîte de dialogue **Expression** est contextuelle : les éléments de catégorie et les descriptions changent en fonction de la catégorie d’expression sur laquelle vous travaillez. Elle prend en charge IntelliSense, la saisie semi-automatique des instructions, les exemples d'appels de fonction et les couleurs de la syntaxe pour vous aider à détecter les erreurs de syntaxe.  
  
## <a name="expression-constructs"></a>Composants d'une expression  
 Les expressions commencent par un signe égal (=) et peuvent inclure des constantes, des littéraux, des opérateurs, ainsi que des références à des champs prédéfinis, à des collections intégrées, à des fonctions intégrées, à des fonctions de la bibliothèque d'exécutables [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], à des classes Common Language Runtime (CLR) [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] et à des fonctions personnalisées. La liste suivante décrit les catégories et les valeurs que vous pouvez ajouter à une expression.  
  
 **Définir l’expression pour :**  _\<PropertyName>_  
 Nom de la propriété pour laquelle vous définissez une expression. Vous pouvez également définir cette propriété, par son nom, dans le volet Propriétés.  
  
 **Constantes**  
 Fournit la liste des valeurs prédéfinies valides pour cette propriété pour les propriétés basées sur des constantes. Par exemple, une propriété basée sur la couleur affiche les noms de couleur valides. Pour une propriété qui est un type de données Booléen, les valeurs sont `True` et `False`.  
  
 Une constante ne peut pas être affectée à tous les éléments qui prennent en charge les expressions. Si une valeur constante ne peut pas être affectée à une propriété, le volet de description l'indique.  
  
 **Champs prédéfinis**  
 Donne la liste des éléments de la collection globale que vous pouvez utiliser dans une expression. Certaines collections ne sont prises en charge qu'après la publication du rapport sur le serveur. Pour plus d’informations, consultez [Références à des champs Globals et Users prédéfinis &#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md).  
  
 **Paramètres**  
 Fournit la liste des paramètres de rapport.  
  
 **Champs (**  _\<dataset_sélectionné >_ **)**  
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
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Mise en forme des nombres et des dates &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Références à la collection Parameters&#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-parameters-collection-references-report-builder.md)   
 [Exemples d’expressions de groupe &#40;Générateur de rapports et SSRS&#41;](report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [Exemples d’équations de filtre &#40;Générateur de rapports et SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md)   
 [Ajouter une expression &#40;Générateur de rapports et SSRS&#41;](report-design/add-an-expression-report-builder-and-ssrs.md)  
  
  
