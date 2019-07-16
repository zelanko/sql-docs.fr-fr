---
title: État de ligne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- row status [ODBC]
- cache [ODBC]
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a62bad0e69a8bf8b5365575f97e4791cbbf270d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057113"
---
# <a name="row-status"></a>État des lignes
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 La bibliothèque de curseurs crée une mémoire tampon dans le cache pour l’état de la ligne. La bibliothèque de curseurs récupère les valeurs pour le tableau d’état de ligne (spécifié avec l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR) à partir de cette mémoire tampon. Pour chaque ligne, la bibliothèque de curseurs définit cette mémoire tampon à :  
  
-   SQL_ROW_DELETED lorsqu’il exécute un positionnée delete, instruction sur la ligne.  
  
-   SQL_ROW_ERROR quand il rencontre une erreur de récupération de la ligne à partir de la source de données avec **SQLFetch**.  
  
-   SQL_ROW_SUCCESS lorsqu’il extrait avec succès la ligne à partir de la source de données avec **SQLFetch**.  
  
-   SQL_ROW_UPDATED lorsqu’il exécute une instruction de mise à jour positionnée sur la ligne.
