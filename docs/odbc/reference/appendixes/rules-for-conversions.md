---
title: Règles de conversion | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3ecee500204303dfcbcd8e179b9cb9cb0a94bae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63032920"
---
# <a name="rules-for-conversions"></a>Règles pour les conversions
Les règles dans cette section s’appliquent pour les conversions impliquant des littéraux numériques. Dans le cadre de ces règles, les termes suivants sont définis :  
  
-   *Affectation de Store :* Lors de l’envoi des données dans une colonne de table dans une base de données. Cela se produit pendant les appels aux **SQLExecute**, **SQLExecDirect**, et **SQLSetPos**. Lors de l’attribution de magasin, « target » fait référence à une colonne de base de données, et « source » fait référence à des données dans les mémoires tampons d’application.  
  
-   *Affectation de la récupération :* Lorsque vous récupérez des données à partir de la base de données dans des tampons de l’application. Cela se produit pendant les appels aux **SQLFetch**, **SQLGetData**, **SQLFetchScroll**, et **SQLSetPos**. Lors de l’attribution de la récupération, « target » fait référence aux mémoires tampons de l’application et « source » fait référence à la colonne de base de données.  
  
-   *CS :* La valeur dans la source du caractère.  
  
-   *NT :* La valeur dans la cible numérique.  
  
-   *NS :* La valeur dans la source de type numérique.  
  
-   *CT :* La valeur dans la cible de caractère.  
  
-   Précision d’un littéral numérique exact : le nombre de chiffres qu’il contient.  
  
-   La mise à l’échelle d’un littéral numérique exact : le nombre de chiffres à droite de la période expresse ou implicite.  
  
-   La précision d’un littéral numérique approximatif : la précision de la mantisse.  
  
## <a name="character-source-to-numeric-target"></a>Source du caractère à la cible numérique  
 Voici les règles de conversion à partir d’une source de caractère (CS) vers une cible numérique (NT) :  
  
1.  Remplacez CS avec la valeur obtenue en supprimant les espaces de début ou de fin dans CS. Si CS n’est pas valide *littéral numérique*, SQLSTATE 22018 (valeur de caractère non valide pour la spécification de la casse) est retournée.  
  
2.  Remplacez CS avec la valeur obtenue en supprimant les zéros non significatifs avant la virgule décimale, les zéros de fin après la virgule décimale, ou les deux.  
  
3.  Convertir CS NT. Si la conversion entraîne une perte de chiffres significatifs, SQLSTATE 22003 (valeur numérique hors limites) est retournée. Si la conversion entraîne la perte de chiffres non significatifs, SQLSTATE 01 s 07 (troncation fractionnelle) est retournée.  
  
## <a name="numeric-source-to-character-target"></a>Source de type numérique à caractère cible  
 Voici les règles de conversion à partir d’une source numérique (NS) pour une cible de caractère (CT) :  
  
1.  Soit la longueur en caractères de TR LT Pour l’attribution de la récupération, LT est égale à la longueur de la mémoire tampon en caractères moins le nombre d’octets dans le caractère de fin de la valeur null pour ce jeu de caractères.  
  
2.  Cas :  
  
    -   Si NS est un type numérique exact, puis laissez YP égale à la chaîne de caractères le plus court qui est conforme à la définition de *littéral numérique exacte* telles que la mise à l’échelle de YP est identique à l’échelle de NS, et la valeur interprétée de YP est le valeur absolue de NS.  
  
    -   Si NS est un type numérique approximatif, puis que vous laissez YP être une chaîne de caractères comme suit :  
  
         Cas :  
  
         Si NS est égal à 0, YP est 0.  
  
         Soit la chaîne de caractères le plus court qui est conforme à la définition exacte-YSN*littéral numérique* et dont la valeur interprétée est la valeur absolue de NS. Si la longueur de YSN est inférieur à (*précision* + 1) du type de données de NS, puis laissez YP égal YSN.  
  
         Sinon, YP est la chaîne de caractères le plus court qui est conforme à la définition de *littéral numérique approximatif* dont la valeur interprétée est la valeur absolue de NS et dont la propriété *mantisse* se compose d’un seul *chiffre* autrement dit pas « 0 », suivie d’un *période* et un *entier non signé*.  
  
3.  Cas :  
  
    -   Si NS est inférieur à 0, puis que vous laissez Y être le résultat de :  
  
         '-' &#124;&#124; YP  
  
         où «&#124;&#124;» est l’opérateur de concaténation de chaîne.  
  
         Sinon, permettent d’Y égal YP.  
  
4.  Soit la longueur en caractères de Y EP.  
  
5.  Cas :  
  
    -   Si EP est égale à LT, CT est défini à Y.  
  
    -   Si EP est inférieure à LT, CT est défini à Y étendu sur la droite par un nombre approprié d’espaces.  
  
         Sinon (EP > LT), copiez les premiers caractères LT de Y dans TR  
  
         Cas :  
  
         S’il s’agit d’une attribution de magasin, retournent l’erreur SQLSTATE 22001 (chaîne de données tronquée à droite).  
  
         S’il s’agit d’affectation de la récupération, retourner l’avertissement SQLSTATE 01004 (chaîne de données tronquée à droite). Lors de la copie entraîne la perte de chiffres fractionnaires (autres que des zéros à droite), elle est définie par le pilote si une des actions suivantes se produit :  
  
         (1) le pilote tronque la chaîne de Y pour une mise à l’échelle appropriée (qui peut être pas également de zéro) et écrit le résultat en tr  
  
         (2) le pilote arrondit la chaîne de Y pour une mise à l’échelle appropriée (qui peut être pas également de zéro) et écrit le résultat en tr  
  
         (3) le pilote ni tronque ni arrondit, mais copie simplement les premiers caractères LT de Y dans TR
