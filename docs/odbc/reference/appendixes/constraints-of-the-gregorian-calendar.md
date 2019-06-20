---
title: Contraintes du calendrier grégorien | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30fbdd17e7ec5eb970948e1c7133020081222614
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63224569"
---
# <a name="constraints-of-the-gregorian-calendar"></a>Contraintes du calendrier grégorien
Types de données date et datetime et les champs à droite de types de données interval, doivent être conforme aux contraintes du calendrier grégorien. Ces contraintes sont les suivantes :  
  
-   La valeur du champ mois doit être comprise entre 1 et 12, inclus.  
  
-   La valeur du champ jour doit être dans la plage comprise entre 1 et le nombre de jours du mois. Le nombre de jours du mois est déterminé à partir des valeurs des champs année et mois et peut être 28, 29, 30 ou 31. (Le nombre de jours du mois peut également dépendre s’il s’agit d’une année bissextile.)  
  
-   La valeur du champ heures doit être comprise entre 0 et 23 inclus.  
  
-   La valeur du champ minute doit être comprise entre 0 et 59 inclus.  
  
-   Pour la fin du champ des secondes de types de données interval, la valeur du champ secondes doit être comprise entre 0 et 59,9 (*n*), inclusivement, où *n* est le nombre de chiffres dans la précision en fractions de seconde.  
  
-   Pour la fin du champ des secondes de types de données de date/heure, la valeur du champ secondes doit être comprise entre 0 et 61.9 (*n*), inclusivement, où *n* Spécifie le nombre de chiffres « 9 » et la valeur de *n*  est la précision en fractions de seconde. (La plage des secondes autorise jusqu'à deux secondes intercalaires maintenir la synchronisation de temps de sidereal.)
