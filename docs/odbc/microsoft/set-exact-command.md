---
title: DÉFINIR la commande exacte | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 686ecc89f44bac4b219b760e55160f451a15c503
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997727"
---
# <a name="set-exact-command"></a>SET EXACT, commande
Spécifie les règles de comparaison de deux chaînes de longueurs différentes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ACTIVÉ  
 Spécifie que les expressions doivent correspondre au caractère pour que le caractère soit équivalent. Les espaces à droite dans les expressions sont ignorés pour la comparaison. Pour la comparaison, le plus petit des deux expressions est rempli à droite avec des espaces pour correspondre à la longueur de l’expression la plus longue.  
  
 OFF  
 (Par défaut.) Spécifie que, pour être équivalent, les expressions doivent correspondre au caractère pour le caractère jusqu’à ce que la fin de l’expression sur le côté droit soit atteinte.  
  
## <a name="remarks"></a>Notes  
 Le paramètre SET EXACT n’a aucun effet si les deux chaînes ont la même longueur.  
  
## <a name="string-comparisons"></a>Comparaisons de chaînes  
 Visual FoxPro a deux opérateurs relationnels qui testent l’égalité.  
  
 L’opérateur = effectue une comparaison entre deux valeurs du même type. Cet opérateur est adapté à la comparaison de données de type caractère, numérique, date et logique.  
  
 Toutefois, lorsque vous comparez des expressions de caractères à l’opérateur =, les résultats peuvent ne pas être exactement ce que vous attendez. Les expressions de caractères sont des caractères comparés pour les caractères de gauche à droite jusqu’à ce que l’une des expressions ne soit pas égale à l’autre, jusqu’à ce que la fin de l’expression à droite de l’opérateur = soit atteinte (définissez la valeur EXACT OFF) ou jusqu’à ce que les deux extrémités des expressions soient atteint (définissez EXACT ON).  
  
 L’opérateur « = = » peut être utilisé lorsqu’une comparaison exacte de données caractères est nécessaire. Si deux expressions de caractères sont comparées à l’opérateur = =, les expressions des deux côtés de l’opérateur = = doivent contenir exactement les mêmes caractères, y compris les espaces, pour être considérés comme égaux. Le paramètre SET EXACT est ignoré lorsque les chaînes de caractères sont comparées à l’aide de = =.  
  
 Le tableau suivant montre comment le choix de l’opérateur et le paramètre SET EXACT affectent les comparaisons. (Un trait de soulignement représente un espace vide.)  
  
|Comparaison|= EXACT|= EXACT LE|= = ON ou OFF EXACT|  
|----------------|------------------|-----------------|--------------------------|  
|« ABC » = « ABC »|Correspond|Correspond|Correspond|  
|"AB" = "ABC"|Aucune correspondance|Aucune correspondance|Aucune correspondance|  
|"ABC" = "AB"|Correspond|Aucune correspondance|Aucune correspondance|  
|"ABC" = "ab_"|Aucune correspondance|Aucune correspondance|Aucune correspondance|  
|"AB" = "ab_"|Aucune correspondance|Correspond|Aucune correspondance|  
|"ab_" = "AB"|Correspond|Correspond|Aucune correspondance|  
|"" = "AB"|Aucune correspondance|Aucune correspondance|Aucune correspondance|  
|"AB" = ""|Correspond|Aucune correspondance|Aucune correspondance|  
|"__" = ""|Correspond|Correspond|Aucune correspondance|  
|"" = "___"|Aucune correspondance|Correspond|Aucune correspondance|  
|TRIM ("___") = ""|Correspond|Correspond|Correspond|  
|"" = TRIM ("___")|Correspond|Correspond|Correspond|  
  
## <a name="see-also"></a>Voir aussi  
 [SET ANSI, commande](../../odbc/microsoft/set-ansi-command.md)
