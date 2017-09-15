---
title: Commande exacte SET | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SET EXACT command [ODBC]
ms.assetid: 9533d3e0-e7c1-49de-a3a3-0cc4373a91cb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c94efa07d23249c9fc3e9d661998419b68f7b624
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="set-exact-command"></a>Commande exacte de jeu
Spécifie les règles de comparaison de deux chaînes de longueurs différentes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Arguments  
 ON  
 Spécifie que les expressions doivent correspondre au caractère équivalentes. Les espaces de fin dans les expressions sont ignorés pour la comparaison. Pour la comparaison, la plus courte des deux expressions est complétée à droite par des espaces pour correspondre à la longueur de l’expression la plus longue.  
  
 OFF  
 (Par défaut). Spécifie que, pour être équivalents, expressions doivent correspondre au caractère jusqu'à la fin de l’expression située à droite.  
  
## <a name="remarks"></a>Notes  
 Le paramètre SET EXACT n’a aucun effet si les deux chaînes sont de même longueur.  
  
## <a name="string-comparisons"></a>Comparaisons de chaînes  
 Visual FoxPro comporte deux opérateurs relationnels qui teste l’égalité.  
  
 Le = opérateur effectue une comparaison entre deux valeurs du même type. Cet opérateur est adapté pour la comparaison de caractère, numérique, date et données logiques.  
  
 Toutefois, lorsque vous comparez des expressions de caractères avec l’opérateur =, les résultats peut-être pas exactement à vos attentes. Expressions de caractères sont comparées caractère pour le caractère de gauche à droite jusqu'à ce que l’une des expressions n’est pas égale à l’autre, jusqu'à la fin de l’expression située à droite de la = opérateur est atteinte (SET EXACT OFF), ou jusqu'à la fin de toutes les expressions est (SET EXACT ON).  
  
 Le == opérateur peut être utilisé lorsqu’une comparaison exacte des données de caractères est nécessaire. Si deux expressions de caractères sont comparées avec le ==, opérateur, les expressions des deux côtés de la == opérateur doit contenir exactement les mêmes caractères, y compris les espaces, pour être considérées comme égales. Le paramètre SET EXACT est ignoré lors de la comparaison des chaînes de caractères à l’aide de ==.  
  
 Le tableau suivant montre comment le choix de l’opérateur et le paramètre SET EXACT affectent les comparaisons. (Un trait de soulignement représente un espace.)  
  
|Comparaison|= EXACT OFF|= EXACTE SUR|== EXACT ON ou OFF|  
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
 [Commande SET ANSI](../../odbc/microsoft/set-ansi-command.md)
