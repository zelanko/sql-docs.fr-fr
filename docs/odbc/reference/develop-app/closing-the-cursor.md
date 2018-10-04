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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792957"
---
# <a name="closing-the-cursor"></a>Fermeture du curseur
Lorsqu’une application a terminé d’utiliser un curseur, il appelle **SQLCloseCursor** pour fermer le curseur. Exemple :  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 Jusqu'à ce que l’application ferme le curseur, l’instruction sur laquelle l’ouverture du curseur ne peut pas être utilisée pour la plupart des autres opérations, telles que l’exécution d’une autre instruction SQL. Pour obtenir une liste complète des fonctions qui peuvent être appelées lorsqu’un curseur est ouvert, consultez [tableaux des transitions d’état ODBC annexe b :](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Pour fermer un curseur, une application doit appeler **SQLCloseCursor**, et non **SQLCancel**.  
  
 Les curseurs restent ouverts jusqu'à ce qu’ils sont explicitement fermés, sauf lorsqu’une transaction est validée ou restaurée, auquel cas certaines sources de données fermer le curseur. En particulier, atteint la fin du résultat défini, lorsque **SQLFetch** retourne SQL_NO_DATA, ne fermez pas un curseur. Même les curseurs de jeux de résultats vides (jeux de résultats créé lors d’une instruction exécutée avec succès, mais qui a retourné aucune ligne) doivent être fermés explicitement.
