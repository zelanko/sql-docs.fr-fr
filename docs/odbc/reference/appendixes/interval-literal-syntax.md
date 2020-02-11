---
title: Syntaxe des littéraux d’intervalle | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6352a5ae894adb09f714a78386bfecfa3ce1df77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041619"
---
# <a name="interval-literal-syntax"></a>Syntaxe des littéraux d’intervalle
La syntaxe suivante est utilisée pour les littéraux d’intervalle dans ODBC.  
  
 *Interval-Literal :: = intervalle* [+*&#124;*-] Interval *-chaîne Interval-qualifier*  
  
 *Interval-String* :: = *quote* { *year-mois-Literal* &#124;st *Day-Time-Literal* } *quote*  
  
 *année-mois-littéral* :: = *years-value* &#124; [*years-value* -] *months-value*  
  
 *Day-Time-Literal* :: = *jour-time-interval* &#124; *temps-intervalle*  
  
 *Day-Time-Interval* :: = *Days-value* [*hours-value* [ :*minutes-value*[ :*seconds-value*]]]  
  
 *Time-Interval* :: = *hours-value* [ :*minutes-value* [ :*seconds-value* ]]  
  
 &#124; *minutes-valeur* [ :*secondes-valeur* ]  
  
 &#124; *secondes-valeur*  
  
 *years-value* :: = *DateTime-value*  
  
 *months-value* :: = *DateTime-value*  
  
 *Days-value* :: = *DateTime-value*  
  
 *hours-value* :: = *DateTime-value*  
  
 *minutes-valeur* :: = *DateTime-value*  
  
 *seconds-valeur* :: = *seconds-entier-valeur* [. [ *fractions de seconde*] ]  
  
 *seconds-entier-valeur* :: = *non signé-entier*  
  
 *seconds-fraction* :: = *non signé-entier*  
  
 *DateTime-value* :: = *unsigned-Integer*  
  
 *Interval-qualifier* :: = *Start-Field* TO *end-Field* &#124; *Single-DateTime-Field*  
  
 *Start-Field* :: = *non-second-DateTime-Field* [(*Interval-leader-champ-précision* )]  
  
 *end-Field* :: = *second-datetime-Field* &#124; second [(*Interval-fractionnaire-seconds-Precision*)]  
  
 *Single-DateTime-Field* :: = not *-second-DateTime-Field* [(*Interval-leader-Field-Precision*)] &#124; second [(*Interval-leader-champ-précision* [, (*intervalle-fraction de seconde-précision*)]  
  
 *DateTime-Field* :: = *second-datetime-Field* &#124; seconde  
  
 *non-second-DateTime-Field* :: = Year &#124; mois &#124; jour &#124; heure &#124; minute  
  
 *Interval-fractionnaire-seconds-Precision* :: = *unsigned-Integer*  
  
 *Interval-champ de début-précision* :: = *unsigned-Integer*  
  
 *quote* :: = '  
  
 *unsigned-entier* :: = *digit...*
