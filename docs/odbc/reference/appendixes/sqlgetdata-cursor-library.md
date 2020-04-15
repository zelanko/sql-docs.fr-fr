---
title: SQLGetData (Cursor Library) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307840"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLGetData** dans la bibliothèque de curseurs. Pour plus d’informations sur **SQLGetData**, voir [SQLGetData Fonction](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 La bibliothèque de curseurs met en œuvre **SQLGetData** en construisant d’abord une déclaration **SELECT** avec une clause **WHERE** qui énumère les valeurs stockées dans son cache pour chaque colonne liée dans la rangée actuelle. Il exécute ensuite la déclaration **SELECT** pour réélire la ligne et appelle **SQLGetData** dans le conducteur pour récupérer les données de la source de données (par opposition au cache).  
  
> [!CAUTION]  
>  La clause **WHERE** construite par la bibliothèque du curseur pour identifier la rangée actuelle peut ne pas identifier les lignes, identifier une rangée différente ou identifier plus d’une rangée. Pour plus d’informations, voir [Construction des déclarations recherchées](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Si l’attribut de l’SQL_ATTR_USE_BOOKMARKS déclaration est configuré pour SQL_UB_VARIABLE, **SQLGetData** peut être appelé sur la colonne 0 pour retourner les données de signets.  
  
 Les appels à **SQLGetData** sont soumis aux restrictions suivantes :  
  
-   **SQLGetData** ne peut pas être appelé pour les curseurs avant-seulement.  
  
-   **SQLGetData** ne peut être appelé que lorsque les conditions suivantes sont remplies : une déclaration **SELECT** a généré l’ensemble de résultats; la déclaration **SELECT** ne contenait pas de jointure, de clause **UNION** ou **d’une** clause GROUPE BY; et toutes les colonnes qui utilisaient un pseudonyme ou une expression dans la liste de sélection n’étaient pas liées à **SQLBindCol**.  
  
-   Si le conducteur ne prend en charge qu’une seule déclaration active, la bibliothèque de curseurs récupère le reste du résultat fixé avant d’exécuter la déclaration **SELECT** et d’appeler **SQLGetData**.
