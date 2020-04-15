---
title: Utilisation de cursors de bloc Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f5c487bd8b60a83c709399cb9673dc0b015bd79d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306790"
---
# <a name="using-block-cursors"></a>Utilisation de curseurs de bloc
Le support pour les curseurs de bloc est intégré dans ODBC 3. *x*. **SQLFetch** ne peut être utilisé que pour les lots multirow lorsqu’il est appelé dans ODBC 3. *x*; si un ODBC 2. *x* application appelle **SQLFetch**, il n’ouvrira qu’un seul-ligne, à l’avant seulement curseur. Quand un ODBC 3. *x* application appelle **SQLFetch** dans un ODBC 2. *x* conducteur, il retourne une seule ligne à moins que le conducteur ne supporte **SQLExtendedFetch**. Pour plus d’informations, voir [Block Cursors, Scrollable Cursors et Compatibility backward](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) in Appendix G: Driver Guidelines for Backward Compatibility.  
  
 Pour utiliser des curseurs de blocs, l’application définit la taille de l’aquage, lie les tampons encastrés (comme décrit dans la section précédente), définit en option les attributs SQL_ATTR_ROWS_FETCHED_PTR et SQL_ATTR_ROW_STATUS_PTR déclaration, et appelle **SQLFetch** ou **SQLFetchScroll** pour aller chercher un bloc de lignes. L’application peut modifier la taille de l’aviron et lier de nouveaux tampons encastrés (en appelant **SQLBindCol** ou en spécifiant un décalage de liaison) même après que des rangées ont été récupérées.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Taille des ensembles de lignes](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Nombre de lignes extraites et état](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData et Block Cursors; bloc curso](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)
