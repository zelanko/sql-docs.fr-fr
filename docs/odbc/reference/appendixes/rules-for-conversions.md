---
title: Règles pour les conversions (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], literals
- conversions with numeric literals [ODBC]
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: 89f846a3-001d-496a-9843-ac9c38dc1762
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c49177d62fffc3b3b5c47a25bf3fb421d7564245
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305085"
---
# <a name="rules-for-conversions"></a>Règles pour les conversions
Les règles de cette section s’appliquent aux conversions impliquant des littérals numériques. Aux fins de ces règles, les termes suivants sont définis :  
  
-   *Affectation de magasin :* Lors de l’envoi de données dans une colonne de table dans une base de données. Cela se produit lors des appels à **SQLExecute**, **SQLExecDirect**, et **SQLSetPos**. Pendant l’affectation en magasin, « cible » désigne une colonne de base de données et une « source » se réfère aux données dans les tampons d’application.  
  
-   *Affectation de récupération :* Lors de la récupération des données de la base de données dans les tampons d’application. Cela se produit lors des appels à **SQLFetch**, **SQLGetData**, **SQLFetchScroll**, et **SQLSetPos**. Lors de l’affectation de récupération, « cible » désigne les tampons d’application et la « source » se réfère à la colonne de base de données.  
  
-   *CS:* La valeur dans la source de caractère.  
  
-   *NT:* La valeur de la cible numérique.  
  
-   *Nouvelle-Ment:* La valeur de la source numérique.  
  
-   *CT:* La valeur de la cible de caractère.  
  
-   Précision d’un littéral numérique exact : le nombre de chiffres qu’il contient.  
  
-   L’échelle d’un littéral numérique exact : le nombre de chiffres à droite de la période exprimée ou implicite.  
  
-   La précision d’un littéral numérique approximatif : la précision de sa mantissa.  
  
## <a name="character-source-to-numeric-target"></a>Source de caractère à Numeric Target  
 Voici les règles de conversion d’une source de caractère (CS) à une cible numérique (NT):  
  
1.  Remplacez CS par la valeur obtenue en supprimant les espaces de tête ou de fuite dans CS. Si CS n’est pas un *numérique-littéral*valide, SQLSTATE 22018 (valeur de caractère invalide pour la spécification de distribution) est retourné.  
  
2.  Remplacez CS par la valeur obtenue en supprimant les zéros de tête avant le point décimal, en s’enlevant les zéros après le point décimal, ou les deux.  
  
3.  Convertir CS en NT. Si la conversion entraîne une perte de chiffres significatifs, SQLSTATE 22003 (valeur numérique hors de portée) est retournée. Si la conversion entraîne la perte de chiffres non significatifs, SQLSTATE 01S07 (fractionnement) est retourné.  
  
## <a name="numeric-source-to-character-target"></a>Numeric Source à la cible de caractère  
 Voici les règles de conversion d’une source numérique (NS) à une cible de caractère (CT):  
  
1.  Que LT soit la longueur des caractères de CT. Pour l’affectation de récupération, LT est égal à la longueur du tampon dans les caractères moins le nombre d’octets dans le caractère de non-termination pour cet ensemble de caractère.  
  
2.  Cas:  
  
    -   Si NS est un type numérique exact, laissez YP égaler la chaîne de caractères la plus courte qui se conforme à la définition de *l’exactitude-numérique-littérale* telle que l’échelle de YP est la même que l’échelle de NS, et la valeur interprétée de YP est la valeur absolue de NS.  
  
    -   Si NS est un type numérique approximatif, laissez YP être une chaîne de caractères comme suit :  
  
         Casse :  
  
         Si NS est égal à 0, alors YP est 0.  
  
         Que YSN soit la chaîne de caractères la plus courte qui se conforme à la définition de la valeur*exacte-numérique-littérale* et dont la valeur interprétée est la valeur absolue de NS. Si la longueur de YSN est inférieure à la *(précision* 1) du type de données de NS, laissez YP égaler YSN.  
  
         Sinon, YP est la chaîne de caractères la plus courte qui se conforme à la définition *d’approximatif-numérique-littérale* dont la valeur interprétée est la valeur absolue de NS et dont *la mantissa* se compose d’un *seul chiffre* qui n’est pas «0», suivie d’une *période* et un *non signé-integer*.  
  
3.  Casse :  
  
    -   Si NS est inférieure à 0, laissez Y être le résultat de:  
  
         '- &#124;&#124; YP  
  
         où '&#124;&#124;' est l’opérateur de concatenation de chaîne.  
  
         Sinon, laissez Y égal YP.  
  
4.  Que LY soit la longueur dans les caractères de Y.  
  
5.  Casse :  
  
    -   Si LY est égal à LT, alors CT est réglé à Y.  
  
    -   Si LY est inférieur à LT, alors CT est réglé à Y étendu sur la droite par le nombre approprié d’espaces.  
  
         Sinon (LY > LT), copiez les premiers caractères LT de Y en CT.  
  
         Casse :  
  
         S’il s’agit d’une affectation de magasin, retournez l’erreur SQLSTATE 22001 (données de chaîne, à droite tronquées).  
  
         S’il s’agit d’une affectation de récupération, retournez l’avertissement SQLSTATE 01004 (données de chaîne, à droite tronquées). Lorsque la copie entraîne la perte de chiffres fractionnels (autres que les zéros de fuite), il est défini par le conducteur si l’un des éléments suivants se produit:  
  
         (1) Le conducteur tronque la chaîne en Y à une échelle appropriée (qui peut être zéro aussi) et écrit le résultat en CT.  
  
         (2) Le conducteur arrondit la chaîne en Y à une échelle appropriée (qui peut être zéro aussi) et écrit le résultat dans CT.  
  
         (3) Le conducteur ne tronque ni ne arrondit, mais il suffit d’exemplaires les premiers caractères LT de Y en CT.
