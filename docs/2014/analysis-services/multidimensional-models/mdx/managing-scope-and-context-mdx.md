---
title: Gestion de la portée et du contexte (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], context
- scope [MDX]
- CALCULATE statement
- This function [MDX]
- SCOPE statement
- scripts [MDX], scope
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bec0dc51a4f91ba4ca8f71a0a3caba387d37bf1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074643"
---
# <a name="managing-scope-and-context-mdx"></a>Gestion de la portée et du contexte (MDX)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], un script MDX (Multidimensional Expressions) peut s’appliquer à l’intégralité du cube ou à des portions spécifiques du cube, à des points spécifiques de l’exécution du script. Le script MDX peut opter pour approche par couche des calculs au sein d'un cube à l'aide de tests de calcul.  
  
> [!NOTE]  
>  Pour plus d’informations sur la manière dont les tests de calcul peuvent affecter les calculs, consultez [Présentation des concepts d’ordre de passage et d’ordre de résolution &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
 Pour contrôler le test de calcul, la portée et le contexte au sein d'un script MDX, vous devez utiliser en particulier l'instruction CACULATE, la fonction `This` et l'instruction SCOPE.  
  
## <a name="using-the-calculate-statement"></a>Utilisation de l'instruction CALCULATE  
 L'instruction CALCULATE remplit chaque cellule du cube avec des données agrégées. Par exemple, une instruction CALCULATE unique se situe au début du script MDX par défaut.  
  
 Pour plus d’informations sur la syntaxe de l’instruction CALCULATE, consultez [Instruction CALCULATE &#40;MDX&#41;](/sql/mdx/mdx-scripting-calculate).  
  
> [!NOTE]  
>  Si le script contient une instruction SCOPE comprenant une instruction CALCULATE, la syntaxe MDX évalue cette dernière au sein du contexte du sous-cube défini par l'instruction SCOPE, et non sur l'intégralité du cube.  
  
## <a name="using-the-this-function"></a>Utilisation de la fonction This  
 La fonction `This` permet de récupérer le sous-cube actuel au sein d'un script MDX. Vous pouvez utiliser la fonction `This` pour affecter rapidement une expression MDX comme valeur aux cellules du sous-cube actuel. La plupart du temps, la fonction `This` est utilisée conjointement avec l'instruction SCOPE pour modifier le contenu d'un sous-cube particulier pendant un test de calcul spécifique.  
  
> [!NOTE]  
>  Si le script contient une instruction SCOPE comprenant une fonction `This`, la syntaxe MDX évalue la fonction `This` au sein du contexte du sous-cube défini par l'instruction SCOPE, et non sur l'intégralité du cube.  
  
### <a name="this-function-example"></a>Exemple de fonction This  
 L'exemple de commande de script MDX suivant utilise la fonction `This` pour augmenter de 10 % la valeur de la mesure Amount, dans le groupe de mesures Finance de l'exemple de cube [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)], pour les enfants du membre Redmond de la dimension Customer :  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 Pour plus d’informations sur la syntaxe de `This` la fonction, consultez [cet &#40;&#41;MDX ](/sql/mdx/this-mdx).  
  
## <a name="using-the-scope-statement"></a>Utilisation de l'instruction SCOPE  
 L'instruction SCOPE définit le sous-cube actuel qui contient (et spécifie la portée) d'autres expressions et instructions MDX au sein d'un script MDX. MDX évalue ces autres expressions et instructions MDX, notamment la fonction `This` et l'instruction CALCULATE, dans le contexte du sous-cube.  
  
 Une instruction SCOPE est dynamique, mais pas itérative de nature. Les instructions contenues dans une instruction SCOPE s'exécutent à une seule reprise, mais le sous-cube proprement dit peut être déterminé de manière dynamique. Vous pouvez, par exemple, posséder un cube appelé SampleCube et appliquer à ce dernier l'instruction SCOPE suivante pour définir un sous-cube définissant le contexte en tant que ALLMEMBERS dans la dimension Measures :  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 Les instructions et expressions contenues dans cette instruction SCOPE s'exécutent à une seule reprise.  
  
 À présent, un utilisateur de l'entreprise exécute la requête suivante contenant une mesure, appelée ExistingMeasure, sur le cube SampleCube :  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 Le jeu de cellules retourné par la requête ressemble au résultat affiché dans le tableau suivant.  
  
||[ExistingMeasure]|[NewMeasure]|  
|-|-------------------------|--------------------|  
|[Customer].[All]|2|2|  
  
 Si vous observez le jeu de cellules retourné, vous pouvez constater que la valeur ExistingMeasure, comprise dans l'instruction SCOPE du script MDX, est mise à jour dynamiquement après la définition de la mesure NewMeasure.  
  
 Une instruction SCOPE peut être imbriquée dans une autre instruction SCOPE. Cependant, comme l'instruction SCOPE n'est pas itérative, l'objectif principal de l'imbrication d'instructions SCOPE consiste à sous-diviser davantage un sous-cube en vue d'un traitement spécial.  
  
### <a name="scope-statement-example"></a>Exemple d'instruction SCOPE  
 L'exemple de script MDX suivant utilise l'instruction SCOPE pour augmenter de 10 % la valeur de la mesure Amount, dans le groupe de mesures Finance de l'exemple de cube [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] , pour les enfants du membre Redmond de la dimension Customer. Cependant, une autre instruction SCOPE modifie le sous-cube pour inclure la mesure Amount des enfants de l'année civile 2002. Pour terminer, la mesure Amount n'est agrégée que pour ce sous-cube, en laissant inchangées les valeurs agrégées de la mesure Amount pour les autres années civiles.  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 Pour plus d’informations sur la syntaxe de l’instruction SCOPE, consultez [Instruction SCOPE &#40;MDX&#41;](/sql/mdx/mdx-scripting-scope).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage MDX &#40;&#41;MDX](/sql/mdx/mdx-language-reference-mdx)   
 [Script MDX de base &#40;&#41;MDX](the-basic-mdx-script-mdx.md)   
 [Notions de base des requêtes MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
