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
ms.openlocfilehash: 9f67d313f5a1261dba1f88e9ef3a70d30c1cd503
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019179"
---
# <a name="constraints-of-the-gregorian-calendar"></a>Contraintes du calendrier grégorien
Les types de données date et DateTime, et les champs de fin des types de données Interval, doivent être conformes aux contraintes du calendrier grégorien. Ces contraintes sont les suivantes :  
  
-   La valeur du champ month doit être comprise entre 1 et 12, inclus.  
  
-   La valeur du champ jour doit être comprise entre 1 et le nombre de jours du mois. Le nombre de jours du mois est déterminé à partir des valeurs des champs année et mois et peut être 28, 29, 30 ou 31. (Le nombre de jours du mois peut également dépendre du fait qu’il s’agit d’une année bissextile ou non).  
  
-   La valeur du champ heure doit être comprise entre 0 et 23 inclus.  
  
-   La valeur du champ minute doit être comprise entre 0 et 59 inclus.  
  
-   Pour le champ secondes de fin des types de données Interval, la valeur du champ seconds doit être comprise entre 0 et 59,9 (*n*), inclus, où *n* est le nombre de chiffres dans la précision en fractions de seconde.  
  
-   Pour le champ des secondes de fin des types de données DateTime, la valeur du champ seconds doit être comprise entre 0 et 61,9 (*n*), inclus, où *n* spécifie le nombre de chiffres « 9 » et la valeur de *n* est la précision en fractions de seconde. (La plage de secondes autorise jusqu’à deux secondes bissextiles pour maintenir la synchronisation du temps de SIDEREAL.)
