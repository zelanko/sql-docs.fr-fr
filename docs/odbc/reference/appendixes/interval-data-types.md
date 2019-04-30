---
title: Types de données Interval | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 930a848ea01d128cb248c7929408ce7510937ad9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188901"
---
# <a name="interval-data-types"></a>Types de données d’intervalle
Un intervalle est défini comme la différence entre deux dates et heures. Intervalles sont exprimées dans un des deux manières différentes. Un est un *année-mois* intervalle qui exprime les intervalles en termes d’années et un nombre entier d’un mois. L’autre est un *jours-heures* intervalle qui exprime les intervalles en termes de jours, les minutes et secondes. Ces deux types d’intervalles sont distincts et ne peut pas être combinés, étant donné que les mois peuvent avoir différents nombres de jours.  
  
 Un intervalle se compose d’un ensemble de champs. Il existe un classement implicite entre les champs. Par exemple, dans un intervalle année-mois, l’année en premier, suivie du mois. De même, dans un intervalle de jours à la minute, les champs sont dans l’ordre jour, heure et à la minute. Le premier champ dans un type d’intervalle est appelé le *début* champ, ou le *poids* champ. Le dernier champ est appelé le *fin* champ.  
  
 Dans tous les intervalles, le champ de début n’est pas limité par les règles du calendrier grégorien. Par exemple, dans un intervalle heure-minute, le champ d’heure n’est pas limité à être comprise entre 0 et 23 inclus, car il s’agit normalement. Les champs de fin après le début du champ suivent les contraintes habituelles du calendrier grégorien. Pour plus d’informations, consultez [contraintes du calendrier grégorien](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md), plus loin dans cette annexe.  
  
 Il existe 13 types de données SQL intervalle et les types de données C intervalle 13. Chacun des types de données d’intervalle C utilise la même structure, SQL_INTERVAL_STRUCT, pour contenir les données d’intervalle. (Pour plus d’informations, consultez la section suivante, [Structure d’intervalle C](../../../odbc/reference/appendixes/c-interval-structure.md).) Pour plus d’informations sur les types de données SQL, consultez [les Types de données SQL](../../../odbc/reference/appendixes/sql-data-types.md); pour plus d’informations sur les types de données C, consultez [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Identificateur de type|Classe|Description|  
|---------------------|-----------|-----------------|  
|MONTH|Année-mois|Nombre de mois entre deux dates.|  
|YEAR|Année-mois|Nombre d’années entre deux dates.|  
|YEAR_TO_MONTH|Année-mois|Nombre d’années et mois entre deux dates.|  
|DAY|Jours-heures|Nombre de jours entre deux dates.|  
|HOUR|Jours-heures|Nombre d’heures entre deux dates/heures.|  
|MINUTE|Jours-heures|Nombre de minutes entre deux dates/heures.|  
|SECOND|Jours-heures|Nombre de secondes entre deux dates/heures.|  
|DAY_TO_HOUR|Jours-heures|Nombre de jours/heures entre deux dates/heures.|  
|DAY_TO_MINUTE|Jours-heures|Nombre de jours/heures/minutes entre deux dates/heures.|  
|DAY_TO_SECOND|Jours-heures|Nombre de jours/heures/minutes/secondes entre deux dates/heures.|  
|HOUR_TO_MINUTE|Jours-heures|Nombre d’heures/minutes entre deux dates/heures.|  
|HOUR_TO_SECOND|Jours-heures|Nombre d’heures/minutes/secondes entre deux dates/heures.|  
|MINUTE_TO_SECOND|Jours-heures|Nombre de minutes/secondes entre deux dates/heures.|  
  
 Cette section contient les rubriques suivantes.  
  
-   [Structure d’intervalle C](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Précision des types de données d’intervalle](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Longueur des types de données d’intervalle](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Littéraux d’intervalle](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Remplacement de la précision du début et de la fin par défaut pour les types de données d’intervalle](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
