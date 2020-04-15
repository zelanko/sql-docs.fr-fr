---
title: Contraintes du calendrier grégorien (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f88842c7426e17af1fdc0533b8b97e2c559de237
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284759"
---
# <a name="constraints-of-the-gregorian-calendar"></a>Contraintes du calendrier grégorien
Les types de données relatives aux dates et aux dates horaires, ainsi que les champs de fuite des types de données d’intervalle, doivent être conformes aux contraintes du calendrier grégorien. Ces contraintes sont les suivantes :  
  
-   La valeur du champ de mois doit être comprise entre 1 et 12, inclusivement.  
  
-   La valeur du champ de jour doit être dans la gamme de 1 à 1 nombre de jours dans le mois. Le nombre de jours dans le mois est déterminé à partir des valeurs de l’année et des champs mois et peut être 28, 29, 30, ou 31. (Le nombre de jours dans le mois peut également dépendre de savoir s’il s’agit d’une année bissextile.)  
  
-   La valeur du champ horaire doit être comprise entre 0 et 23, inclusivement.  
  
-   La valeur du champ minute doit être comprise entre 0 et 59, inclusivement.  
  
-   Pour le champ de secondes de fuite des types de données d’intervalle, la valeur du champ secondes doit être comprise entre 0 et 59,9 *(n*), inclusivement, où *n* est le nombre de chiffres dans la précision fractionnelle secondes.  
  
-   Pour le champ de trailing secondes des types de données de date, la valeur du champ secondes doit être comprise entre 0 et 61,9 *(n*), inclusivement, où *n* spécifie le nombre de "9" chiffres et la valeur de *n* est la précision fractionnelle secondes. (La plage de secondes permet jusqu’à deux secondes bissextiles pour maintenir la synchronisation du temps sidéral.)
