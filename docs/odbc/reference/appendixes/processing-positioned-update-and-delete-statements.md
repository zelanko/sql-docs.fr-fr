---
title: Traitement Des mises à jour positionnées et supprimer les déclarations ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- ODBC cursor library [ODBC], statement processing
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- SQL statements [ODBC], cursor library
- ODBC cursor library [ODBC], positioned update or delete
- cursor library [ODBC], statement processing
ms.assetid: 2975dd97-48e6-4d0a-a9c7-40759a7d94c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b3f20da018bcd4e28e8ffca097fb5a4373d7f42
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81308020"
---
# <a name="processing-positioned-update-and-delete-statements"></a>Traitement des instructions de mise à jour et de suppression positionnées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 La bibliothèque de curseurs prend en charge les mises à jour positionnées et suppriment les déclarations en remplaçant la clause **WHERE CURRENT OF** dans de telles déclarations par une clause **WHERE** qui énumère les valeurs stockées dans son cache pour chaque colonne consolidée. La bibliothèque de curseurs transmet les instructions **UPDATE** et **DELETE** nouvellement construites au conducteur pour exécution. Pour les instructions de mise à jour positionnées, la bibliothèque de curseurs met à jour son cache à partir des valeurs des tampons encastrés et définit la valeur correspondante du tableau d’état de la ligne à SQL_ROW_UPDATED. Pour les instructions de suppression positionnées, il définit la valeur correspondante dans le tableau d’état de la ligne à SQL_ROW_DELETED.  
  
> [!CAUTION]  
>  La clause **WHERE** construite par la bibliothèque du curseur pour identifier la rangée actuelle peut ne pas identifier les lignes, identifier une rangée différente ou identifier plus d’une rangée. Pour plus d’informations, voir [Construction des déclarations recherchées](../../../odbc/reference/appendixes/constructing-searched-statements.md), plus tard dans cette annexe.  
  
 Les relevés de mise à jour et de suppression positionnés sont soumis aux restrictions suivantes :  
  
-   Les instructions de mise à jour et de suppression positionnées ne peuvent être utilisées que dans les cas suivants : lorsqu’une instruction **SELECT** a généré l’ensemble de résultats ; lorsque la déclaration **SELECT** ne contenait pas de jointure, de clause **UNION** ou **d’une** clause GROUPE BY; et quand toutes les colonnes qui utilisaient un alias ou une expression dans la liste de sélection n’étaient pas liées à **SQLBindCol**.  
  
-   Si une application prépare une mise à jour ou une déclaration de suppression positionnée, elle doit le faire après avoir appelé **SQLFetch** ou **SQLFetchScroll**. Bien que la bibliothèque de curseurs soumette la déclaration au conducteur pour la préparation, elle ferme l’instruction et l’exécute directement lorsque la demande appelle **SQLExecute**.  
  
-   Si le conducteur ne prend en charge qu’une seule déclaration active, la bibliothèque de curseurs récupère le reste de l’ensemble de résultats, puis refoigne le jeu de ligne actuel de son cache avant d’exécuter une mise à jour ou une déclaration de suppression positionnée. Si l’application appelle alors une fonction qui renvoie les métadonnées dans un ensemble de résultats (par exemple, **SQLNumResultCols** ou **SQLDescribeCol),** la bibliothèque de curseurs renvoie une erreur.  
  
-   Si une mise à jour ou une déclaration de suppression positionnée est effectuée sur une colonne d’une table qui comprend une colonne timetamp qui est automatiquement mise à jour chaque fois qu’une mise à jour est effectuée, toutes les mises à jour ou supprimer les instructions ultérieures échoueront si la colonne timetamp est liée. Cela se produit parce que la mise à jour recherchée ou supprimer l’instruction que la bibliothèque de curseur crée n’identifiera pas avec précision la ligne à mettre à jour. La valeur de l’instruction recherchée pour la colonne de timestamp ne correspondra pas à la valeur automatiquement mise à jour de la colonne de timestamp.
