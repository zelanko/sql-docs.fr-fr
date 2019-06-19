---
title: SQLGetData (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e3009b4e3bed6fc871ecfd1aab4e2af2f1f1c86
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188771"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLGetData** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLGetData**, consultez [fonction SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 La bibliothèque de curseurs implémente **SQLGetData** en commençant par construire un **sélectionnez** instruction avec un **où** clause qui énumère les valeurs stockées dans son cache pour chaque limite colonne dans la ligne actuelle. Ensuite, il exécute la **sélectionnez** instruction sélectionner à nouveau la ligne et les appels **SQLGetData** dans le pilote pour récupérer les données à partir de la source de données (par opposition au cache).  
  
> [!CAUTION]  
>  Le **où** clause construit par la bibliothèque de curseurs pour identifier la ligne actuelle peut échouer pour identifier toutes les lignes, identifier une ligne différente ou identifier plusieurs lignes. Pour plus d’informations, consultez [construisant des instructions recherché](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Si l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS a SQL_UB_VARIABLE, **SQLGetData** peut être appelée sur la colonne 0 pour retourner des données de signet.  
  
 Les appels à **SQLGetData** sont soumis aux restrictions suivantes :  
  
-   **SQLGetData** ne peut pas être appelée pour les curseurs avant uniquement.  
  
-   **SQLGetData** peut être appelée uniquement lorsque les conditions suivantes sont remplies : un **sélectionnez** l’instruction produit le jeu de résultats ; les **sélectionnez** instruction ne contenait pas d’une jointure, une  **UNION** clause, ou un **GROUP BY** clause ; et toutes les colonnes qui a utilisé un alias ou une expression dans la liste de sélection n’ont pas été liés avec **SQLBindCol**.  
  
-   Si le pilote prend en charge qu’une seule instruction active, la bibliothèque de curseurs extrait le reste du résultat de la définir avant d’exécuter le **sélectionnez** instruction et en appelant **SQLGetData**.
