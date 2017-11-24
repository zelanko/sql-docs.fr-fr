---
title: "État de la ligne | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60931ff8464478a55828713747ad6f4bb408f10d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="row-status"></a>État de la ligne
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 La bibliothèque de curseurs crée une mémoire tampon dans le cache pour l’état de la ligne. La bibliothèque de curseurs récupère les valeurs pour le tableau d’état de ligne (spécifié avec l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR) à partir de cette mémoire tampon. Pour chaque ligne, la bibliothèque de curseurs définit cette mémoire tampon à :  
  
-   SQL_ROW_DELETED lorsqu’il exécute un positionnée delete instruction sur la ligne.  
  
-   SQL_ROW_ERROR quand il rencontre une erreur durant la récupération de la ligne à partir de la source de données avec **SQLFetch**.  
  
-   SQL_ROW_SUCCESS lorsqu’il extrait avec succès la ligne à partir de la source de données avec **SQLFetch**.  
  
-   SQL_ROW_UPDATED lorsqu’il exécute une instruction de mise à jour positionnée sur la ligne.
