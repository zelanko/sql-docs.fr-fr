---
title: Longueur des données de colonne | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d2998eace4772624a1e6590ab2541577147f5c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041607"
---
# <a name="length-of-column-data"></a>Longueur des données de colonne
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 La bibliothèque de curseurs crée une mémoire tampon dans le cache pour chaque mémoire tampon de longueur / d’indicateur lié à un jeu de résultats avec **SQLBindCol**. Il utilise les valeurs de ces mémoires tampons pour construire un **où** clause lorsqu’il émule mise à jour positionnée ou supprimer des instructions. Il met à jour ces mémoires tampons à partir de mémoires tampons de l’ensemble de lignes lorsqu’il extrait des données à partir de la source de données et lorsqu’il s’exécute les instructions de mise à jour positionnée.  
  
 Si le type C d’une mémoire tampon de données est SQL_C_CHAR ou SQL_C_BINARY, et la valeur de longueur / d’indicateur est SQL_NTS, la longueur de chaîne des données est placée dans la mémoire tampon de longueur / d’indicateur.  
  
> [!NOTE]  
>  La bibliothèque de curseurs ne met pas à jour son cache pour une colonne si **StrLen_or_IndPtr* dans l’ensemble de lignes correspondante mémoire tampon est SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC.
