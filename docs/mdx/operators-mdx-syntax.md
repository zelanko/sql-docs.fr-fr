---
description: Opérateurs (syntaxe MDX)
title: Opérateurs (syntaxe MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3d52751978dbe2973ecab9506094fad6a6f6c29a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471771"
---
# <a name="operators-mdx-syntax"></a>Opérateurs (syntaxe MDX)


  Dans la syntaxe MDX (Multidimensional Expressions), les opérateurs permettent d'exécuter les actions suivantes :  
  
-   Modifier des données, soit définitivement, soit temporairement.  
  
-   Chercher des valeurs ou des objets selon un critère de recherche.  
  
-   Implémenter une décision entre des valeurs ou des expressions.  
  
-   Tester des conditions précises avant de commencer ou de valider une transaction, ou avant d'exécuter des instructions spécifiques.  
  
 MDX prend en charge les opérateurs répertoriés dans le tableau suivant :  
  
|Si vous devez effectuer ce type d'opération|Utilisation|  
|---------------------------------------|---------|  
|Affecter une valeur à une variable ou associer une colonne de jeu de résultats à un alias|[Opérateurs d’assignation](../mdx/assignment-operators.md)|  
|Addition, soustraction, multiplication, division.|[Opérateurs arithmétiques](../mdx/arithmetic-operators.md)|  
|Tester une condition telle que AND, OR, NOT et XOR.|[Opérateurs au niveau du bit](../mdx/bitwise-operators.md)|  
|Comparer une valeur à une autre ou à une expression|[Opérateurs de comparaison](../mdx/comparison-operators.md)|  
|Combiner deux chaînes en une de façon permanente ou temporaire.|[Opérateurs de concaténation](../mdx/concatenation-operators.md)|  
|Combiner deux expressions d'ensemble en une de façon permanente ou temporaire.|[Opérateurs de jeu](../mdx/set-operators.md)|  
|Exécute une opération sur un opérande.|[Opérateurs unaires](../mdx/unary-operators.md)|  
  
> [!NOTE]  
>  Dans les requêtes, toute personne qui peut voir les données d'un cube devant être utilisé avec un certain type d'opérateur peut effectuer des opérations. Cependant, vous avez besoin des droits adéquats pour de pouvoir modifier les données.  
  
 Si vous utilisez plusieurs opérateurs, l'ordre dans lequel la syntaxe MDX les évalue est important. De même, l'utilisateur des opérateurs peut exiger la conversion d'un type de données en un autre avant que les opérateurs puissent être évalués.  
  
## <a name="evaluating-complex-expressions"></a>Évaluation d'expressions complexes  
 Vous pouvez créer une expression en utilisant des opérateurs pour combiner plusieurs expressions plus petites. Dans ces expressions complexes, MDX évalue les opérateurs dans l’ordre selon la définition de la priorité des opérateurs utilisée par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . MDX effectue des opérateurs avec une priorité plus élevée avant d’effectuer des opérateurs avec une priorité plus faible.  
  
### <a name="understanding-operator-precedence"></a>Description de la priorité des opérateurs  
 La liste suivante présente les opérateurs par ordre de priorité décroissant. Les opérateurs contenus dans la même ligne ont une priorité équivalente et sont évalués de gauche à droite sauf contrainte due à la présence de parenthèses :  
  
-   IS  
  
-   AS  
  
-   DISTINCT  
  
-   :  
  
-   ^  
  
-   /, *  
  
-   +, -  
  
-   EXISTING  
  
-   <>, >=, =, \<=, > , <  
  
-   NOT  
  
-   AND  
  
-   XOR  
  
-   OR  
  
 Pour plus d’informations sur les opérateurs dans MDX, consultez [référence des opérateurs mdx &#40;mdx&#41;](../mdx/mdx-operator-reference-mdx.md).  
  
### <a name="determining-results"></a>Détermination de résultats  
 Lorsque vous combinez des expressions simples pour constituer une expression complexe, les règles des opérateurs combinées à celles de priorité des types de données déterminent le type de données de la valeur obtenue.  
  
 Si le résultat est un caractère ou une valeur Unicode, les règles des opérateurs combinées à celles de la priorité de classement déterminent le classement du résultat. Pour plus d’informations sur les classements, consultez [langues et classements &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/languages-and-collations-analysis-services).  
  
 Il existe également des règles pour déterminer la précision, l’échelle et la longueur du résultat basées sur la précision, l’échelle et la longueur des expressions simples.  
  
## <a name="converting-data-types"></a>Conversion des types de données  
 La syntaxe MDX convertit un objet en un autre type lorsqu'il est utilisé dans une expression qui exige un type différent. Le tableau suivant définit les règles de conversion de chaque objet.  
  
|Type d'origine|Type exigé|Conversion|  
|-------------------|-----------------|----------------|  
|Level|Définissez|\<level>. membres|  
|Hierarchy|Membre|\<hierarchy>. DefaultMember|  
|Membre|Tuple|(\<Member>)|  
|Tuple|Membre|\<tuple>. Item (0)|  
|Tuple|Scalaire|\<tuple>. valeur|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;&#41;MDX ](../mdx/mdx-operator-reference-mdx.md)   
 [Éléments de la syntaxe MDX &#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
