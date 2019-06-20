---
title: Fermeture du curseur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 632a922abb544a379892dfa168f55efd605304c8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63125435"
---
# <a name="closing-the-cursor"></a>Fermeture du curseur
Lorsqu’une application a terminé d’utiliser un curseur, il appelle **SQLCloseCursor** pour fermer le curseur. Exemple :  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 Jusqu'à ce que l’application ferme le curseur, l’instruction sur laquelle l’ouverture du curseur ne peut pas être utilisée pour la plupart des autres opérations, telles que l’exécution d’une autre instruction SQL. Pour obtenir une liste complète des fonctions qui peuvent être appelées lorsqu’un curseur est ouvert, consultez [annexe b : Tableaux des transitions d’état ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Pour fermer un curseur, une application doit appeler **SQLCloseCursor**, et non **SQLCancel**.  
  
 Les curseurs restent ouverts jusqu'à ce qu’ils sont explicitement fermés, sauf lorsqu’une transaction est validée ou restaurée, auquel cas certaines sources de données fermer le curseur. En particulier, atteint la fin du résultat défini, lorsque **SQLFetch** retourne SQL_NO_DATA, ne fermez pas un curseur. Même les curseurs de jeux de résultats vides (jeux de résultats créé lors d’une instruction exécutée avec succès, mais qui a retourné aucune ligne) doivent être fermés explicitement.
