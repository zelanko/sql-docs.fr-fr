---
title: Set EXACT Commande (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXACT command [ODBC]
ms.assetid: 9533d3e0-e7c1-49de-a3a3-0cc4373a91cb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e754fff35b6b948ac63d19361067b2d65a07fdd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300869"
---
# <a name="set-exact-command"></a>SET EXACT, commande
Spécifie les règles pour comparer deux chaînes de longueurs différentes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 Spécifie que les expressions doivent correspondre au caractère pour que le caractère soit équivalent. Tous les blancs de fuite dans les expressions sont ignorés pour la comparaison. Pour la comparaison, le plus court des deux expressions est rembourré sur la droite avec des blancs pour correspondre à la longueur de l’expression plus longue.  
  
 OFF  
 (Par défaut.) Précise que, pour être équivalent, les expressions doivent correspondre caractère pour le caractère jusqu’à ce que la fin de l’expression sur le côté droit est atteint.  
  
## <a name="remarks"></a>Notes  
 Le paramètre SET EXACT n’a aucun effet si les deux cordes sont de la même longueur.  
  
## <a name="string-comparisons"></a>Comparaisons de cordes  
 Visual FoxPro a deux opérateurs relationnels qui testent pour l’égalité.  
  
 L’opérateur effectue une comparaison entre deux valeurs du même type. Cet opérateur est adapté pour comparer le caractère, le numérique, la date et les données logiques.  
  
 Toutefois, lorsque vous comparez les expressions de caractère avec l’opérateur, les résultats pourraient ne pas être exactement ce que vous attendez. Les expressions de caractère sont comparées caractère pour le caractère de gauche à droite jusqu’à ce que l’une des expressions n’est pas égale à l’autre, jusqu’à ce que la fin de l’expression sur le côté droit de l’opérateur est atteint (SET EXACT OFF), ou jusqu’à ce que les extrémités des deux expressions sont atteintes (SET EXACT ON).  
  
 L’opérateur peut être utilisé lorsqu’une comparaison exacte des données de caractère est nécessaire. Si deux expressions de caractère sont comparées à l’opérateur, les expressions des deux côtés de l’opérateur doivent contenir exactement les mêmes caractères, y compris les blancs, pour être considérées comme égales. Le paramètre SET EXACT est ignoré lorsque les chaînes de caractères sont comparées à l’aide de l’utilisation de l’utilisation de l’utilisation de l’utilisation de l’AD.  
  
 Le tableau suivant montre comment le choix de l’opérateur et le paramètre SET EXACT affectent les comparaisons. (Un soulignement représente un espace vide.)  
  
|Comparaison|- EXACT OFF|EXACT SUR|EXACT ON OU OFF|  
|----------------|------------------|-----------------|--------------------------|  
|"abc" - "abc"|Correspond|Correspond|Correspond|  
|"ab" et "abc"|Pas de correspondance|Pas de correspondance|Pas de correspondance|  
|"abc" - "ab"|Correspond|Pas de correspondance|Pas de correspondance|  
|"abc" - "ab_"|Pas de correspondance|Pas de correspondance|Pas de correspondance|  
|"ab" et "ab_"|Pas de correspondance|Correspond|Pas de correspondance|  
|"ab_" et "ab"|Correspond|Correspond|Pas de correspondance|  
|"" et "ab"|Pas de correspondance|Pas de correspondance|Pas de correspondance|  
|"ab" - ""|Correspond|Pas de correspondance|Pas de correspondance|  
|"__" = ""|Correspond|Correspond|Pas de correspondance|  
|"" = "___"|Pas de correspondance|Correspond|Pas de correspondance|  
|TRIM (")|Correspond|Correspond|Correspond|  
|"" et garnitures (")|Correspond|Correspond|Correspond|  
  
## <a name="see-also"></a>Voir aussi  
 [SET ANSI, commande](../../odbc/microsoft/set-ansi-command.md)
