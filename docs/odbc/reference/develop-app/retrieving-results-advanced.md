---
title: Récupération des résultats (avancés) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 5199fb82cbc6b2a9da644554db12dc525cc0be40
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47693521"
---
# <a name="retrieving-results-advanced"></a>Récupération des résultats (avancée)
Une application peut spécifier qu’un décalage est ajouté à adresses de tampons de données et l’indicateur de longueur/correspondante liées aux adresses de mémoire tampon quand **SQLBulkOperations**, **SQLFetch**,  **SQLFetchScroll**, ou **SQLSetPos** est appelée. Les résultats de ces ajouts déterminent les adresses utilisées dans ces opérations.  
  
 Les décalages de liaison permettent à une application modifier les liaisons sans appeler **SQLBindCol** pour les colonnes liées précédemment. Un appel à **SQLBindCol** pour relier des données change l’adresse de la mémoire tampon et le pointeur de longueur / d’indicateur. Rétablissement de la liaison avec un décalage, en revanche, ajoute simplement la valeur un décalage à l’adresse de mémoire tampon de données liées existante et l’adresse de mémoire tampon de longueur / d’indicateur. Lorsque les décalages sont utilisés, les liaisons sont un « modèle » de la disposition des mémoires tampons de l’application et l’application peut passer cet « modèle » vers différentes zones de mémoire en modifiant le décalage. Un nouveau décalage peut être spécifié à tout moment et est toujours ajouté aux valeurs liées à l’origine.  
  
 Pour spécifier un décalage de la liaison, l’application définit l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR à l’adresse d’une mémoire tampon SQLINTEGER. Avant que l’application appelle une fonction qui utilise les liaisons, tel que **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, ou **SQLSetPos**, elle place un décalage en octets dans cette mémoire tampon, tant que l’adresse de mémoire tampon de données, ni l’adresse de mémoire tampon de longueur / d’indicateur a la valeur 0, et que la colonne liée est dans le jeu de résultats. La somme de l’adresse et le décalage doit être une adresse valide. (Cela signifie qu’un ou les deux le décalage et l’adresse à laquelle le décalage est ajouté peuvent être non valides, tant que leur somme est une adresse valide.) L’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR est un pointeur afin que la valeur de décalage peut être appliquée à plusieurs jeux de liaison de données, qui peut être modifiée en modifiant une valeur de décalage. Une application doit s’assurer que le pointeur reste valide jusqu'à ce que le curseur est fermé.  
  
> [!NOTE]  
>  Décalages des liaisons ne sont pas pris en charge par ODBC 2. *x* pilotes.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Curseurs de bloc](../../../odbc/reference/develop-app/block-cursors.md)  
  
-   [Curseurs avec défilement](../../../odbc/reference/develop-app/scrollable-cursors.md)  
  
-   [Bibliothèque de curseurs ODBC](../../../odbc/reference/develop-app/the-odbc-cursor-library.md)  
  
-   [Résultats multiples](../../../odbc/reference/develop-app/multiple-results.md)
