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
manager: craigg
ms.openlocfilehash: d477dbc6b54d7ebd82b7e2ef8611f5f6dd807e83
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188817"
---
# <a name="interval-literal-syntax"></a>Syntaxe des littéraux d’intervalle
La syntaxe suivante est utilisée pour les littéraux d’intervalle dans ODBC.  
  
 *littéral d’intervalle :: = intervalle* [+*&#124;*-] *intervalle-qualificateur de la chaîne de l’intervalle*  
  
 *interval-string* ::= *quote* { *year-month-literal* &#124; *day-time-literal* } *quote*  
  
 *year-month-literal* ::= *years-value* &#124; [*years-value* -] *months-value*  
  
 *day-time-literal* ::= *day-time-interval* &#124; *time-interval*  
  
 *day-time-interval* ::= *days-value* [*hours-value* [:*minutes-value*[:*seconds-value*]]]  
  
 *intervalle de temps* :: = *-valeur en heures* [ :*valeur des minutes* [ :*valeur des secondes* ]]  
  
 &#124; *minutes-value* [:*seconds-value* ]  
  
 &#124; *seconds-value*  
  
 *valeur en années* :: = *-valeur datetime*  
  
 *months-value* ::= *datetime-value*  
  
 *days-value* ::= *datetime-value*  
  
 *valeur des heures* :: = *-valeur datetime*  
  
 *minutes-value* ::= *datetime-value*  
  
 *seconds-value* ::= *seconds-integer-value* [.[*seconds-fraction*] ]  
  
 *seconds-integer-value* ::= *unsigned-integer*  
  
 *seconds-fraction* ::= *unsigned-integer*  
  
 *datetime-value* ::= *unsigned-integer*  
  
 *interval-qualifier* ::= *start-field* TO *end-field* &#124; *single-datetime-field*  
  
 *champ de début* :: = *non-seconde--champ datetime* [(*intervalle pointe champ précision* )]  
  
 *champ de fin* :: = *non-seconde--champ datetime* &#124; deuxième [(*intervalle--secondes-précision fractionnelle*)]  
  
 *champ d’horodatage unique* :: = *non-seconde--champ datetime* [(*intervalle pointe champ précision*)] &#124; deuxième [(*-début-champ-précision de l’intervalle * [, (*intervalle--secondes-précision fractionnelle*)]  
  
 *champ d’horodatage* :: = *non-seconde--champ datetime* &#124; deuxième  
  
 *non-seconde--champ datetime* :: = année &#124; mois &#124; jour &#124; heure &#124; MINUTE  
  
 *interval-fractional-seconds-precision* ::= *unsigned-integer*  
  
 *interval-leading-field-precision* ::= *unsigned-integer*  
  
 *quote* ::= '  
  
 *entier non signé* :: = *chiffre...*
