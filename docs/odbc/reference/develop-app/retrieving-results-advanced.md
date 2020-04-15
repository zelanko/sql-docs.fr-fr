---
title: Résultats de récupération (Avancé) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- offsets [ODBC]
- result sets [ODBC], about result sets
- bind offsets [ODBC]
ms.assetid: bc00c379-71a7-407a-975c-898243f39bb6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca02b4ff911c8edff06b38d5341eeaa288cc194c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294639"
---
# <a name="retrieving-results-advanced"></a>Récupération des résultats (avancée)
Une application peut spécifier qu’un décalage est ajouté aux adresses tampons de données consolidées et aux adresses tampons de longueur/indicateur correspondantes lorsque **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos** est appelé. Les résultats de ces ajouts déterminent les adresses utilisées dans ces opérations.  
  
 Les compensations de liaison permettent à une application de modifier les fixations sans appeler **SQLBindCol** pour les colonnes précédemment liées. Un appel à **SQLBindCol** pour reliser les données modifie l’adresse tampon et le pointeur longueur/indicateur. Le rebinding avec un décalage, d’autre part, ajoute simplement une compensation à l’adresse tampon de données consolidées existantes et l’adresse tampon de longueur/indicateur. Lorsque des compensations sont utilisées, les fixations sont un « modèle » de la façon dont les tampons d’application sont disposés et l’application peut déplacer ce « modèle » vers différents domaines de mémoire en changeant la compensation. Un nouveau décalage peut être spécifié à tout moment et est toujours ajouté aux valeurs initialement liées.  
  
 Pour spécifier un décalage de liaison, la demande définit l’attribut SQL_ATTR_ROW_BIND_OFFSET_PTR énoncé à l’adresse d’un tampon SQLINTEGER. Avant que l’application appelle une fonction qui utilise les liaisons, telles que **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**, il place un décalage dans les octets dans ce tampon, tant que ni l’adresse tampon de données ni la longueur / indicateur adresse tampon est 0, et aussi longtemps que la colonne de limite est dans l’ensemble de résultats. La somme de l’adresse et la compensation doivent être une adresse valide. (Cela signifie que l’un ou l’autre ou à la fois le décalage et l’adresse à laquelle le décalage est ajouté peuvent être invalides, tant que leur somme est une adresse valide.) L’attribut de l’SQL_ATTR_ROW_BIND_OFFSET_PTR déclaration est un pointeur de sorte que la valeur offset peut être appliquée à plus d’un ensemble de données contraignantes, qui peuvent toutes être modifiées en changeant une valeur offset. Une application doit s’assurer que le pointeur reste valide jusqu’à ce que le curseur soit fermé.  
  
> [!NOTE]  
>  Les compensations contraignantes ne sont pas prises en charge par ODBC 2. *x* conducteurs.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Curseurs de bloc](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [Curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [Bibliothèque de curseurs ODBC](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [Résultats multiples](../../../odbc/reference/develop-app/multiple-results.md)
