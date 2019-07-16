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
ms.openlocfilehash: de22797bdcf4ff526a8c17aee313567da3114b60
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036543"
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
