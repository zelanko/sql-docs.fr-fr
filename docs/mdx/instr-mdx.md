---
description: InStr (MDX)
title: InStr (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 877fc4658081108e810e404dfc8d4a368c6964ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387355"
---
# <a name="instr-mdx"></a>InStr (MDX)


  Retourne la position de la première occurrence d'une chaîne dans une autre chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
InStr([start, ]searched_string, search_string[, compare])  
```  
  
## <a name="arguments"></a>Arguments  
 *start*  
 (Facultatif) Expression numérique qui définit la position de début de chaque recherche. Si cette valeur est omise, la recherche démarre au niveau du premier caractère. Si start est Null, la valeur de retour de fonction n'est pas définie.  
  
 *searched_string*  
 Expression de chaîne à rechercher.  
  
 *search_string*  
 Expression de chaîne à rechercher.  
  
 *Compare*  
 (facultatif) Valeur entière. Cet argument est toujours ignoré. Elle est définie pour la compatibilité avec d’autres fonctions **InStr** dans d’autres langages.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur entière avec la position de départ de *Chaîne2* dans *Chaîne1*.  
  
 En outre, la fonction **InStr** retourne les valeurs indiquées dans le tableau suivant en fonction de la condition :  
  
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
>  **InStr** effectue toujours une comparaison qui ne respecte pas la casse.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la fonction **InStr** et affiche des scénarios de résultats différents.  
  
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
  
|Champ dans les mesures|Résultats|  
|-|-|  
|minuscules trouvées dans la chaîne en minuscules|16|  
|majuscules trouvées dans la chaîne en minuscules|16|  
|la chaîne de recherche est vide|0|  
|la chaîne de recherche est Null|Non défini|  
|la chaîne de recherche est vide|1|  
|la chaîne de recherche est start 10 vide|10|  
|la chaîne de recherche est null|Non défini|  
|trouvé à partir de start 10|16|  
|introuvable à partir de start 17|0|  
|start Null|Non défini|  
|start est supérieur à la longueur recherchée|0|  
  
  
