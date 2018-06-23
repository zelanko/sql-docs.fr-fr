---
title: Fonctions (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- functions [Integration Services]
- expressions [Integration Services], functions
- string functions
- SQL Server Integration Services, functions
- SSIS, functions
ms.assetid: e9a41a31-94f4-46a4-b737-c707dd59ce48
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 65c272c738877eef0d8f931c7ed3a9262eeeae72
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051566"
---
# <a name="functions-ssis-expression"></a>Fonctions (expression SSIS)
  Le langage d'expression comprend un ensemble de fonctions utilisables dans les expressions. Une expression peut utiliser une seule fonction mais, en règle générale, elle combine des fonctions avec des opérateurs et utilise plusieurs fonctions.  
  
 Les fonctions peuvent être classées selon les regroupements suivants :  
  
-   les fonctions mathématiques, qui effectuent des calculs à partir de valeurs d'entrée numériques fournies en tant que paramètres et qui renvoient des valeurs numériques ;  
  
-   les fonctions de chaîne, qui effectuent des opérations sur des valeurs d'entrée hexadécimales ou de chaîne et qui renvoient une valeur numérique ou de chaîne ;  
  
-   les fonctions de date et d'heure, qui effectuent des opérations sur des valeurs de date et d'heure et qui renvoient des valeurs numériques, de chaîne ou de date et d'heure ;  
  
-   les fonctions système, qui renvoient des informations sur une expression.  
  
 Le langage d'expression dispose des fonctions mathématiques suivantes.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[ABS &#40;Expression SSIS&#41;](abs-ssis-expression.md)|Renvoie la valeur absolue d'une expression numérique.|  
|[EXP &#40;Expression SSIS&#41;](exp-ssis-expression.md)|Renvoie l'exposant de base e de l'expression spécifiée.|  
|[PLAFOND &#40;Expression SSIS&#41;](ceiling-ssis-expression.md)|Renvoie le plus petit entier qui est supérieur ou égal à une expression numérique.|  
|[FLOOR &#40;Expression SSIS&#41;](floor-ssis-expression.md)|Renvoie l'entier le plus élevé inférieur ou égal à une expression numérique.|  
|[LN &#40;Expression SSIS&#41;](ln-ssis-expression.md)|Renvoie le logarithme népérien d'une expression numérique.|  
|[JOURNAL &#40;Expression SSIS&#41;](log-ssis-expression.md)|Renvoie le logarithme de base 10 d'une expression numérique.|  
|[ALIMENTATION &#40;Expression SSIS&#41;](power-ssis-expression.md)|Renvoie le résultat de l'élévation d'une expression numérique à une puissance donnée.|  
|[ROUND &#40;Expression SSIS&#41;](round-ssis-expression.md)|Renvoie une expression numérique, arrondie à la longueur ou à la précision indiquée. .|  
|[SIGNE &#40;Expression SSIS&#41;](sign-ssis-expression.md)|Renvoie le signe positif (+), négatif (-) ou zéro (0) d'une expression numérique.|  
|[CARRÉ &#40;Expression SSIS&#41;](square-ssis-expression.md)|Renvoie le carré d'une expression numérique.|  
|[SQRT &#40;Expression SSIS&#41;](sqrt-ssis-expression.md)|Renvoie la racine carrée d'une expression numérique.|  
  
 L'évaluateur d'expression dispose des fonctions de chaîne suivantes.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[CODEPOINT &#40;Expression SSIS&#41;](codepoint-ssis-expression.md)|Renvoie la valeur du code Unicode du caractère placé à l'extrême gauche d'une expression de caractères.|  
|[FINDSTRING &#40;Expression SSIS&#41;](findstring-ssis-expression.md)|Renvoie l'index de base un de l'occurrence spécifiée d'une chaîne de caractères dans une expression.|  
|[HEX &#40;Expression SSIS&#41;](hex-ssis-expression.md)|Renvoie une chaîne représentant la valeur hexadécimale d'un entier.|  
|[LEN &#40;Expression SSIS&#41;](len-ssis-expression.md)|Renvoie le nombre de caractères d'une expression de caractères.|  
|[GAUCHE &#40;Expression SSIS&#41;](left-ssis-expression.md)|Renvoie le nombre de caractères spécifié en commençant par la partie la plus à gauche d'une expression de caractères donnée.|  
|[INFÉRIEUR &#40;Expression SSIS&#41;](lower-ssis-expression.md)|Renvoie une expression de caractères après avoir transformé les caractères majuscules en caractères minuscules.|  
|[LTRIM &#40;Expression SSIS&#41;](trim-ssis-expression.md)|Renvoie une chaîne de caractères après avoir supprimé les espaces de début.|  
|[Remplacez &#40;Expression SSIS&#41;](replace-ssis-expression.md)|Renvoie une expression de caractères après le remplacement d'une chaîne située dans l'expression par une autre chaîne ou une chaîne vide.|  
|[RÉPLIQUER &#40;Expression SSIS&#41;](replicate-ssis-expression.md)|Renvoie une expression de caractères, répliquée un nombre de fois spécifié.|  
|[Inverser &#40;Expression SSIS&#41;](reverse-ssis-expression.md)|Renvoie une expression de caractères en ordre inverse.|  
|[DROIT &#40;Expression SSIS&#41;](right-ssis-expression.md)|Renvoie le nombre de caractères spécifié en commençant par la partie la plus à droite d'une expression de caractères donnée.|  
|[La fonction RTRIM &#40;Expression SSIS&#41;](rtrim-ssis-expression.md)|Renvoie une chaîne de caractères après la suppression des espaces de fin.|  
|[SOUS-chaîne &#40;Expression SSIS&#41;](substring-ssis-expression.md)|Renvoie une partie d'une expression de type caractère.|  
|[TRIM &#40;Expression SSIS&#41;](trim-ssis-expression.md)|Renvoie une chaîne de type caractère après la suppression des espaces de début et de fin.|  
|[SUPÉRIEUR &#40;Expression SSIS&#41;](upper-ssis-expression.md)|Renvoie une chaîne de caractères après avoir converti les caractères minuscules en caractères majuscules.|  
  
 L'évaluateur d'expression dispose des fonctions de date et d'heure suivantes.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[DATEADD &#40;Expression SSIS&#41;](dateadd-ssis-expression.md)|Renvoie une nouvelle valeur DT_DBTIMESTAMP en ajoutant un intervalle de date ou de temps à une date spécifiée.|  
|[DATEDIFF &#40;Expression SSIS&#41;](datediff-ssis-expression.md)|Renvoie le nombre de limites de date et d'heure traversées entre deux dates données.|  
|[DATEPART &#40;Expression SSIS&#41;](datepart-ssis-expression.md)|Renvoie un entier représentant une partie d'une date.|  
|[JOUR &#40;Expression SSIS&#41;](day-ssis-expression.md)|Renvoie un entier représentant le jour de la date spécifiée.|  
|[GETDATE &#40;Expression SSIS&#41;](getdate-ssis-expression.md)|Renvoie la date actuelle du système.|  
|[GETUTCDATE &#40;Expression SSIS&#41;](getutcdate-ssis-expression.md)|Renvoie la date actuelle du système en temps UTC (Universal Time Coordinate ou Greenwich Mean Time).|  
|[MOIS &#40;Expression SSIS&#41;](month-ssis-expression.md)|Renvoie un entier représentant le mois de la date spécifiée.|  
|[ANNÉE &#40;Expression SSIS&#41;](year-ssis-expression.md)|Renvoie un entier représentant l'année de la date spécifiée.|  
  
 L'évaluateur d'expression dispose des fonctions NULL suivantes.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[ISNULL &#40;Expression SSIS&#41;](null-ssis-expression.md)|Renvoie une valeur booléenne basée sur le test du caractère NULL d'une expression.|  
|[NULL &#40;Expression SSIS&#41;](null-ssis-expression.md)|Renvoie une valeur NULL d'un type de données demandé.|  
  
 Bien qu'indiqués en caractères majuscules, les noms d'expression ne respectent pas la casse. Par exemple, vous pouvez utiliser aussi bien « null » que « NULL ».  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs &#40;Expression SSIS&#41;](operators-ssis-expression.md)   
 [Exemples d’expressions Integration Services avancées](examples-of-advanced-integration-services-expressions.md)   
 [Expressions Integration Services &#40;SSIS&#41;](integration-services-ssis-expressions.md)  
  
  