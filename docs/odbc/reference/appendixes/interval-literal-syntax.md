---
title: Syntaxe de littéral d’intervalle | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041619"
---
# <a name="interval-literal-syntax"></a>Syntaxe des littéraux d’intervalle
La syntaxe suivante est utilisée pour les littéraux d’intervalle dans ODBC.  
  
 *littéral d’intervalle :: = intervalle* [+ *&#124;* -] *intervalle-qualificateur de la chaîne de l’intervalle*  
  
 *interval-string* ::= *quote* { *year-month-literal* &#124; *day-time-literal* } *quote*  
  
 *year-month-literal* ::= *years-value* &#124; [*years-value* -] *months-value*  
  
 *day-time-literal* ::= *day-time-interval* &#124; *time-interval*  
  
 *intervalle de temps jour* :: = *-valeur en jours* [ *-valeur en heures* [ :*valeur des minutes*[ :*valeur des secondes*]]]  
  
 *intervalle de temps* :: = *-valeur en heures* [ :*valeur des minutes* [ :*valeur des secondes* ]]  
  
 &#124;*valeur des minutes* [ :*valeur des secondes* ]  
  
 &#124; *seconds-value*  
  
 *valeur en années* :: = *-valeur datetime*  
  
 *valeur de mois* :: = *-valeur datetime*  
  
 *valeur de jours* :: = *-valeur datetime*  
  
 *valeur des heures* :: = *-valeur datetime*  
  
 *valeur de minutes* :: = *-valeur datetime*  
  
 *valeur des secondes* :: = *secondes entier* [. [ *fraction de seconde*]]  
  
 *valeur de nombre entier de secondes* :: = *entier non signé*  
  
 *fraction de seconde* :: = *entier non signé*  
  
 *valeur de date/heure* :: = *entier non signé*  
  
 *qualificateur de l’intervalle* :: = *début champ* TO *fin-champ* &#124; *champ d’horodatage unique*  
  
 *champ de début* :: = *non-seconde--champ datetime* [(*intervalle pointe champ précision* )]  
  
 *champ de fin* :: = *non-seconde--champ datetime* &#124; deuxième [(*intervalle--secondes-précision fractionnelle*)]  
  
 *champ d’horodatage unique* :: = *non-seconde--champ datetime* [(*intervalle pointe champ précision*)] &#124; deuxième [( *-début-champ-précision de l’intervalle*  [, (*intervalle--secondes-précision fractionnelle*)]  
  
 *champ d’horodatage* :: = *non-seconde--champ datetime* &#124; deuxième  
  
 *non-seconde--champ datetime* :: = année &#124; mois &#124; jour &#124; heure &#124; MINUTE  
  
 *intervalle--secondes-précision fractionnelle* :: = *entier non signé*  
  
 *intervalle de début-champ précision* :: = *entier non signé*  
  
 *guillemet* :: = '  
  
 *entier non signé* :: = *chiffre...*
