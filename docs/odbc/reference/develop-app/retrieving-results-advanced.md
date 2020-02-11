---
title: Récupération des résultats (avancé) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22a88a96b856ba0976dcb8600d26f78b772654bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020506"
---
# <a name="retrieving-results-advanced"></a>Récupération des résultats (avancée)
Une application peut spécifier qu’un décalage est ajouté aux adresses de tampons de données liées et les adresses de tampon de longueur/indicateur correspondantes lors de l’appel de **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**ou **SQLSetPos** . Les résultats de ces ajouts déterminent les adresses utilisées dans ces opérations.  
  
 Les décalages de liaison permettent à une application de modifier des liaisons sans appeler **SQLBindCol** pour les colonnes précédemment liées. Un appel à **SQLBindCol** pour relier les données modifie l’adresse de la mémoire tampon et le pointeur de longueur/indicateur. La reliaison avec un décalage, en revanche, ajoute simplement un décalage à l’adresse de tampon de données liée existante et à l’adresse tampon de longueur/d’indicateur. Lorsque des décalages sont utilisés, les liaisons sont un « modèle » de la façon dont les mémoires tampons d’application sont présentées et l’application peut déplacer ce « modèle » dans différentes zones de mémoire en modifiant le décalage. Un nouveau décalage peut être spécifié à tout moment et est toujours ajouté aux valeurs liées à l’origine.  
  
 Pour spécifier un décalage de liaison, l’application définit l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR sur l’adresse d’une mémoire tampon SQLINTEGER destinée. Avant que l’application appelle une fonction qui utilise les liaisons, telles que **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**ou **SQLSetPos**, elle place un décalage en octets dans cette mémoire tampon, tant que l’adresse de tampon de données, ni l’adresse de tampon de longueur/d’indicateur ne sont 0, et tant que la colonne liée est dans le jeu de résultats. La somme de l’adresse et du décalage doit être une adresse valide. (Cela signifie que l’offset et l’adresse à laquelle le décalage est ajouté peuvent être non valides, à condition que leur somme soit une adresse valide.) L’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR est un pointeur afin que la valeur de décalage puisse être appliquée à plusieurs jeux de données de liaison, qui peuvent tous être modifiés en modifiant une valeur de décalage. Une application doit s’assurer que le pointeur reste valide jusqu’à la fermeture du curseur.  
  
> [!NOTE]  
>  ODBC 2 ne prend pas en charge les décalages de liaison. *x* pilotes.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Curseurs de bloc](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [Curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [Bibliothèque de curseurs ODBC](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [Résultats multiples](../../../odbc/reference/develop-app/multiple-results.md)
