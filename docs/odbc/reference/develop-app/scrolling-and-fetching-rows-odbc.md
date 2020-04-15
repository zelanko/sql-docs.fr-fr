---
title: Rouleaux et aller chercher des rangées (ODBC) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 72d262bf73e69388f65ff281e62235d2d831669e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304200"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>Défilement et extraction de lignes (ODBC)
Lors de l’utilisation d’un curseur défilant, les applications appellent **SQLFetchScroll** pour positionner le curseur et aller chercher des rangées. **SQLFetchScroll** prend en charge le défilement relatif (suivant, préalable et relatif *n* lignes), le défilement absolu (premier, dernier et rangée *n*), et le positionnement par signet. Les arguments *de FetchOrientation* et *FetchOffset* dans **SQLFetchScroll** précisent quel ensemble à atteindre, comme le montrent les diagrammes suivants.  
  
 ![Extraction des ensembles de lignes suivante, précédente, première et dernière](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Extraction des ensembles de lignes suivante, précédente, première et dernière**  
  
 ![Extraction de l'ensemble de lignes absolu, relatif ou avec signet](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Aller chercher des rames absolues, relatives et signets**  
  
 **SQLFetchScroll** positionne le curseur à la rangée spécifiée et renvoie les rangées dans le rangée en commençant par cette rangée. Si le jeu de ligne spécifié chevauche la fin de l’ensemble de résultat, un jeu de ligne partiel est retourné. Si le jeu de ligne spécifié chevauche le début de l’ensemble de résultat, le premier jeu de ligne dans l’ensemble de résultat est habituellement retourné ; pour plus de détails, consultez la description de la fonction [SQLFetchScroll.](../../../odbc/reference/syntax/sqlfetchscroll-function.md)  
  
 Dans certains cas, l’application peut vouloir positionner le curseur sans récupérer de données. Par exemple, il pourrait vouloir tester si une ligne existe ou tout simplement obtenir le signet de la ligne sans apporter d’autres données à travers le réseau. Pour ce faire, il définit l’attribut SQL_ATTR_RETRIEVE_DATA déclaration à SQL_RD_OFF. La variable liée à la colonne de signets (le cas échéant) est toujours mise à jour, quel que soit le paramètre de cet attribut d’instruction.  
  
 Une fois le ramset récupéré, l’application peut appeler **SQLSetPos** pour se positionner sur une rangée particulière dans le rame ou rafraîchir les rangées dans le rame. Pour plus d’informations sur l’utilisation **de SQLSetPos**, voir [Mise à jour des données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Le défilement est pris en charge dans ODBC 2. *x* drivers par **SQLExtendedFetch**. Pour plus d’informations, voir [Block Cursors, Scrollable Cursors et Compatibility backward](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)in Appendix G: Driver Guidelines for Backward Compatibility.
