---
description: Syntaxe des littéraux d’intervalle
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20a994cbcfa063a4bbc7189f95d6f7e45ba2ffb0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483252"
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
