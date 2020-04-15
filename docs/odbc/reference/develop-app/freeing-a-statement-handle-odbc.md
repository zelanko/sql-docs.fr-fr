---
title: Libérer une déclaration Poignée ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01e4cb46edf1b1a0f1c6dfaa0273c1dd5b392686
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305614"
---
# <a name="freeing-a-statement-handle-odbc"></a>Libération d’un handle d’instruction dans ODBC
Comme nous l’avons mentionné précédemment, il est plus efficace de réutiliser les déclarations que de les laisser tomber et d’en allouer de nouvelles. Avant d’exécuter une nouvelle déclaration SQL sur une déclaration, les applications doivent être sûres que les paramètres d’instruction actuels sont appropriés. Cela inclut les attributs d'instruction, les liaisons de paramètres et les liaisons de jeux de résultats. En général, les paramètres et les ensembles de résultats pour l’ancienne déclaration SQL doivent être non liés (en appelant **SQLFreeStmt** avec les options SQL_RESET_PARAMS et SQL_UNBIND) et rebondir pour la nouvelle déclaration SQL.  
  
 Lorsque l’application a terminé l’utilisation de la déclaration, il appelle **SQLFreeHandle** pour libérer la déclaration. Après avoir libéré l’énoncé, il s’agit d’une erreur de programmation d’applications pour utiliser la poignée de l’instruction dans un appel à une fonction ODBC; conséquences indéfinises mais probablement fatales.  
  
 Lorsque **SQLFreeHandle** est appelé, le conducteur libère la structure utilisée pour stocker des informations sur la déclaration.  
  
 **SQLDisconnect** libère automatiquement toutes les instructions sur une connexion.
