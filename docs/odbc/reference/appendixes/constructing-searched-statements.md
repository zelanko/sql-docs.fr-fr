---
title: Construire des déclarations recherchées (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- searched statements [ODBC]
- ODBC cursor library [ODBC], statement processing
- ODBC cursor library [ODBC], searched statements
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
- cursor library [ODBC], searched statements
- SQL statements [ODBC], searched statements
ms.assetid: e429254c-c43f-4fbf-98b2-5f1ed53501ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8b9a27aa9fc84aadc6659993de3e12e269631d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284739"
---
# <a name="constructing-searched-statements"></a>Construction d’instructions de recherche
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Pour prendre en charge les instructions de mise à jour et de suppression positionnées, la bibliothèque de curseurs construit une mise **à JOUR** recherchée ou une instruction **DELETE** à partir de l’instruction positionnée. Pour prendre en charge les appels à **SQLGetData** dans un bloc de données, la bibliothèque de curseurs construit une déclaration **SELECT** recherchée pour créer un ensemble de résultats contenant la ligne actuelle de données. Dans chacune de ces déclarations, la clause **WHERE** énumère les valeurs stockées dans le cache pour chaque colonne liée qui renvoie SQL_PRED_SEARCHABLE ou SQL_PRED_BASIC pour l’identificateur de champ SQL_DESC_SEARCHABLE dans **SQLColAttribute**.  
  
> [!CAUTION]  
>  La clause **WHERE** construite par la bibliothèque du curseur pour identifier la rangée actuelle peut ne pas identifier les lignes, identifier une rangée différente ou identifier plus d’une rangée.  
  
 Si une mise à jour ou une déclaration de suppression positionnée affecte plus d’une rangée, la bibliothèque de curseur met à jour le tableau d’état de la ligne uniquement pour la rangée sur laquelle le curseur est positionné et retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01001 (conflit d’opération cursor). Si l’énoncé n’identifie aucune ligne, la bibliothèque de curseur ne met pas à jour le tableau d’état de la rangée et renvoie SQL_SUCCESS_WITH_INFO et SQLSTATE 01001 (conflit d’opération Cursor). Une application peut appeler **SQLRowCount** pour déterminer le nombre de lignes qui ont été mises à jour ou supprimées.  
  
 Si la clause **SELECT** utilisée pour positionner le curseur pour un appel à **SQLGetData** identifie plus d’une rangée, **SQLGetData** n’est pas garanti de retourner les données correctes. S’il n’identifie aucune ligne, **SQLGetData** retourne SQL_NO_DATA.  
  
 Si une application est conforme aux lignes directrices suivantes, la clause **WHERE** construite par la bibliothèque de curseurs devrait identifier de façon unique la ligne actuelle, sauf lorsque cela est impossible, par exemple lorsque la source de données contient des lignes en double.  
  
-   **Lier les colonnes qui identifient uniquement la ligne.** Si les colonnes liées n’identifient pas uniquement la ligne, la clause **WHERE** construite par la bibliothèque de curseurs peut identifier plus d’une rangée. Dans une mise à jour ou une déclaration de suppression positionnée, une telle clause peut entraîner la mise à jour ou la suppression de plus d’une rangée. Dans un appel à **SQLGetData**, une telle clause pourrait amener le conducteur à retourner les données pour la mauvaise rangée. Lier toutes les colonnes dans une clé unique garantit que chaque ligne est identifiée de manière unique.  
  
-   **Allouer des tampons de données assez grands pour qu’aucune troncation ne se produise.** Le cache de la bibliothèque de curseurs est une copie des valeurs dans les tampons en rangée liés au résultat défini avec **SQLBindCol**. Si les données sont tronquées lorsqu’elles sont placées dans ces tampons, elles seront également tronquées dans le cache. Une clause **WHERE** construite à partir de valeurs tronquées pourrait ne pas identifier correctement la ligne sous-jacente dans la source de données.  
  
-   **Spécifier des tampons de longueur non nulle pour les données C binaires.** La bibliothèque de curseurs n’alloue des tampons de longueur dans son cache que si *l’argument StrLen_or_IndPtr* dans **SQLBindCol** n’est pas nul. Lorsque l’argument *de TargetType* est SQL_C_BINARY, la bibliothèque de curseur nécessite la longueur des données binaires pour construire une clause **WHERE** à partir des données. S’il n’y a pas de tampon de longueur pour une colonne SQL_C_BINARY et que l’application appelle **SQLGetData** ou tente d’exécuter une mise à jour ou une déclaration de suppression positionnée, la bibliothèque de curseurs renvoie SQL_ERROR et SQLSTATE SL014 (Une demande positionnée n’a pas été émise et tous les champs de comptage de colonnes n’ont pas été tamponnés).  
  
-   **Spécifier des tampons de longueur non nulle pour les colonnes nulles.** La bibliothèque de curseurs n’alloue des tampons de longueur dans son cache que si *l’argument StrLen_or_IndPtr* dans **SQLBindCol** n’est pas nul. Étant donné que SQL_NULL_DATA est stockée dans le tampon de longueur, la bibliothèque de curseur suppose que toute colonne pour laquelle aucun tampon de longueur n’est spécifiée n’est pas annulable. Si aucune colonne de longueur n’est spécifiée pour une colonne in nullable, la bibliothèque de curseur construit une clause **WHERE** qui utilise la valeur de données pour la colonne. Cette clause n’identifiera pas correctement la ligne.
