---
title: Longueur des données de colonnes (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304930"
---
# <a name="length-of-column-data"></a>Longueur des données de colonne
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 La bibliothèque de curseurs crée un tampon dans le cache pour chaque tampon longueur/indicateur lié au résultat défini avec **SQLBindCol**. Il utilise les valeurs de ces tampons pour construire une clause **WHERE** lorsqu’il imite les mises à jour positionnées ou les relevés de suppression. Il met à jour ces tampons à partir des tampons rowset lorsqu’il récupère les données de la source de données et lorsqu’il exécute des instructions de mise à jour positionnées.  
  
 Si le type C d’un tampon de données est SQL_C_CHAR ou SQL_C_BINARY, et que la durée/la valeur de l’indicateur est SQL_NTS, la longueur des chaînes des données est mise dans le tampon longueur/indicateur.  
  
> [!NOTE]  
>  La bibliothèque de curseurs ne met pas à jour son cache pour une colonne si*StrLen_or_IndPtr* dans le tampon de rowset correspondant est SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC.
