---
title: InStr (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5638c358-47da-40ad-b988-1a5214c05492
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7a6b5a1a987662fbe4ec0bcab4241ac0d6ff3109
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="instr-mdx"></a>InStr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la position de la première occurrence d'une chaîne dans une autre chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
InStr([start, ]searched_string, search_string[, compare])  
```  
  
## <a name="arguments"></a>Arguments  
 *Démarrer*  
 (Facultatif) Expression numérique qui définit la position de début de chaque recherche. Si cette valeur est omise, la recherche démarre au niveau du premier caractère. Si start est Null, la valeur de retour de fonction n'est pas définie.  
  
 *searched_string*  
 L’expression de chaîne à rechercher.  
  
 *search_string*  
 Expression de chaîne à rechercher.  
  
 *Comparer*  
 (facultatif) Valeur entière. Cet argument est toujours ignoré. Il est défini pour la compatibilité avec d’autres **Instr** fonctions dans d’autres langages.  
  
## <a name="return-value"></a>Valeur retournée  
 Une valeur entière avec la position de départ de *chaîne2* dans *String1*.  
  
 En outre, **InStr** fonction retourne les valeurs répertoriées dans le tableau suivant en fonction de la condition :  
  
|Condition|Valeur retournée|  
|---------------|------------------|  
|String1 est de longueur nulle|zéro (0)|  
|String1 a la valeur null|non défini|  
|String2 est de longueur nulle|start|  
|String2 a la valeur null|non défini|  
|String2 est introuvable|zéro (0)|  
|start est supérieur à Len(String2)|zéro (0)|  
  
## <a name="remarks"></a>Notes   
  
> [!WARNING]  
>  **InStr** effectue toujours une comparaison respectant la casse.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant illustre l’utilisation de la **Instr** fonction et affiche différents scénarios de résultat.  
  
```  
with   
    member [Date].[Date].[Results] as "Results"  
    member measures.[lowercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[uppercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "O")  
    member measures.[searched string is empty]            as InStr( "", "o")  
    member measures.[searched string is null]             as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[search string is empty]              as InStr( "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is empty start 10]     as InStr(10, "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is null]               as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[found from start 10]                 as InStr( 10, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NOT found from start 17]             as InStr( 17, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NULL start]                          as iif(IsError(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Error", iif(IsNull(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Null","Is undefined"))  
    member measures.[start greater than searched length]  as InStr( 170, "abcdefghijklmnñopqrstuvwxyz", "o")  
  
select  [Results] on columns,  
       { measures.[lowercase found in lowercase string]  
       , measures.[uppercase found in lowercase string]  
       , measures.[searched string is empty]  
       , measures.[searched string is null]  
       , measures.[search string is empty]  
       , measures.[search string is empty start 10]  
       , measures.[search string is null]  
       , measures.[found from start 10]  
       , measures.[NOT found from start 17]  
       , measures.[NULL start]   
       , measures.[start greater than searched length]  
       } on rows  
  
from [Adventure Works]  
```  
  
 Le tableau suivant présente les résultats obtenus.  
  
|||  
|-|-|  
||Résultats|  
|minuscules trouvées dans la chaîne en minuscules|16|  
|majuscules trouvées dans la chaîne en minuscules|16|  
|la chaîne de recherche est vide|0|  
|la chaîne de recherche est Null|Non défini|  
|chaîne de recherche est vide| 1|  
|la chaîne de recherche est start 10 vide|10|  
|chaîne de recherche a la valeur null|Non défini|  
|trouvé à partir de start 10|16|  
|introuvable à partir de start 17|0|  
|start Null|Non défini|  
|start est supérieur à la longueur recherchée|0|  
  
  
