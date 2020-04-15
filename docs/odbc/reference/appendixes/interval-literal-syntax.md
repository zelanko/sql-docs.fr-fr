---
title: Syntaxe littérale d’intervalle Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3387b07a8e769206a6a495addff4287000691fec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290569"
---
# <a name="interval-literal-syntax"></a>Syntaxe des littéraux d’intervalle
La syntaxe suivante est utilisée pour les littérals d’intervalle dans ODBC.  
  
 *intervalle-littéral ::' INTERVAL* * [&#124;*-] *interval-string interval-string interval-qualifier*  
  
 *intervalle-corde* ::' *citation* - *année-mois-littérale* &#124; *jour-temps-littérale* ' *citation*  
  
 *mois-littéral* ::' *années-valeur* &#124;*[années-valeur* -] *mois-valeur*  
  
 *jour-temps-littérale* :: *jour-temps-intervalle* &#124; *temps-intervalle*  
  
 *jour-temps-intervalle* *::'jours-valeur* [*heures-valeur* [:*minutes-valeur*[:*secondes-valeur*]]]  
  
 *temps-intervalle* *::'heures-valeur* [:*minutes-valeur* [:*secondes-valeur* ]  
  
 &#124; *minutes-valeur* [:*seconde valeur* ]  
  
 &#124; *seconde-valeur*  
  
 *années de valeur* ::- *datetime-valeur*  
  
 *mois de valeur* ::- *datetime-value*  
  
 *jours-valeur* ::' *datetime-value*  
  
 *heures de valeur* ::- *datetime-value*  
  
 *minutes-valeur* ::' *datetime-value*  
  
 *secondes-valeur* ::md *secondes-integer-valeur* [.[ *secondes-fraction*] ]  
  
 *seconde-integer-valeur* ::' *non signé-integer*  
  
 *secondes-fraction* ::- *non signé-integer*  
  
 *datetime-value* ::md *insigned-integer*  
  
 *intervalle-qualification* ::md *start-field* TO *end-field* &#124; *single-datetime-field*  
  
 *start-field* ::md *non-second-datetime-field* [(*intervalle-leader-champ-précision* )]  
  
 *champ final* ::md *non-second-datetime-field* &#124; SECOND[(*intervalle-fractional-secondes-précision)]*  
  
 *champ à temps unique* ::md *non-second-datetime-field* [(*intervalle-leader-champ-précision*)] &#124; SECOND [(*intervalle-leader-champ-précision* [, (*intervalle-fractional-secondes-précision)]*  
  
 *datetime-field* ::md *non-second-datetime-field* &#124; SECOND  
  
 *non-deuxième date-champ* ::' YEAR &#124; MONTH &#124; DAY &#124; HOUR &#124; MINUTE  
  
 *intervalle-fractional-secondes-précision* ::' *insigned-integer*  
  
 *intervalle-leader-champ-précision* *::'insigned-integer*  
  
 *citation* ::MD ' '  
  
 *non signé-integer* ::' *chiffre ...*
