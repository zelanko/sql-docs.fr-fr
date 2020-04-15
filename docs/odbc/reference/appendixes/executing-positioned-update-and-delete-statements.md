---
title: Exécution des mises à jour positionnées et suppression des déclarations (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- ODBC cursor library [ODBC], positioned update or delete
ms.assetid: 1d64f309-2a6e-4ad1-a6b5-e81145549c56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96a1aa891ef8ba26c6c239cf35e62a8f36018e65
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307000"
---
# <a name="executing-positioned-update-and-delete-statements"></a>Exécution d’instructions de mise à jour et de suppression positionnées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Après qu’une application a récupéré un bloc de données avec **SQLFetchScroll**, il peut mettre à jour ou supprimer les données dans le bloc. Pour exécuter une mise à jour ou une suppression positionnée, l’application :  
  
1.  Appelle **SQLSetPos** pour positionner le curseur sur la ligne à mettre à jour ou à supprimer.  
  
2.  Construit une mise à jour ou supprimer l’instruction positionnée avec la syntaxe suivante :  
  
     **NOM** *de table* UPDATE  
  
     **SET** *colonne-identificateur* **=** -*expression* &#124; **NULL**'  
  
     [**,** *colonne-identifiant* **=** '*expression* &#124; **NULL**']  
  
     **Où CURRENT OF** *cursor-name*  
  
     **DELETE FROM** *table-name* **WHERE CURRENT OF** *cursor-name*  
  
     La façon la plus simple de construire la clause **SET** dans une instruction de mise à jour positionnée est d’utiliser des marqueurs de paramètres pour chaque colonne à mettre à jour et d’utiliser **SQLBindParameter** pour les lier aux tampons encastrés pour que la ligne soit mise à jour. Dans ce cas, le type de données C du paramètre sera le même que le type de données C du tampon rowset.  
  
3.  Mise à jour des tampons encastrés pour la ligne actuelle s’il exécute une instruction de mise à jour positionnée. Après avoir exécuté avec succès une instruction de mise à jour positionnée, la bibliothèque de curseur copie les valeurs de chaque colonne de la rangée actuelle à son cache.  
  
    > [!CAUTION]  
    >  Si l’application ne met pas à jour correctement les tampons rowset avant d’exécuter une mise à jour positionnée, les données du cache seront incorrectes après l’exécution de la déclaration.  
  
4.  Exécute la mise à jour ou supprimer l’instruction positionnée à l’aide d’une instruction différente de celle associée au curseur.  
  
    > [!CAUTION]  
    >  La clause **WHERE** construite par la bibliothèque du curseur pour identifier la rangée actuelle peut ne pas identifier les lignes, identifier une rangée différente ou identifier plus d’une rangée. Pour plus d’informations, voir [Construction des déclarations recherchées](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Toutes les mises à jour et suppressions de relevés positionnées nécessitent un nom de curseur. Pour spécifier le nom du curseur, une application appelle **SQLSetCursorName** avant l’ouverture du curseur. Pour utiliser le nom du curseur généré par le conducteur, une application appelle **SQLGetCursorName** après l’ouverture du curseur.  
  
 Une fois que la bibliothèque de curseurs exécute une mise à jour ou une déclaration de suppression positionnée, le tableau d’état, les tampons encastrés et le cache conservés par la bibliothèque du curseur contiennent les valeurs indiquées dans le tableau suivant.  
  
|Déclaration utilisée|Valeur dans le tableau d’état de ligne|Valeurs en<br /><br /> tampons en rangée|Valeurs en<br /><br /> tampons cache|  
|--------------------|-------------------------------|----------------------------------|---------------------------------|  
|Mise à jour positionnée|SQL_ROW_UPDATED|Nouvelles valeurs[1]|Nouvelles valeurs[1]|  
|Suppression positionnée|SQL_ROW_DELETED|Anciennes valeurs|Anciennes valeurs|  
  
 [1] L’application doit mettre à jour les valeurs dans les tampons rowset avant d’exécuter l’énoncé de mise à jour positionné; après l’exécution de l’énoncé de mise à jour positionné, la bibliothèque de curseur copie les valeurs des tampons encastrés à son cache.
