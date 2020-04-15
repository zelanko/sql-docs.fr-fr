---
title: 'Annexe E : Fonctions Scalar (fr) Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ea354a7f882bd1a75c5f16fb19350d69ca11d375
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292489"
---
# <a name="appendix-e-scalar-functions"></a>Annexe E : Fonctions scalaires
ODBC spécifie les types suivants de fonctions scalaires, avec des informations détaillées sur chacun de ces types de fonctions fournies dans les sections correspondantes de cette annexe. Les descriptions de fonction incluent la syntaxe associée.  
  
 Cette annexe contient les sujets suivants.  
  
-   [Fonctions de chaîne](../../../odbc/reference/appendixes/string-functions.md)  
  
-   [Fonctions numériques](../../../odbc/reference/appendixes/numeric-functions.md)  
  
-   [Fonctions d'heure, de date et d'intervalle](../../../odbc/reference/appendixes/time-date-and-interval-functions.md)  
  
-   [Fonctions système](../../../odbc/reference/appendixes/system-functions.md)  
  
-   [Fonctions de conversion de types de données explicites](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md)  
  
-   [CAST (SQL-92), fonction](../../../odbc/reference/appendixes/sql-92-cast-function.md)  
  
 ODBC n’exige pas un type de données pour les valeurs de retour des fonctions scalaires parce que les fonctions sont souvent spécifiques aux données. Les applications doivent utiliser la fonction scalaire CONVERT dans la mesure du possible pour forcer la conversion de type de données.  
  
## <a name="odbc-and-sql-92-scalar-functions"></a>Fonctions ODBC et SQL-92 Scalar  
 Les tableaux de cette annexe comprennent des fonctions qui ont été ajoutées dans ODBC 3.0 pour s’aligner avec SQL-92. Ces fonctions ajoutées pour un type particulier de fonction scalaire, telles que définies dans ODBC, sont indiquées dans chaque section.  
  
 ODBC et SQL-92 classent leurs fonctions scalaires différemment. ODBC classe les fonctions scalaires par type d’argument; SQL-92 les classe par valeur de retour. Par exemple, la fonction EXTRACT est classée comme fonction de décalage par ODBC, parce que l’argument de champ d’extraction est un mot clé de date et l’argument de l’extraction-source est une expression de date ou d’intervalle. SQL-92, d’autre part, classe EXTRACT comme une fonction scalaire numérique, parce que la valeur de rendement est un numérique.  
  
 Une application peut déterminer quelles fonctions scalaires un conducteur prend en charge en appelant **SQLGetInfo**. Les types d’information sont inclus à la fois pour ODBC et pour les classifications SQL-92 des fonctions scalaires. Étant donné que ces classifications sont différentes, le soutien de certaines fonctions scalaires peut être indiqué dans les types d’information qui ne correspondent pas à ODBC et SQL-92. Par exemple, l’appui à l’EXTRACT dans ODBC est indiqué par le type d’information SQL_TIMEDATE_FUNCTIONS; L’appui à l’EXTRACT dans SQL-92, par contre, est indiqué par le type d’information SQL_SQL92_NUMERIC_VALUE_FUNCTIONS.
