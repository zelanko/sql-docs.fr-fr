---
title: Littéraux d’intervalle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- interval literals [ODBC]
- interval data type [ODBC], literals
ms.assetid: f9e6c3c7-4f98-483f-89d8-ebc5680f021b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc5d09bca83724bb956d39512c51c3dc47db1bad
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188808"
---
# <a name="interval-literals"></a>Littéraux d’intervalle
ODBC requiert que tous les pilotes prennent en charge la conversion du type de données SQL_CHAR ou SQL_VARCHAR à tous les types de données d’intervalle C. Si la source de données sous-jacente ne prend pas en charge les types de données interval, toutefois, le pilote a besoin de connaître le format correct de la valeur dans le champ SQL_CHAR pour prendre en charge de ces conversions. De même, ODBC requiert que n’importe quel type être convertible en SQL_CHAR ou SQL_VARCHAR, par conséquent, un pilote doit savoir quel format un intervalle stocké dans le champ de caractère de ODBC C doit avoir. Cette section décrit la syntaxe des littéraux d’intervalle, le writer de pilote doit utiliser pour valider les champs SQL_CHAR lors de la conversion vers ou depuis les types de données d’intervalle C.  
  
> [!NOTE]  
>  La syntaxe BNF complète pour les littéraux d’intervalle est indiquée dans la section [syntaxe de littéral d’intervalle](../../../odbc/reference/appendixes/interval-literal-syntax.md) dans l’annexe c : Grammaire SQL.  
  
 Pour transmettre des littéraux d’intervalle dans le cadre d’une instruction SQL, une syntaxe de clause d’échappement est définie pour les littéraux d’intervalle. Pour plus d’informations, consultez [Date, Time et Timestamp littéraux](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Un littéral d’intervalle est au format :  
  
```  
INTERVAL[<sign>] 'value' <interval qualifier>  
```  
  
 où « INTERVAL » indique que le littéral de caractère est un intervalle. La connexion peut être plus ou moins ; Il est en dehors de la chaîne de l’intervalle et est facultatif.  
  
 Le qualificateur de l’intervalle peut être un champ d’horodatage unique ou être composée de deux champs de date/heure, sous la forme : \< *champ début*> TO \< *fin champ*>.  
  
-   Lorsque l’intervalle est composé d’un champ unique, le seul champ peut être un champ non seconde qui peut être accompagné d’une précision de début facultative entre parenthèses. Le champ de date/heure unique peut être également un deuxième champ qui peut être accompagné de la précision de début facultative, la précision en fractions de seconde facultatif entre parenthèses ou les deux. Si une précision de début et une précision en fractions de seconde sont présents pour un champ de secondes, ils sont séparés par des virgules. Si le champ des secondes a une précision en fractions de seconde, il doit également avoir une précision de début.  
  
-   Lorsque l’intervalle est composée de champs de début et de fin, le champ Début est un champ non seconde qui peut être accompagné de l’intervalle de précision de champ d’en-tête entre parenthèses. Le champ de fin peut être un champ non seconde ou un deuxième champ qui peut être accompagné d’une précision de fractions de secondes d’intervalle entre parenthèses.  
  
 La chaîne de l’intervalle dans *valeur* est placée entre guillemets simples. Il peut être un littéral de l’année-mois ou un littéral d’heure de la journée. Le format de la chaîne dans *valeur* est déterminée par les règles suivantes :  
  
-   La chaîne contient une valeur décimale pour chaque champ qui est impliquée par le \< *intervalle* *qualificateur*>.  
  
-   Si la précision de l’intervalle inclut les champs année et mois, les valeurs de ces champs sont séparés par un signe moins.  
  
-   Si la précision de l’intervalle inclut les champs jours et heures, les valeurs de ces champs sont séparés par un espace.  
  
-   Si la précision de l’intervalle inclut les champs heure et l’ordre inférieur (minutes et secondes), les valeurs de ces champs sont séparés par un signe deux-points.  
  
-   Si la précision de l’intervalle inclut un deuxième champ et la précision en expresse ou implicite est différent de zéro, le caractère immédiatement avant le premier chiffre de la partie fractionnaire de la deuxième est un point.  
  
-   Aucun champ ne peut être plus de deux chiffres, à l’exception :  
  
    -   La valeur du champ Début peut être aussi longue que la précision expresse ou implicite interval.  
  
    -   La partie fractionnaire du deuxième champ peut être aussi longue que la précision en expresse ou implicite.  
  
    -   Les champs à droite suivent les contraintes habituelles du calendrier grégorien. (Consultez [contraintes du calendrier grégorien](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md).)  
  
 Le tableau suivant répertorie des exemples de littéraux d’intervalle valide comme étant inclus dans la clause d’échappement ODBC pour les intervalles. La syntaxe de la clause d’échappement est comme suit :  
  
> [!NOTE]  
>  *{Intervalle-chaîne de connexion intervalle intervalle-qualificateur}*  
  
|Littéral clause d’échappement|Intervalle spécifié|  
|---------------------------|------------------------|  
|{YEAR(4) INTERVALLE '326'}|Spécifie un intervalle d’années 326. La précision interval est 4.|  
|{MONTH(3) INTERVALLE '326'}|Spécifie un intervalle de mois 326. La précision interval est 3.|  
|{DAY(4) INTERVALLE '3261'}|Spécifie un intervalle de jours 3261. La précision interval est 4.|  
|{HOUR(3) INTERVALLE '163'}|Spécifie un intervalle de jours 163. La précision interval est 3.|  
|{INTERVAL '163' MINUTE(3)}|Spécifie un intervalle de minutes 163. La précision interval est 3.|  
|{SECOND(3,2) INTERVALLE '223.16'}|Spécifie un intervalle de secondes 223.16. La précision de début d’intervalle est 3, et la précision des secondes est 2.|  
|{INTERVALLE ' 163-11' ANNÉE (3) MOIS}|Spécifie un intervalle de 163 ans et 11 mois. La précision interval est 3.|  
|{INTERVALLE 163 ' 12' DAY (3) HEURE}|Spécifie un intervalle de 163 jours et 12 heures. La précision interval est 3.|  
|{INTERVALLE 163 » 12:39 ' DAY (3) À LA MINUTE}|Spécifie un intervalle de 163 jours, 12 heures, et 39 minutes. La précision interval est 3.|  
|{INTERVALLE '163 12:39:59.163' DAY (3) À SECOND(3)}|Spécifie un intervalle de 163 jours, 12 heures, 39 minutes, et 59.163 secondes. La précision de début d’intervalle est 3, et la précision des secondes est 3.|  
|{INTERVALLE '163:39' HOUR(3) MINUTE}|Spécifie un intervalle de 163 heures et 39 minutes. La précision interval est 3.|  
|{INTERVALLE '163:39:59.163' HOUR(3) À SECOND(4)}|Spécifie un intervalle de 163 heures 39 minutes, et 59.163 secondes. La précision de début d’intervalle est 3, et la précision des secondes est 4.|  
|{INTERVALLE '163:59.163' MINUTE(3) À SECOND(5)}|Spécifie un intervalle de 163 minutes et 59.163 secondes. La précision de début d’intervalle est 3, et la précision des secondes est 5.|  
|{INTERVALLE - JOUR « 23:39:56.23 16 » À LA SECONDE}|Spécifie un intervalle de moins de 16 jours, 23 heures, 39 minutes, et 56.23 secondes. La précision de début implicite est 2, et la précision en implicite est 6.|  
  
 Le tableau suivant répertorie des exemples de littéraux d’intervalle non valide :  
  
|Littéral clause d’échappement|Raison pourquoi non valide|  
|---------------------------|------------------------|  
|{HOUR(2) INTERVALLE '163'}|La précision de début d’intervalle est 2, mais la valeur du champ Début est 163.|  
|{SECOND(2,2) INTERVALLE '223.16'}<br /><br /> {SECOND(3,1) INTERVALLE '223.16'}|Dans le premier exemple, la précision de début est trop petite, et dans le deuxième exemple, la précision en secondes est trop petite.|  
|{INTERVALLE '223.16' SECOND}<br /><br /> {INTERVALLE '223' ANNÉE}|Étant donné que la précision de début n’est pas spécifiée, il est par défaut 2, qui est trop petit pour contenir le littéral spécifié.|  
|{INTERVALLE '22.1234567' SECOND}|La précision en secondes n’est pas spécifiée, afin de la valeur par défaut est 6. Le littéral a sept chiffres après la virgule décimale.|  
|{INTERVALLE ' 163-13' ANNÉE (3) MOIS}<br /><br /> {INTERVALLE ' 163 65' DAY (3) HEURE}<br /><br /> {INTERVALLE '163 62:39' DAY (3) À LA MINUTE}<br /><br /> {INTERVALLE '163 12:125:59.163' DAY (3) À SECOND(3)}<br /><br /> {INTERVAL '163:144' HOUR(3) TO MINUTE}<br /><br /> {INTERVALLE '163:567:234.163' HOUR(3) À SECOND(4)}<br /><br /> {INTERVALLE '163:591.163' MINUTE(3) À SECOND(5)}|Le champ à droite ne suit pas les règles du calendrier grégorien.|
