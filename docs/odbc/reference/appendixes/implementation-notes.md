---
title: Notes de mise en œuvre (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7ec14b9c-69b8-4c6e-838a-88d1ebdc8725
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 970188a2fca45706405e398cece0f04d38dfdc68
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284310"
---
# <a name="implementation-notes"></a>Remarques relatives à l’implémentation
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Cette section décrit comment la bibliothèque de curseurs de l’ODBC est mise en œuvre. Il décrit comment la bibliothèque de curseurs maintient son cache, exécute les relevés SQL et implémente les fonctions oDBC.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Cache de la bibliothèque de curseurs](../../../odbc/reference/appendixes/cursor-library-cache.md)  
  
-   [Traitement des instructions SQL](../../../odbc/reference/appendixes/processing-sql-statements.md)  
  
-   [Fonctions ODBC et la bibliothèque de curseurs](../../../odbc/reference/appendixes/odbc-functions-and-the-cursor-library.md)
