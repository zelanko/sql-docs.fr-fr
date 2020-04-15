---
title: Statut de la rangée (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4ae4169dc3f2a491663f4a86c564cfee5c2f4d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305098"
---
# <a name="row-status"></a>État des lignes
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 La bibliothèque de curseurs crée un tampon dans le cache pour l’état de la ligne. La bibliothèque de curseurs récupère les valeurs du tableau d’état de la ligne (spécifié avec l’attribut SQL_ATTR_ROW_STATUS_PTR) de ce tampon. Pour chaque rangée, la bibliothèque de curseurs définit ce tampon pour :  
  
-   SQL_ROW_DELETED lorsqu’il exécute une déclaration de suppression positionnée sur la ligne.  
  
-   SQL_ROW_ERROR lorsqu’il rencontre une erreur récupérant la ligne à partir de la source de données avec **SQLFetch**.  
  
-   SQL_ROW_SUCCESS lorsqu’il réussit à aller chercher la ligne à partir de la source de données avec **SQLFetch**.  
  
-   SQL_ROW_UPDATED lorsqu’il exécute une mise à jour positionnée sur la ligne.
