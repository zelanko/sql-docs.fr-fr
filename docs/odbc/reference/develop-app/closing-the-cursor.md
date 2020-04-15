---
title: Fermeture du curseur ( Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 723e40e6d83eed84ed93ee1eeab3535622ad5f04
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299139"
---
# <a name="closing-the-cursor"></a>Fermeture du curseur
Lorsqu’une application a terminé à l’aide d’un curseur, elle appelle **SQLCloseCursor** pour fermer le curseur. Par exemple :  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 Jusqu’à ce que la demande ferme le curseur, la déclaration sur laquelle le curseur est ouvert ne peut pas être utilisée pour la plupart des autres opérations, comme l’exécution d’une autre déclaration SQL. Pour une liste complète des fonctions qui peuvent être appelées pendant qu’un curseur est ouvert, voir [Annexe B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Pour fermer un curseur, une application doit appeler **SQLCloseCursor**, pas **SQLCancel**.  
  
 Les curseurs restent ouverts jusqu’à ce qu’ils soient explicitement fermés, sauf lorsqu’une transaction est engagée ou annulée, auquel cas certaines sources de données ferment le curseur. En particulier, atteindre la fin de l’ensemble de résultats, lorsque **SQLFetch** retourne SQL_NO_DATA, ne ferme pas un curseur. Même les curseurs sur les ensembles de résultats vides (ensembles de résultats créés lorsqu’une instruction exécutée avec succès mais qui n’a retourné aucune ligne) doivent être explicitement fermés.
