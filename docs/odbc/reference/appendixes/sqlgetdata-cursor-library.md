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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07200d48f439c97003da7062fc218cd2f3081d1b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307840"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLGetData** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLGetData**, consultez [fonction SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 La bibliothèque de curseurs implémente **SQLGetData** en créant d’abord une instruction **Select** avec une clause **Where** qui énumère les valeurs stockées dans son cache pour chaque colonne liée dans la ligne actuelle. Il exécute ensuite l’instruction **Select** pour resélectionner la ligne et appelle **SQLGetData** dans le pilote pour récupérer les données de la source de données (par opposition au cache).  
  
> [!CAUTION]  
>  La clause **Where** construite par la bibliothèque de curseurs pour identifier la ligne actuelle peut ne pas pouvoir identifier de lignes, identifier une autre ligne ou identifier plusieurs lignes. Pour plus d’informations, consultez [construction d’instructions recherchées](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Si l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS est défini sur SQL_UB_VARIABLE, **SQLGetData** peut être appelé sur la colonne 0 pour retourner les données de signet.  
  
 Les appels à **SQLGetData** sont soumis aux restrictions suivantes :  
  
-   **SQLGetData** ne peut pas être appelé pour les curseurs avant uniquement.  
  
-   **SQLGetData** peut être appelé uniquement lorsque les conditions suivantes sont remplies : une instruction **Select** a généré le jeu de résultats ; l’instruction **Select** ne contenait pas de clause Join, **Union** ou **Group by** . et les colonnes qui utilisaient un alias ou une expression dans la liste de sélection n’étaient pas liées à **SQLBindCol**.  
  
-   Si le pilote ne prend en charge qu’une seule instruction active, la bibliothèque de curseurs extrait le reste du jeu de résultats avant d’exécuter l’instruction **Select** et d’appeler **SQLGetData**.
