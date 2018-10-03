---
title: SET EXACT, commande | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 16651df836ac3fb87c5e28b4b8fa25088e9dd86a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47606798"
---
# <a name="set-exact-command"></a>SET EXACT, commande
Spécifie les règles de comparaison de deux chaînes de longueurs différentes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 Spécifie que les expressions doivent correspondre au caractère équivalent. Les espaces de fin dans les expressions sont ignorés pour la comparaison. Pour la comparaison, la plus courte des deux expressions est complétée à droite avec des espaces pour correspondre à la longueur de l’expression plus longue.  
  
 OFF  
 (Valeur par défaut). Spécifie que, comme équivalents, expressions doivent correspondre au caractère jusqu'à la fin de l’expression située à droite.  
  
## <a name="remarks"></a>Notes  
 Le paramètre SET EXACT n’a aucun effet si les deux chaînes ont la même longueur.  
  
## <a name="string-comparisons"></a>Comparaisons de chaînes  
 Visual FoxPro a deux opérateurs relationnels qui testent l’égalité.  
  
 Le = opérateur effectue une comparaison entre deux valeurs du même type. Cet opérateur est adapté pour la comparaison de caractère, numérique, date et données logiques.  
  
 Toutefois, lorsque vous comparez des expressions de caractères avec l’opérateur =, les résultats peut-être pas exactement ce que vous attendez. Expressions de caractères sont comparées caractère pour caractère de gauche à droite jusqu'à ce que l’une des expressions n’est pas égale à l’autre, jusqu'à la fin de l’expression sur le côté droit de la = opérateur est atteinte (SET EXACT OFF), ou jusqu'à ce que les terminaisons des deux expressions sont atteinte (SET EXACT ON).  
  
 Le == opérateur peut être utilisé lorsqu’une comparaison exacte des données de caractères est nécessaire. Si deux expressions de caractères sont comparées avec l’opérateur ==, les expressions des deux côtés de la == opérateur doit contenir exactement les mêmes caractères, y compris les espaces, pour être considérées comme égales. Le paramètre SET EXACT est ignoré lors de la comparaison des chaînes de caractères à l’aide de ==.  
  
 Le tableau suivant montre comment le choix de l’opérateur et le paramètre SET EXACT affectent les comparaisons. (Un trait de soulignement représente un espace blanc.)  
  
|Comparaison|= EXACT OFF|= EXACT SUR|== EXACTE ON ou OFF|  
|----------------|------------------|-----------------|--------------------------|  
|« abc » = « abc »|Correspondance|Correspondance|Correspondance|  
|« ab » = « abc »|Aucune correspondance|Aucune correspondance|Aucune correspondance|  
|« abc » = « ab »|Correspondance|Aucune correspondance|Aucune correspondance|  
|« abc » = « ab_ »|Aucune correspondance|Aucune correspondance|Aucune correspondance|  
|« ab » = « ab_ »|Aucune correspondance|Correspondance|Aucune correspondance|  
|« ab_ » = « ab »|Correspondance|Correspondance|Aucune correspondance|  
|« » = « ab »|Aucune correspondance|Aucune correspondance|Aucune correspondance|  
|« ab » = « »|Correspondance|Aucune correspondance|Aucune correspondance|  
|"__" = ""|Correspondance|Correspondance|Aucune correspondance|  
|"" = "___"|Aucune correspondance|Correspondance|Aucune correspondance|  
|TRIM("___") = « »|Correspondance|Correspondance|Correspondance|  
|« « = TRIM("___")|Correspondance|Correspondance|Correspondance|  
  
## <a name="see-also"></a>Voir aussi  
 [SET ANSI, commande](../../odbc/microsoft/set-ansi-command.md)
