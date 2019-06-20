---
title: L’exécution positionné instructions Update et Delete | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2391c01d93c876562ab9d870ab0dba22bf74cea5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63189019"
---
# <a name="executing-positioned-update-and-delete-statements"></a>Exécution d’instructions de mise à jour et de suppression positionnées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Une fois une application a extrait un bloc de données avec **SQLFetchScroll**, il peut mettre à jour ou supprimer les données dans le bloc. Pour exécuter une mise à jour positionnée ou delete, l’application :  
  
1.  Appels **SQLSetPos** pour positionner le curseur sur la ligne d’être mis à jour ou supprimées.  
  
2.  Construit une mise à jour positionnée ou une instruction delete avec la syntaxe suivante :  
  
     **Mise à jour** *nom de la table*  
  
     **SET** *column-identifier* **=** {*expression* &#124; **NULL**}  
  
     [ **,** *column-identifier* **=** {*expression* &#124; **NULL**}]  
  
     **WHERE CURRENT OF** *nom de curseur*  
  
     **DELETE FROM** *nom de la table* **WHERE CURRENT OF** *nom de curseur*  
  
     Le moyen le plus simple pour construire le **définir** clause dans une instruction de mise à jour positionnée consiste à utiliser des marqueurs de paramètres pour chaque colonne pour être mis à jour et utiliser **SQLBindParameter** pour lier ces aux mémoires tampons de l’ensemble de lignes pour le ligne à mettre à jour. Dans ce cas, le type de données C du paramètre doit être le même que le type de données C de la mémoire tampon d’ensemble de lignes.  
  
3.  Met à jour les mémoires tampons d’ensemble de lignes de la ligne actuelle si elle doit être exécutée une instruction de mise à jour positionnée. Après avoir exécuté une instruction de mise à jour positionnée, la bibliothèque de curseurs copie les valeurs de chaque colonne dans la ligne actuelle à son cache.  
  
    > [!CAUTION]  
    >  Si l’application ne met pas à jour les mémoires tampons d’ensemble de lignes avant d’exécuter une instruction de mise à jour positionnée correctement, les données dans le cache seront incorrectes après que l’instruction est exécutée.  
  
4.  Exécute la mise à jour positionnée ou une instruction delete à l’aide d’une instruction autre que l’instruction associée le curseur.  
  
    > [!CAUTION]  
    >  Le **où** clause construit par la bibliothèque de curseurs pour identifier la ligne actuelle peut échouer pour identifier toutes les lignes, identifier une ligne différente ou identifier plusieurs lignes. Pour plus d’informations, consultez [construisant des instructions recherché](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Tous les positionné mise à jour et des instructions de suppression nécessitent un nom de curseur. Pour spécifier le nom du curseur, une application appelle **SQLSetCursorName** avant l’ouverture du curseur. Pour utiliser le nom de curseur généré par le pilote, une application appelle **SQLGetCursorName** après l’ouverture du curseur.  
  
 Après le curseur bibliothèque exécute une mise à jour positionnée ou instruction delete, le tableau d’état, mémoires tampons d’ensemble de lignes et cache maintenu par la bibliothèque de curseurs contiennent les valeurs indiquées dans le tableau suivant.  
  
|Instruction utilisée|Valeur dans le tableau d’état de ligne|Valeurs dans<br /><br /> mémoires tampons d’ensemble de lignes|Valeurs dans<br /><br /> mémoires tampons de cache|  
|--------------------|-------------------------------|----------------------------------|---------------------------------|  
|Mise à jour positionnée|SQL_ROW_UPDATED|Nouvelles valeurs [1]|Nouvelles valeurs [1]|  
|Suppression positionnée|SQL_ROW_DELETED|Anciennes valeurs|Anciennes valeurs|  
  
 [1] l’application doit mettre à jour les valeurs dans les mémoires tampons d’ensemble de lignes avant d’exécuter l’instruction de mise à jour positionnée ; après l’exécution de l’instruction de mise à jour positionnée, la bibliothèque de curseurs copie les valeurs dans les mémoires tampons d’ensemble de lignes à son cache.
