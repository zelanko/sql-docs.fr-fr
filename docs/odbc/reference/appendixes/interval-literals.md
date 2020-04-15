---
title: Intervalles Littéraires - France Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1761ac0acb57b3f375a7d19e9371384c000eca5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304940"
---
# <a name="interval-literals"></a>Littéraux d’intervalle
ODBC exige que tous les conducteurs prennent en charge la conversion du type de données SQL_CHAR ou SQL_VARCHAR à tous les types de données d’intervalle C. Toutefois, si la source de données sous-jacente ne prend pas en charge les types de données d’intervalle, le conducteur doit connaître le format correct de la valeur dans le domaine SQL_CHAR afin de prendre en charge ces conversions. De même, ODBC exige que n’importe quel type C DBC soit convertible pour SQL_CHAR ou SQL_VARCHAR, de sorte qu’un pilote doit savoir quel format un intervalle stocké dans le champ de caractère devrait avoir. Cette section décrit la syntaxe des littérals d’intervalle, que l’auteur pilote doit utiliser pour valider les champs SQL_CHAR lors de la conversion, soit vers ou à partir de types de données d’intervalle C.  
  
> [!NOTE]  
>  La syntaxe complète BNF pour les littérals d’intervalle est indiquée dans la section [Interval Literal Syntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) à l’Annexe C: SQL Grammar.  
  
 Pour passer les littérals d’intervalle dans le cadre d’une déclaration SQL, une syntaxe clause d’évasion est définie pour les littérals d’intervalle. Pour plus d’informations, voir [Date, Time, et Timestamp Literals](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Un intervalle littéral est de la forme:  
  
```  
INTERVAL[<sign>] 'value' <interval qualifier>  
```  
  
 où "INTERVAL" indique que le caractère littéral est un intervalle. Le signe peut être plus ou moins; il est en dehors de la chaîne d’intervalle et est facultatif.  
  
 Le qualificatif d’intervalle peut être soit un champ de date \<unique ou être \<composé de deux champs de date, sous la forme: champ de *tête*> TO champ de *fuite*>.  
  
-   Lorsque l’intervalle est composé d’un seul champ, le champ unique peut être un champ non-deuxième qui peut être accompagné d’une précision de conduite optionnelle entre parenthèses. Le champ d’heure unique peut également être un deuxième champ qui peut être accompagné par la précision de conduite optionnelle, la précision fractionnelle-secondes optionnelle entre parenthèses, ou les deux. Si une précision de tête et une précision fractionnelle sont présentes pendant une seconde, elles sont séparées par des virgules. Si le champ de secondes a une précision fractionnelle-secondes, il doit également avoir une précision de conduite.  
  
-   Lorsque l’intervalle est composé de champs de tête et de fuite, le champ de tête est un champ non-deuxième qui peut être accompagné par la précision de champ de tête d’intervalle entre parenthèses. Le champ de trail peut être soit un champ non-deuxième ou un deuxième champ qui peut être accompagné d’une précision fractionnaire d’intervalle-secondes entre parenthèses.  
  
 La chaîne d’intervalle en *valeur* est incluse dans des guillemets uniques. Il peut s’agir d’un mois littéral d’un mois ou d’un littératie de jour. Le format de la chaîne en *valeur* est déterminé par les règles suivantes :  
  
-   La chaîne contient une valeur décimale pour \<chaque domaine qui est impliqué par le *qualificatif* *d’intervalle*>.  
  
-   Si la précision d’intervalle inclut les champs YEAR et MONTH, les valeurs de ces champs sont séparées par un signe moins.  
  
-   Si la précision d’intervalle inclut les champs DAY et HOUR, les valeurs de ces champs sont séparées par un espace.  
  
-   Si la précision d’intervalle inclut le champ HOUR et les champs d’ordre inférieur (MINUTE et SECOND), les valeurs de ces champs sont séparées par un côlon.  
  
-   Si la précision d’intervalle inclut un champ SECOND et que la précision exprimée ou implicite des secondes n’est pas zéro, le personnage immédiatement avant le premier chiffre de la partie fractionnaire de la seconde est une période.  
  
-   Aucun champ ne peut être plus de deux chiffres de long, sauf:  
  
    -   La valeur du champ de tête peut être aussi longue que l’intervalle exprimé ou implicite menant la précision.  
  
    -   La partie fractionnaire du champ SECOND peut être aussi longue que la précision exprimée ou implicite secondes.  
  
    -   Les champs de fuite suivent les contraintes habituelles du calendrier grégorien. (Voir [Les contraintes du calendrier grégorien](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md).)  
  
 Le tableau suivant énumère des exemples de littéral d’intervalle valides tels qu’inclus dans la clause d’évacuation de l’ODBC pour les intervalles. La syntaxe de la clause d’évacuation est la suivante :  
  
> [!NOTE]  
>  *'INTERVAL signent l’intervalle-corde d’intervalle-qualification'*  
  
|Clause d’évasion littérale|Intervalle spécifié|  
|---------------------------|------------------------|  
|ANNÉE D’INTERVALLE '326'))MD|Spécifie un intervalle de 326 ans. La précision de tête d’intervalle est de 4.|  
|MOIS D’INTERVALLE '326')|Spécifie un intervalle de 326 mois. La précision de tête d’intervalle est 3.|  
|JOUR D’INTERVALLE '3261')MD|Spécifie un intervalle de 3261 jours. La précision de tête d’intervalle est de 4.|  
|«INTERVALLE '163' HEURE(3)MD|Spécifie un intervalle de 163 jours. La précision de tête d’intervalle est 3.|  
|«INTERVALLE '163' MINUTE(3)MD|Spécifie un intervalle de 163 minutes. La précision de tête d’intervalle est 3.|  
|«INTERVALLE '223.16' SECONDE (3,2)'|Spécifie un intervalle de 223,16 secondes. La précision de tête d’intervalle est de 3, et la précision secondes est de 2.|  
|«INTERVALLE '163-11' ANNÉE(3) À MOIS|Spécifie un intervalle de 163 ans et 11 mois. La précision de tête d’intervalle est 3.|  
|«INTERVALLE '163 12' JOUR(3) À L’HEURE|Spécifie un intervalle de 163 jours et 12 heures. La précision de tête d’intervalle est 3.|  
|«INTERVALLE '163 12:39' JOUR(3) À MINUTE|Spécifie un intervalle de 163 jours, 12 heures et 39 minutes. La précision de tête d’intervalle est 3.|  
|«INTERVALLE '163 12:39:59.163' JOUR(3) À LA DEUXIÈME(3)'|Spécifie un intervalle de 163 jours, 12 heures, 39 minutes et 59,163 secondes. La précision de tête d’intervalle est de 3, et la précision secondes est 3.|  
|«INTERVALLE '163:39' HEURE(3) À MINUTE|Spécifie un intervalle de 163 heures et 39 minutes. La précision de tête d’intervalle est 3.|  
|«INTERVALLE '163:39:59.163' HEURE(3) À LA DEUXIÈME(4)'|Spécifie un intervalle de 163 heures, 39 minutes et 59,163 secondes. La précision de tête d’intervalle est de 3, et la précision secondes est de 4.|  
|«INTERVALLE '163:59.163' MINUTE(3) À LA DEUXIÈME(5)'|Spécifie un intervalle de 163 minutes et 59,163 secondes. La précision de tête d’intervalle est de 3, et la précision secondes est de 5.|  
|«INTERVALLE -'16 23:39:56.23' JOUR À LA DEUXIÈME|Spécifie un intervalle de moins 16 jours, 23 heures, 39 minutes et 56,23 secondes. La précision de tête implicite est de 2, et la précision implicite secondes est de 6.|  
  
 Le tableau suivant énumère des exemples de littérals d’intervalle invalides :  
  
|Clause d’évasion littérale|Raison pour laquelle invalide|  
|---------------------------|------------------------|  
|«INTERVALLE '163' HEURE(2)MD|La précision de tête d’intervalle est de 2, mais la valeur du champ de tête est de 163.|  
|«INTERVALLE '223.16' SECONDE (2,2)'<br /><br /> «INTERVALLE '223.16' SECONDE (3,1)'|Dans le premier exemple, la précision de pointe est trop petite, et dans le second exemple, la précision secondes est trop petite.|  
|«INTERVALLE '223.16' SECONDE<br /><br /> «INTERVALLE '223' ANNÉE|Parce que la précision de tête n’est pas spécifiée, elle est par défaut à 2, ce qui est trop petit pour tenir le littératal spécifié.|  
|«INTERVALLE '22.1234567' SECONDE|La précision des secondes n’est pas spécifiée, de sorte qu’elle par défaut à 6. Le littéral a sept chiffres après le point décimal.|  
|«INTERVALLE '163-13' ANNÉE(3) À MOIS<br /><br /> «INTERVALLE '163 65' JOUR(3) À L’HEURE<br /><br /> «INTERVALLE '163 62:39' JOUR(3) À LA MINUTE<br /><br /> «INTERVALLE '163 12:125:59.163' JOUR(3) À LA DEUXIÈME(3)'<br /><br /> «INTERVALLE '163:144' HEURE(3) À MINUTE<br /><br /> «INTERVALLE '163:567:234.163' HEURE(3) À LA DEUXIÈME(4)'<br /><br /> «INTERVALLE '163:591.163' MINUTE(3) À LA DEUXIÈME(5)'|Le champ de fuite ne suit pas les règles du calendrier grégorien.|
