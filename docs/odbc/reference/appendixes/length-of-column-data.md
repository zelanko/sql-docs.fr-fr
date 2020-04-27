---
title: Longueur des données de la colonne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column data [ODBC]
- length of column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d0b7ad515661cce4c5b1d407be768cc3da131bb4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304930"
---
# <a name="length-of-column-data"></a>Longueur des données de colonne
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 La bibliothèque de curseurs crée une mémoire tampon dans le cache pour chaque tampon longueur/indicateur lié au jeu de résultats avec **SQLBindCol**. Elle utilise les valeurs de ces mémoires tampons pour construire une clause **Where** lorsqu’elle émule des instructions Update ou DELETE positionnées. Il met à jour ces mémoires tampons à partir des tampons de l’ensemble de lignes lorsqu’il extrait des données de la source de données et lorsqu’il exécute des instructions de mise à jour positionnées.  
  
 Si le type C d’une mémoire tampon de données est SQL_C_CHAR ou SQL_C_BINARY, et si la valeur de longueur/indicateur est SQL_NTS, la longueur de chaîne des données est placée dans le tampon de longueur/d’indicateur.  
  
> [!NOTE]  
>  La bibliothèque de curseurs ne met pas à jour son cache pour une colonne si **StrLen_or_IndPtr* dans la mémoire tampon de l’ensemble de lignes correspondante est SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC.
