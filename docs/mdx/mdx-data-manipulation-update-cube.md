---
title: Instruction UPDATE CUBE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f52dd59b67b42ad430df9bb1e9d00dce7ad6d697
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68003529"
---
# <a name="mdx-data-manipulation---update-cube"></a>Manipulation de données MDX - UPDATE CUBE


  L'instruction UPDATE CUBE est utilisée pour l'écriture différée des données dans une cellule d'un cube qui agrège uniquement dans son parent à l'aide de l'agrégation SUM. Pour obtenir plus d’explications et un exemple, consultez la rubrique « Présentation des allocations » dans ce billet de blog : [création d’une application d’écriture différée avec Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UPDATE [ CUBE ] Cube_Name   
   SET   
            <update clause>   
           [, <update clause> ...n ]  
  
<update clause> ::=   
      Tuple_Expression[.VALUE]= New_Value  
      [   
        USE_EQUAL_ALLOCATION   
        | USE_EQUAL_INCREMENT   
        | USE_WEIGHTED_ALLOCATION [ BY Weight_Expression]   
        | USE_WEIGHTED_INCREMENT [ BY Weight_Expression]  
      ]  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Chaîne valide qui fournit le nom d’un cube.  
  
 *Tuple_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un tuple.  
  
 *New_Value*  
 Expression numérique valide.  
  
 *Weight_Expression*  
 Expression numérique MDX (Multidimensional Expressions) valide qui retourne une valeur décimale comprise entre 0 et 1.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez mettre à jour la valeur d'une cellule feuille ou non-feuille d'un cube, et allouer inévitablement la valeur d'une cellule non-feuille spécifiée à toutes les cellules feuilles dépendantes. La cellule spécifiée par l'expression de tuple peut être n'importe quelle cellule valide dans l'espace multidimensionnel (ce qui signifie que la cellule ne dispose d'aucune cellule feuille). Toutefois, la cellule doit être agrégée avec la fonction d’agrégation [Sum](../mdx/sum-mdx.md) et ne doit pas inclure un membre calculé dans le tuple utilisé pour identifier la cellule.  
  
 Il peut être utile de considérer l’instruction **Update cube** comme une sous-routine qui génère automatiquement une série d’opérations d’écriture différée de cellule individuelles dans des cellules feuilles et non-feuilles qui se cumulent dans une somme spécifiée.  
  
 Vous trouverez ci-dessous une description des méthodes d’allocation.  
  
 **USE_EQUAL_ALLOCATION :** Chaque cellule feuille qui contribue à la cellule mise à jour reçoit une valeur égale en fonction de l’expression suivante.  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT :** Chaque cellule feuille qui contribue à la cellule mise à jour est modifiée en fonction de l’expression suivante.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION :** Chaque cellule feuille qui contribue à la cellule mise à jour reçoit une valeur égale qui est basée sur l’expression suivante.  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT :** Chaque cellule feuille qui contribue à la cellule mise à jour est modifiée en fonction de l’expression suivante.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Si aucune expression de pondération n’est spécifiée, l’instruction **Update cube** utilise implicitement l’expression suivante.  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Une expression de poids doit être exprimée sous forme de valeur décimale comprise entre zéro (0) et 1. Cette valeur spécifie le ratio de la valeur allouée que vous voulez affecter aux cellules feuilles affectées par l'allocation. Il est de la responsabilité du programmeur de l'application cliente de créer des expressions dont les valeurs agrégées de cumul seront égales à la valeur allouée de l'expression.  
  
> [!CAUTION]  
>  L'application cliente doit considérer simultanément l'allocation de toutes les dimensions afin d'éviter l'éventualité de résultats imprévus, notamment des valeurs de cumul incorrectes ou des données incohérentes.  
  
 Chaque allocation de **cube de mise à jour** doit être considérée comme atomique à des fins transactionnelles. Ceci signifie que si l'une des opérations d'allocation échoue pour quelque raison que ce soit, par exemple une erreur de formule ou une violation de sécurité, l'ensemble de l'opération UPDATE CUBE échouera. Avant le calcul des opérations individuelles d'allocation, un instantané des données est réalisé pour garantir la correction des calculs résultants.  
  
> [!CAUTION]  
>  Lorsqu'elle est utilisée sur une mesure contenant des entiers, la méthode USE_WEIGHTED_ALLOCATION peut retourner des résultats imprécis causés par des arrondis successifs.  
  
> [!IMPORTANT]  
>  Quand les cellules mises à jour ne se chevauchent pas, la propriété de chaîne de connexion **Update Isolation Level** peut être utilisée pour améliorer les performances pour UPDATE CUBE.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [Instructions de manipulation de données MDX &#40;&#41;MDX](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
