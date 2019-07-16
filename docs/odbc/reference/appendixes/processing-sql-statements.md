---
title: Traitement des instructions SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9452ade90f6967dff6d72d5692efcf91b93154d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057246"
---
# <a name="processing-sql-statements"></a>Traitement des instructions SQL
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 La bibliothèque de curseurs ODBC transmet toutes les instructions SQL directement dans le pilote à l’exception de ce qui suit :  
  
-   Positionné de mise à jour et supprimer des instructions  
  
-   **SELECT FOR UPDATE** instructions  
  
-   Instructions SQL par lots  
  
 Pour exécuter la mise à jour positionnée et supprimer des instructions et pour positionner le curseur sur une ligne pour appeler **SQLGetData** pour cette ligne, la bibliothèque de curseurs construit une instruction de recherche qui identifie la ligne.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Traitement des instructions de mise à jour et de suppression positionnées](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [Traitement des instructions SELECT FOR UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Traitement des lots d’instructions SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Construction d’instructions de recherche](../../../odbc/reference/appendixes/constructing-searched-statements.md)
