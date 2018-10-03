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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694051"
---
# <a name="interval-literal-syntax"></a>Syntaxe des littéraux d’intervalle
La syntaxe suivante est utilisée pour les littéraux d’intervalle dans ODBC.  
  
 *littéral d’intervalle :: = intervalle* [+*&#124;*-] *intervalle-qualificateur de la chaîne de l’intervalle*  
  
 *chaîne de l’intervalle* :: = *devis* { *année-mois-literal* &#124; *littéral d’heure jour* } *devis*  
  
 *année-mois-literal* :: = *-valeur en années* &#124; [*-valeur en années* -] *-valeur en mois*  
  
 *littéral d’heure jour* :: = *jours d’intervalle de temps* &#124; *intervalle de temps*  
  
 *intervalle de temps jour* :: = *-valeur en jours* [*-valeur en heures* [ :*valeur des minutes*[ :*valeur des secondes*]]]  
  
 *intervalle de temps* :: = *-valeur en heures* [ :*valeur des minutes* [ :*valeur des secondes* ]]  
  
 &#124;*valeur des minutes* [ :*valeur des secondes* ]  
  
 &#124;*valeur des secondes*  
  
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
  
 *champ d’horodatage unique* :: = *non-seconde--champ datetime* [(*intervalle pointe champ précision*)] &#124; deuxième [(*-début-champ-précision de l’intervalle*  [, (*intervalle--secondes-précision fractionnelle*)]  
  
 *champ d’horodatage* :: = *non-seconde--champ datetime* &#124; deuxième  
  
 *non-seconde--champ datetime* :: = année &#124; mois &#124; jour &#124; heure &#124; MINUTE  
  
 *intervalle--secondes-précision fractionnelle* :: = *entier non signé*  
  
 *intervalle de début-champ précision* :: = *entier non signé*  
  
 *guillemet* :: = '  
  
 *entier non signé* :: = *chiffre...*
