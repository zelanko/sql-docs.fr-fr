---
title: 'Annexe E : Fonctions scalaires | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL-92 functions [ODBC]
- scalar functions [ODBC]
- functions [ODBC], scalar
ms.assetid: 59c7cd5e-32d6-43ab-bac3-7010322d105a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bb5f16485312979e9fb2ad6b3a95dacb79b695d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67996180"
---
# <a name="appendix-e-scalar-functions"></a>Annexe E : Fonctions scalaires
ODBC spécifie les types suivants de fonctions scalaires, des informations détaillées sur chacun de ces types de fonction fournis dans les sections correspondantes de cette annexe. Les descriptions fonction incluent la syntaxe associée.  
  
 Cette annexe contient les rubriques suivantes.  
  
-   [Fonctions de chaîne](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Fonctions numériques](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Fonctions d’heure, de date et d’intervalle](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Fonctions système](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Fonctions de conversion de types de données explicites](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [CAST (SQL-92), fonction](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC ne force pas un type de données pour les valeurs de retour à partir de fonctions scalaires, car les fonctions sont souvent spécifiques à la source de données. Applications doivent utiliser la fonction scalaire CONVERT chaque fois que possible de forcer la conversion de type de données.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>Fonctions scalaires ODBC et SQL-92  
 Les tables dans cette annexe incluent des fonctions qui ont été ajoutées dans ODBC 3.0 pour les aligner avec SQL-92. Ces fonctions ajoutées pour un type particulier d’une fonction scalaire, tel que défini dans ODBC, sont indiquées dans chaque section.  
  
 ODBC et SQL-92 classent leurs fonctions scalaires différemment. ODBC classifie les fonctions scalaires par type d’argument ; SQL-92 les classe par valeur de retour. Par exemple, la fonction EXTRACT est classée comme une fonction timedate par ODBC, étant donné que l’argument de champ d’extrait est un mot clé de date/heure et l’argument de la source de l’extraction est une expression datetime ou interval. SQL-92, classifie quant à eux, extraction comme une fonction scalaire numérique, car la valeur de retour est une valeur numérique.  
  
 Une application peut déterminer les fonctions scalaires, un pilote prend en charge en appelant **SQLGetInfo**. Types d’informations sont incluses pour ODBC et les classifications de SQL-92 des fonctions scalaires. Étant donné que ces classifications sont différentes, la prise en charge pour certaines fonctions scalaires peut-être être indiqué dans les types d’informations qui ne correspondent pas à ODBC et SQL-92. Par exemple, la prise en charge pour l’extraction dans ODBC est indiquée par le type d’informations SQL_TIMEDATE_FUNCTIONS ; prise en charge pour l’extraction dans SQL-92, quant à eux, est indiqué par le type d’information SQL_SQL92_NUMERIC_VALUE_FUNCTIONS.
