---
title: Types de données d’intervalles (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- second intervals [ODBC]
- data types [ODBC], interval data types
- interval data type [ODBC]
- day-time intervals [ODBC]
- intervals [ODBC], about intervals
- minute intervals [ODBC]
- day intervals [ODBC]
- year intervals [ODBC]
- month intervals [ODBC]
- interval data type [ODBC], about interval data types
- SQL data types [ODBC], interval
- year-month intervals [ODBC]
- C data types [ODBC], interval
- interval fields [ODBC]
ms.assetid: fba93f65-c1db-44f4-91ba-532f87241cf7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee4a6e845e0bc0830f514b2e768075dd75bcf6e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304965"
---
# <a name="interval-data-types"></a>Types de données d’intervalle
Un intervalle est défini comme la différence entre deux dates et les heures. Les intervalles s’expriment de l’une des deux façons différentes. L’un est un intervalle *d’un mois* qui exprime des intervalles en termes d’années et un nombre intégral de mois. L’autre est un intervalle *de jour* qui exprime des intervalles en termes de jours, de minutes et de secondes. Ces deux types d’intervalles sont distincts et ne peuvent pas être mélangés, parce que les mois peuvent avoir un nombre variable de jours.  
  
 Un intervalle se compose d’un ensemble de champs. Il y a une commande implicite entre les champs. Par exemple, dans un intervalle d’une année à l’autre, l’année passe en premier, suivie du mois. De même, dans un intervalle de jour en minute, les champs sont dans le jour de l’ordre, heure et minute. Le premier champ dans un type d’intervalle est appelé le champ *de tête,* ou le champ *de haut-ordre.* Le dernier champ est appelé le champ *de traîne.*  
  
 Dans tous les intervalles, le champ de tête n’est pas limité par les règles du calendrier grégorien. Par exemple, dans un intervalle d’une heure à la minute, le champ d’heures n’est pas limité à entre 0 et 23 (inclusivement), comme il est normalement. Les champs de fuite suivant le champ de tête suivent les contraintes habituelles du calendrier grégorien. Pour plus d’informations, voir [Contraintes du calendrier grégorien](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md), plus tard dans cette annexe.  
  
 Il existe 13 types de données SQL d’intervalle et 13 types de données d’intervalle C. Chacun des types de données D’intervalle C utilise la même structure, SQL_INTERVAL_STRUCT, pour contenir les données d’intervalle. (Pour plus d’informations, voir la section suivante, [C Interval Structure](../../../odbc/reference/appendixes/c-interval-structure.md).) Pour plus d’informations sur les types de données SQL, voir [SQL Data Types;](../../../odbc/reference/appendixes/sql-data-types.md) pour plus d’informations sur les types de données C, voir [C Data Types](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Type d’identificateur|Classe|Description|  
|---------------------|-----------|-----------------|  
|MONTH|Mois de l’année|Nombre de mois entre deux dates.|  
|YEAR|Mois de l’année|Nombre d’années entre deux dates.|  
|YEAR_TO_MONTH|Mois de l’année|Nombre d’années et de mois entre deux dates.|  
|DAY|Jour-Temps|Nombre de jours entre deux dates.|  
|HOUR|Jour-Temps|Nombre d’heures entre deux dates/heures.|  
|MINUTE|Jour-Temps|Nombre de minutes entre deux dates/heures.|  
|SECOND|Jour-Temps|Nombre de secondes entre deux dates/heures.|  
|DAY_TO_HOUR|Jour-Temps|Nombre de jours/heures entre deux dates/heures.|  
|DAY_TO_MINUTE|Jour-Temps|Nombre de jours/heures/minutes entre deux dates/heures.|  
|DAY_TO_SECOND|Jour-Temps|Nombre de jours/heures/minutes/secondes entre deux dates/heures.|  
|HOUR_TO_MINUTE|Jour-Temps|Nombre d’heures/minutes entre deux dates/heures.|  
|HOUR_TO_SECOND|Jour-Temps|Nombre d’heures/minutes/secondes entre deux dates/heures.|  
|MINUTE_TO_SECOND|Jour-Temps|Nombre de minutes/secondes entre deux dates/heures.|  
  
 Cette section contient les rubriques suivantes :  
  
-   [Structure d’intervalle C](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Précision des types de données d’intervalle](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Longueur des types de données d’intervalle](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Littéraux d’intervalle](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Remplacement de la précision du début et de la fin par défaut pour les types de données d’intervalle](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
